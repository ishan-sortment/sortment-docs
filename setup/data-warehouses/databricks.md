# Databricks

## Overview

Sortment lets you pull data stored in your Databricks warehouse and use it to create schema.

## Configuring Databricks in Sortment

The credentials needed to connect to your cluster can be found in the ODBC options in your databricks account. Enter the following required fields into Sortment:

1. **Server hostname**: To find your server hostname, visit the Databricks web console and locate your cluster. Then, click to reveal Advanced options and navigate to the JDBC/ ODBC tab.
2. **HTTP path**: To find your HTTP path, visit the Databricks web console and locate your cluster. Then, click to reveal Advanced options and navigate to the JDBC/ ODBC tab.
3. **Personal Access Token:** To get your personal access token from user settings in Databricks, open **Settings** by clicking the cog ⚙️ in the sidebar and select **User settings.** Click **Generate token**. You'll be asked to enter a name and expiry. Copy the token and put it in Sortment.
4. **Catalog name**: Catalog shared here will be used by Sortment to publish audiences and campaigns data back into your Databricks account.
5. **Database:** The tables shared in the database will be available to be used in Sortment.

## Test your connection <a href="#test-your-connection" id="test-your-connection"></a>

When setting up a source for the first time, Sortment validates the following:

* Network connectivity
* Databricks credentials
* Permission to list schemas and tables
* Permission to write to the catalog

Some sources may initially fail connection tests due to timeouts. Once a connection is established, subsequent API requests should happen more quickly, so it's best to retry tests if they first fail. You can do this by clicking **Test again**.

## Blob setup for Databricks

Once you've saved these Databricks credentials, you're ready to set up the blob credentials in Sortment. Blob storage helps to move data out from your warehouse to messaging provider. This is also used to batch events coming from campaigns before they are sent back into your warehouse for analytics.

In case your Databricks account is hosted in AWS, use [Amazon S3 setup](../cloud-bucket-storage/amazon-s3-for-snowflake.md) to set up the blob storage.
