# Amazon S3 for Databricks



## Prerequisite

Create an S3 bucket you want Sortment to give access to. This bucket URI will be required when creating policy and role for bucket access.

To give Sortment access to S3 bucket on your AWS account, follow these steps to create an account:

#### Configuring Access Key

The **Access Key** access type allows you to configure Sortment to use an IAM user by providing the user's **Access Key ID** and **Secret Access Key**.

If you need help generating these keys, consult the [IAM article](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) on this topic.

Once you have an Access Key ID and Secret Access Key, paste those values into the form and click **Create**.

## Setting up the credentials

Following details are required to setup S3 blob storage in Sortment. Some fields are duplicate from Databricks account setup, and you may or may not use the same credentials.

* **AWS Region:** Select the region your account is setup in from the given list.
* **AWS S3 Bucket Name:** This is the bucket you may have setup for Sortment.
* **Access Key:** With **Access Key ID** and **Secret Access Key,** Sortment will be able to generate an access key to establish connection with S3 bucket and read/write data.
* **Server hostname**: To find your server hostname, visit the Databricks web console and locate your cluster. Then, click to reveal Advanced options and navigate to the JDBC/ ODBC tab.
* **HTTP path**: To find your HTTP path, visit the Databricks web console and locate your cluster. Then, click to reveal Advanced options and navigate to the JDBC/ ODBC tab.
* **Personal Access Token:** To get your personal access token from user settings in Databricks, open **Settings** by clicking the cog ⚙️ in the sidebar and select **User settings.** Click **Generate token**. You'll be asked to enter a name and expiry. Copy the token and put it in Sortment.

Use the credentials generated above to connect Sortment to your S3 bucket and proceed.<br>





