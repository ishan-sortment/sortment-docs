# Athena

### Overview

Sortment lets you access data stored in your Athena "warehouse" and use it to create audiences and run campaigns.

> Connecting Sortment to Athena requires some setup in both platforms. It is recommended to set up a dedicated IAM user or role with the correct permissions before configuring the connection in Sortment.

Athena uses a regular query editor with S3 as the backing storage where query results and materialized tables are written. All actual data lives in S3; Athena itself does not store data server-side.

Sortment supports two Athena table types:

* Iceberg‑managed tables (typically for Parquet datasets).
* Hive tables (typically for CSV datasets from application flows or exports).

The Athena catalog functions as the logical schema/database, similar to databases or schemas in other warehouses.

***

### Connection configuration

#### Connection type

Right now, **Sortment supports only direct connection over public internet** for Athena. Since data is encrypted in transit via TLS, a direct connection is suitable for most use cases.

#### Athena credential and configuration setup

When configuring Athena as a data warehouse in Sortment, the following details are required:

* **AWS Region**\
  The region where your Athena workgroup and S3 buckets are deployed (for example, `us-east-1` or `ap-south-1`). In your AWS Console → top‑right profile menu, you can see the selected region.
* **Catalog**\
  The Athena catalog name that acts as the logical database layer (similar to a database/schema in other data warehouses). Sortment will query this catalog to discover and run queries on your tables.
* **Database (Schema)**\
  The database inside the catalog where your business data lives. This is where Sortment will read your source tables.
* **S3 Data Directory (optional)**\
  The S3 location for storing table data when materializing models. This is optional and only needed if you're using dbt to create tables.
* **S3 Staging Directory**\
  The S3 location where Athena stores query results. This is required for all Athena queries. e.g. `s3://your-bucket/athena-results/`
* **AWS Access Key ID & Secret Access Key**\
  Programmatic credentials for an IAM user or role. You can generate these via AWS Console → IAM → Users → Security Credentials → Access Keys.

***

#### Recommended architecture

#### Table types and engine

* Use **Iceberg tables** for Parquet‑based datasets that are managed by Athena.
* Use **Hive tables** for CSV datasets coming from your application flows or from exports out of existing warehouses (for example, BigQuery → CSV → S3 → Hive table).
* For unmanaged Iceberg tables (data already present in S3 and registered in Glue/Athena), use Athena **engine version 3** as the standard setup.

**Rule of thumb:**

* Parquet → Iceberg.
* CSV → Hive.

#### S3 bucket and folder layout

* You can leverage an existing S3 bucket and give Sortment/Athena credentials access to specific folders within that bucket.
* Read and write operations can use **different buckets** if your infra requires it, as long as the credentials you provide to Sortment have access to both.
* All data is stored in S3; Athena only reads from and writes to S3 and does not store data itself.

A common layout is:

* `s3://your-bucket/master/` – master or core tables.
* `s3://your-bucket/data/` – campaign/event data and other onboarded tables.
* `s3://your-bucket/query-results/` – Athena query results and Sortment materializations.

Any materialized tables or CTAS outputs used by Sortment should be configured to write into a dedicated "query results schema" folder under your S3 bucket.

#### Permission model

Access key credentials provided to Sortment must have read/write access to the S3 bucket or prefixes used for query results. Folder‑level permission segregation is possible via custom IAM policies that restrict the allowed S3 paths.

> ⚠️ **Important:** Athena workgroups and data catalogs are **independent resources** in AWS. Permissions granted on a workgroup do not apply to the data catalog, and vice versa. Both must be explicitly granted in separate policy statements.

**Policy 1 — Athena (query execution + metadata)**

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "athena:StartQueryExecution",
                "athena:GetQueryExecution",
                "athena:GetQueryResults",
                "athena:GetWorkGroup"
            ],
            "Resource": [
                "arn:aws:athena:<region>:<account-id>:workgroup/<your-workgroup-name>"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "athena:GetTableMetadata",
                "athena:ListTableMetadata"
            ],
            "Resource": [
                "arn:aws:athena:<region>:<account-id>:datacatalog/AwsDataCatalog"
            ]
        }
    ]
}
```

> ⚠️ `GetTableMetadata` and `ListTableMetadata` must be granted at the **data catalog level** (`datacatalog/AwsDataCatalog`), not the workgroup level. These are independent resources in AWS and permissions do not carry over between them.

**Policy 2 — AWS Glue (schema/metadata catalog)**

```json
{
    "Version": "2012-10-17",
    "Statement": [
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
                "arn:aws:glue:<region>:<account-id>:database/<your-database-name>",
                "arn:aws:glue:<region>:<account-id>:table/<your-database-name>/*"
            ]
        }
    ]
}
```

**Policy 3 — S3 (query results storage)**

```json
{
    "Version": "2012-10-17",
    "Statement": [
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
    ]
}
```

***

#### Data onboarding and testing

To validate Athena with Sortment end‑to‑end, we recommend the following steps:

1. **Prepare test data**
   * Download a few representative result sets from your existing warehouse (for example, BigQuery) as CSV files.
   * Upload these CSVs into S3 under your chosen folder structure (for example, `master/` and `data/`).
2. **Create Athena tables**
   * In Athena, create at least two test tables: one under your "Master" folder and one under your "Data" folder.
   * Use Hive table definitions pointing to the CSV paths you uploaded.
   * Preview the tables in Athena to confirm that the schema and sample data look correct.
3. **Connect to Sortment and test**
   * Configure the Athena connection in Sortment using the details described above (region, catalog, database, S3 results location, access keys).
   * Validate that Sortment can list these tables and run basic queries.
   * Run a sample campaign cloning flow locally (as done in the demo) to ensure files and uploads work with two or more variables.

***

#### Known limitations and considerations

* Athena is typically **slower than Redshift** in terms of speed, latency, and concurrency. Plan for higher query times and fewer concurrent heavy workloads compared to a dedicated MPP warehouse.
* The current implementation uses some workarounds to handle **memory and CPU constraints** in Athena while still supporting existing Sortment functionality.
* The **dbt–Athena adapter/library is less mature**, so dbt workloads may be slower or encounter more issues than with mainstream warehouses.
* When exporting data from your warehouse to S3, **column headers are often not preserved by default**, so you may need a small preprocessing step or script to ensure the CSVs have the correct headers for Hive table creation.

***

### Tips and troubleshooting

If you encounter an error or question not listed below and need assistance, [reach out to support](mailto:support@sortment.com). We're here to help.

#### Connection timeout

When initially testing your connection, you may receive a connection timeout error. Once a connection is established, subsequent API requests should happen more quickly, so it's best to retry the tests if they first fail. You can do this by clicking Continue again.
