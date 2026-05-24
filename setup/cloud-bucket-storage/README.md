# Cloud Bucket Storage

Sortment uses cloud bucket storage to store campaign related data to route to the marketing platform and manage campaign events. Your team has control over this bucket data management and policies to manage and purge the data. There are four types of data interactions happening via the bucket storage in Sortment:

1. Send campaigns data from warehouse to cloud bucket to send campaign to respective communications app.
2. Save events data as received on Sortment callback URL from event sources defined by the user or communication channel integrations to prevent real-time write on the warehouse.
3. Load data stored in the cloud bucket into warehouse at regular intervals.
4. Access data stored in the bucket storage for campaigns and journeys.

The setup depends on which data warehouse is connected to Sortment. Refer to the docs below to create relevant user account and setup on Sortment.

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>Amazon S3 for Snowflake</td><td></td><td></td><td><a href="amazon-s3-for-snowflake.md">amazon-s3-for-snowflake.md</a></td></tr><tr><td>Google Cloud Storage for BigQuery</td><td></td><td></td><td><a href="google-cloud-storage-for-bigquery.md">google-cloud-storage-for-bigquery.md</a></td></tr><tr><td>Amazon S3 for Redshift</td><td></td><td></td><td><a href="amazon-s3-for-redshift.md">amazon-s3-for-redshift.md</a></td></tr></tbody></table>
