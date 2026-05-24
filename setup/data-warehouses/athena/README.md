# Athena

## Overview

Sortment connects to your Athena warehouse to read data for building audiences and running campaigns. All data lives in S3; Athena is just the query engine on top of it.

Three AWS services are involved:

```
Sortment -> Athena -> Glue -> S3
```

* **Athena** is the query engine that runs SQL
* **Glue** is the metadata catalog that tells Athena where your tables are and what columns they have
* **S3** is where your actual data and query results live

Glue is used on every read and write. You cannot use Athena without it.



### Step 1: Set Up Your S3 Bucket

Use an existing bucket or create a new one. Create these folders inside it:

| Folder           | Purpose                               | Referenced in Sortment?    |
| ---------------- | ------------------------------------- | -------------------------- |
| `master/`        | Core / reference data tables          | No                         |
| `data/`          | Campaign, event, transactional tables | No                         |
| `query-results/` | Athena query output                   | Yes (S3 Staging Directory) |

Folder names can be anything. The only one you enter into Sortment is the query results folder. Every time Athena runs a query, it saves the output as a CSV file there, so keeping it separate makes things easier to manage.

### Step 2: Create an IAM User

Go to **AWS Console > IAM > Users** and create a new user (for example, `sortment-athena-user`). Attach the following as a custom inline policy:

#### Athena Permissions

```json
{
  "Effect": "Allow",
  "Action": [
    "athena:StartQueryExecution",
    "athena:GetQueryExecution",
    "athena:GetQueryResults",
    "athena:GetTableMetadata",
    "athena:ListTableMetadata",
    "athena:GetWorkGroup"
  ],
  "Resource": "arn:aws:athena:<region>:<account-id>:workgroup/<workgroup-name>"
}
```

#### Glue Permissions

Glue is Athena's metadata store. These permissions are required for all table operations.

```json
{
  "Effect": "Allow",
  "Action": [
    "glue:GetDatabase",
    "glue:GetDatabases",
    "glue:CreateDatabase",
    "glue:GetTable",
    "glue:GetTables",
    "glue:CreateTable",
    "glue:UpdateTable",
    "glue:DeleteTable",
    "glue:BatchCreatePartition",
    "glue:GetPartitions",
    "glue:BatchDeletePartition"
  ],
  "Resource": [
    "arn:aws:glue:<region>:<account-id>:catalog",
    "arn:aws:glue:<region>:<account-id>:database/<your-database>",
    "arn:aws:glue:<region>:<account-id>:table/<your-database>/*"
  ]
}
```

#### S3 Permissions

```json
{
  "Effect": "Allow",
  "Action": [
    "s3:PutObject",
    "s3:GetObject",
    "s3:GetBucketLocation",
    "s3:ListBucket",
    "s3:DeleteObject",
    "s3:AbortMultipartUpload",
    "s3:ListMultipartUploadParts"
  ],
  "Resource": [
    "arn:aws:s3:::<your-bucket-name>",
    "arn:aws:s3:::<your-bucket-name>/*"
  ]
}
```

{% hint style="warning" %}
Replace all `<placeholders>` with your actual AWS account ID, region, bucket name, and database name.
{% endhint %}

### Step 3: Generate Access Keys

Go to **IAM > Users > your user > Security Credentials tab > Access Keys > Create Access Key**.

1. Select **"Application running outside AWS"** as the use case
2. Finish the creation flow
3. Copy and save both keys immediately. The Secret Access Key is only shown once.

You will need these in the next step.

### Step 4: Configure Athena in Sortment

Go to **Sortment > Settings > Data Warehouse > Add Warehouse > Athena** and fill in:

| Field                | Value                                                    |
| -------------------- | -------------------------------------------------------- |
| AWS Region           | e.g. `us-east-1`                                         |
| Catalog              | `AwsDataCatalog` (default for most setups)               |
| Database             | Your Athena database name                                |
| S3 Staging Directory | `s3://your-bucket/query-results/`                        |
| S3 Data Directory    | `s3://your-bucket/data/` (optional, only needed for dbt) |
| Access Key ID        | From Step 3                                              |
| Secret Access Key    | From Step 3                                              |

Click **Test Connection** or **Save**.

### Troubleshooting Connection Failures

| Error                                     | Likely cause                     | Fix                                                                             |
| ----------------------------------------- | -------------------------------- | ------------------------------------------------------------------------------- |
| `Access Denied / Not Authorized`          | Missing IAM permissions          | Re-check all 3 policy blocks are attached                                       |
| `Bucket does not exist / Invalid S3 path` | Wrong staging directory path     | Copy the exact path from S3 console                                             |
| `Region not found / Endpoint error`       | Region mismatch                  | Make sure bucket, Athena workgroup, and Sortment config all use the same region |
| `Invalid security token / Auth failed`    | Wrong access keys                | Regenerate keys in IAM and re-enter                                             |
| `Database not found / Catalog not found`  | Typo in database or catalog name | Check the exact names in Athena console                                         |

### Step 5: Validate Your Tables

Once connected, Sortment will immediately show any existing Athena tables in your database. Check that your tables are listed inside Sortment.

#### Creating a new table (if needed)

If you have data sitting in S3 but no Athena table pointing to it, you need to register it first. Open **AWS Console > Athena > Query Editor** and run the right query for your file type:

**CSV files (Hive table):**

```sql
CREATE EXTERNAL TABLE your_database.your_table (
  id BIGINT,
  name STRING,
  created_at STRING
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE
LOCATION 's3://your-bucket/your-folder/'
TBLPROPERTIES ('skip.header.line.count' = '1');
```

**Parquet files (Iceberg table):**

```sql
CREATE TABLE your_database.your_table (
  id BIGINT,
  name STRING,
  created_at TIMESTAMP
)
LOCATION 's3://your-bucket/your-folder/'
TBLPROPERTIES ('table_type' = 'ICEBERG');
```

Then verify with:

```sql
SELECT * FROM your_database.your_table LIMIT 10;
```

Note: When exporting CSVs from other warehouses, column headers are often stripped by default. Make sure your CSV files have the correct headers before creating a Hive table.

