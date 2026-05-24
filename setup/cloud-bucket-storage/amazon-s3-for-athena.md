# Amazon S3 for Athena

## Overview

When Sortment needs to move data into or out of your Athena warehouse, it uses S3 as an intermediate storage layer. This is separate from your query results bucket and your data tables bucket.

Two operations use this bucket:

* **syncBlobToWarehouse**: Sortment uploads a file to this S3 location, Athena reads it and loads it into a table
* **syncWarehouseToBlob**: Athena exports data to this S3 location, Sortment reads it from there

This setup is only needed if you are using Sortment's data import or export features. It is not required for the initial Athena connection.

### Connection Configuration

The following details are required in Sortment for S3 blob storage configuration:

| Field                         | Description                                                                                                                         |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| AWS Region                    | The region where your S3 bucket is deployed. Should match your Athena region to avoid data egress costs.                            |
| AWS S3 Bucket Name            | The name of the S3 bucket used for import/export operations. Can be the same bucket as your Athena setup, under a different prefix. |
| Query Results Folder (Prefix) | The folder inside the bucket that Sortment will use for import/export. For example, `blob/` or `sortment-sync/`.                    |
| Access Key ID                 | Access Key ID for the IAM user that has permissions on this bucket.                                                                 |
| Secret Access Key             | Secret Access Key paired with the above. Only shown once at creation time.                                                          |

### Bucket Setup

You can use your existing Athena S3 bucket and add a dedicated prefix for blob operations, or create a separate bucket entirely. Either works as long as the IAM user has the right permissions.

If you need to create a new bucket:

1. Go to **AWS Console > S3 > Create bucket**
2. Enter a unique bucket name (for example, `my-company-sortment-blob`)
3. Select the same region as your Athena workgroup
4. Leave other settings as default and create the bucket
5. Inside the bucket, create a folder for blob operations (for example, `sortment-sync/`)

### IAM Permissions

Create or update the IAM policy for the user that Sortment uses, and add the following statement for the blob bucket:

```json
{
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

Replace `<blob-bucket>` and `<blob-prefix>` with your actual bucket name and folder prefix.

`AbortMultipartUpload` and `ListMultipartUploadParts` are required because Sortment uses multipart uploads when writing large files to S3 during export operations.

### Attaching the Policy to Your IAM User

1. Go to **AWS Console > IAM > Users**
2. Select the user you created for Sortment (for example, `sortment-athena-user`)
3. Under **Permissions**, attach or update the policy with the statement above
4. If you have not already generated access keys for this user, go to **Security Credentials > Access Keys > Create Access Key** and save both keys
