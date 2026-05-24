---
hidden: true
---

# Athena IAM permissions

Sortment needs access to Athena, Glue, and S3 to run queries, manage tables, and move data. This section assumes three logical S3 locations:

### Buckets and resources <a href="#buckets-and-resources" id="buckets-and-resources"></a>

| Variable       | Purpose                              | Used by                                                                    |
| -------------- | ------------------------------------ | -------------------------------------------------------------------------- |
| `s3StagingDir` | Athena query results                 | All queries (`OutputLocation`)                                             |
| `s3DataDir`    | Iceberg table data                   | `createTable`, other DDL operations. Falls back to `s3StagingDir` if empty |
| Blob bucket    | Import/export data (blobs/CSV files) | `syncBlobToWarehouse` (read), `syncWarehouseToBlob` (write)                |

***

### 1. Athena service permissions <a href="#id-1-athena-service-permissions" id="id-1-athena-service-permissions"></a>

Grant these permissions on the workgroup used by Sortment:

```
json{
  "Effect": "Allow",
  "Action": [
    "athena:StartQueryExecution",
    "athena:GetQueryExecution",
    "athena:GetQueryResults",
    "athena:GetTableMetadata",
    "athena:ListTableMetadata",
    "athena:GetWorkGroup"
  ],
  "Resource": "arn:aws:athena:<region>:<account>:workgroup/<workGroupName>"
}
```

* `GetTableMetadata` and `ListTableMetadata` are used to fetch catalog information (for example, `getFullCatalog()`).
* `GetWorkGroup` validates that the configured workgroup exists before running queries.

***

### 2. Glue catalog permissions <a href="#id-2-glue-catalog-permissions" id="id-2-glue-catalog-permissions"></a>

Glue is Athena’s metadata store. For **writeable schemas** (Sortment can create/alter/drop tables):

```
json{
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
    "arn:aws:glue:<region>:<account>:catalog",
    "arn:aws:glue:<region>:<account>:database/<schema>",
    "arn:aws:glue:<region>:<account>:table/<schema>/*"
  ]
}
```

* `CreateDatabase` → `CREATE DATABASE IF NOT EXISTS <schema>` before `createTable()`.
* `UpdateTable` → `ALTER TABLE ADD/DROP COLUMN`, table renames.
* `DeleteTable` → `DROP TABLE` plus cleanup when S3 metadata is missing.
* `BatchCreatePartition`, `GetPartitions`, `BatchDeletePartition` → required by Iceberg for partition management.

For **read‑only schemas** (query‑only data):

```
json{
  "Effect": "Allow",
  "Action": [
    "glue:GetDatabase",
    "glue:GetDatabases",
    "glue:GetTable",
    "glue:GetTables",
    "glue:GetPartitions"
  ],
  "Resource": [
    "arn:aws:glue:<region>:<account>:catalog",
    "arn:aws:glue:<region>:<account>:database/<read-only-schema>",
    "arn:aws:glue:<region>:<account>:table/<read-only-schema>/*"
  ]
}
```

***

### 3. S3 permissions <a href="#id-3-s3-permissions" id="id-3-s3-permissions"></a>

### Query results bucket (`s3StagingDir`) <a href="#query-results-bucket-s3stagingdir" id="query-results-bucket-s3stagingdir"></a>

Every query writes results here. Required by Athena:

```
json{
  "Effect": "Allow",
  "Action": [
    "s3:PutObject",
    "s3:GetObject",
    "s3:GetBucketLocation",
    "s3:ListBucket",
    "s3:DeleteObject"
  ],
  "Resource": [
    "arn:aws:s3:::<staging-bucket>",
    "arn:aws:s3:::<staging-bucket>/<staging-prefix>/*"
  ]
}
```

### Table data bucket (`s3DataDir`) <a href="#table-data-bucket-s3datadir" id="table-data-bucket-s3datadir"></a>

Iceberg table data is stored here. If `s3DataDir` is empty, this is the same as `s3StagingDir`, and permissions must be merged.

```
json{
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
    "arn:aws:s3:::<data-bucket>",
    "arn:aws:s3:::<data-bucket>/<data-prefix>/*"
  ]
}
```

* `DeleteObject` → required by Iceberg for `DROP TABLE` and compaction.
* `AbortMultipartUpload` and `ListMultipartUploadParts` → required for large Iceberg writes.

### Blob bucket (import/export) <a href="#blob-bucket-importexport" id="blob-bucket-importexport"></a>

Used by blob‑level sync operations:

```
json{
  "Effect": "Allow",
  "Action": [
    "s3:PutObject",
    "s3:GetObject",
    "s3:GetBucketLocation",
    "s3:ListBucket",
    "s3:AbortMultipartUpload",
    "s3:ListMultipartUploadParts"
  ],
  "Resource": [
    "arn:aws:s3:::<blob-bucket>",
    "arn:aws:s3:::<blob-bucket>/<blob-prefix>/*"
  ]
}
```

* `syncBlobToWarehouse` → reads from the blob bucket and loads into warehouse tables.
* `syncWarehouseToBlob` → writes to the blob bucket using multipart uploads (`@aws-sdk/lib-storage` `Upload`), hence multipart permissions.

***

### 4. Scenario summary <a href="#id-4-scenario-summary" id="id-4-scenario-summary"></a>

Use this matrix to verify access for each flow:

| Scenario                       | Athena    | Glue                          | `s3StagingDir`            | `s3DataDir`                                | Blob bucket                            |
| ------------------------------ | --------- | ----------------------------- | ------------------------- | ------------------------------------------ | -------------------------------------- |
| Read queries (`SELECT`)        | All above | `GetTable` / `GetDatabase`    | `PutObject` / `GetObject` | `GetObject`                                | —                                      |
| Create / alter tables          | All above | All writeable actions         | `PutObject` / `GetObject` | `PutObject` / `GetObject` / `DeleteObject` | —                                      |
| Drop tables                    | All above | `DeleteTable`                 | `PutObject` / `GetObject` | `DeleteObject`                             | —                                      |
| `syncBlobToWarehouse`          | All above | `CreateTable` / `DeleteTable` | `PutObject` / `GetObject` | `PutObject`                                | `GetObject`                            |
| `syncWarehouseToBlob`          | All above | `GetTable`                    | `PutObject` / `GetObject` | `GetObject`                                | `PutObject` + multipart upload actions |
| `loadCSVIntoWarehouseFromBlob` | All above | `CreateTable` / `DeleteTable` | `PutObject` / `GetObject` | `PutObject`                                | `GetObject`                            |

***

### 5. Notes <a href="#id-5-notes" id="id-5-notes"></a>

1. **If `s3DataDir` is empty**\
   The data and staging directories share the same bucket; add data permissions to the staging bucket/prefix.
2. **IAM roles vs access keys**\
   If using IAM roles (for example, EC2/ECS task roles), attach these policies to the role and you do not need to configure `accessKeyId` / `secretAccessKey` in Sortment.
3. **Glue resource scope**\
   `glue:CreateDatabase` requires both the `catalog` ARN and the specific `database` ARN to be present in `Resource`.
4. **`s3:ListBucket` scope**\
   `s3:ListBucket` must be granted on `arn:aws:s3:::<bucket>`, not only on `bucket/*`, which is why each S3 block includes both the bucket and prefix ARNs.
