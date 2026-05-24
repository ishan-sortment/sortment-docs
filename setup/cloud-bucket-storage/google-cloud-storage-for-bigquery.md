# Google Cloud Storage for BigQuery

## Overview

This bucket storage is needed to process user data from Bigquery to send to communication app as csv files. To give Sortment access to GCS bucket on your GCP account, follow these steps to create an account:

## Connection configuration

To setup Bucket for Sortment, follow these steps:

1. Click **Cloud Storage** on left panel and select Buckets in the dropdown.
2. On Buckets page, click Create to create a new bucket for Sortment.
3. Setup a name for your bucket and click **Continue**.\
   ![](<../../.gitbook/assets/image (101).png>)
4. Setup region in next step based on your organisation policies for data storage. This region should match the region for your datasets in BigQuery. Click Next.
5. For rest of the steps, you can keep default settings and click Create at the end of the form.
6. Once created, go to Permissions tab and click Grant Access.
7. Add email for the service account created for Sortment earlier and grant **Storage Object Admin** role. Click **Save**<br>

## Credential Setup

<figure><img src="../../.gitbook/assets/image (151).png" alt=""><figcaption></figcaption></figure>

To connect to a GCS bucket, navigate to your **Sortment workspace settings -> Blob Storage** and enter the following details:

* **GCS Bucket Name:** The bucket that Sortment has read and write access for creating campaign data tables.
* **Key File:** This will be used to access the bucket storage created above. This key file can be same as you had created earlier for Google BigQuery setup. Storage Object Admin access should be added to this service account.

