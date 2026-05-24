# Amazon S3 for Snowflake

As discussed in [cloud bucket storage setup](./), Amazon S3 is required for several data-related use cases in Sortment.

## Connection configuration

Following details are requied on Sortment for S3 connection for Snowflake:

* **AWS Region:** The geographical region where your AWS services, including S3 and Snowflake, are deployed. Examples include us-east-1 (N. Virginia) or ap-south-1 (Mumbai). In your [AWS Console](https://console.aws.amazon.com/console/home) → Click on your profile (top-right) → See the selected region.



* **AWS S3 Bucket Name:** A globally unique name assigned to an S3 bucket where you store and retrieve data. On [AWS Console](https://console.aws.amazon.com/console/home) → Go to S3 → Locate your bucket under “Buckets” list.



* **Access Key ID:** A unique identifier for an AWS IAM user or service that allows programmatic access to AWS services. On [AWS Console](https://console.aws.amazon.com/console/home) → IAM → Users → Select your user → Security Credentials tab → Generate Access Key.



* **Secret Access Key:** A secret key paired with the Access Key ID, used for signing API requests securely. Generated alongside the Access Key ID in IAM (only shown once). If lost, you must generate a new pair.



* **Snowflake Stage Name:** This stage will be used to read and write data between your Snowflake and Amazon S3 bucket. You have to create a new stage for Sortment, and use the resepctive name here. Follow the [steps below](amazon-s3-for-snowflake.md#creating-stage-in-snowflake) to create the stage.

## AWS credentials setup

Follow these steps to setup an S3 bucket for Sortment:

#### Creating a bucket

1. Sign in to the AWS Management Console and [navigate to the S3 service](https://console.aws.amazon.com/s3/home).
2. Click on "Create bucket."
3. Enter a unique bucket name (globally unique across AWS).
4. Select an AWS region for the bucket. This should be same as your Snowflake cluster region.
5. Create the bucket.

#### Creating a user

Follow the user creation flow to create a new user for Sortment. If you need help, consult the [IAM article](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html) on this topic.

#### Create inline policy to the user

1. From your AWS console navigate to **Identity and Access Management (IAM)** **> Users > Select the user > Add permission > Create inline policy**
2. In the JSON policy editor, use the following policy. Update `{$bucket-name}` to the bucket created above. Give your policy a name and create the policy.

```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": "s3:*",
			"Resource": [
					"arn:aws:s3:::{$bucket-name}",
					"arn:aws:s3:::{$bucket-name}/*"
				]
		}
	]
}
```

#### Configuring Access Key

The **Access Key** access type allows you to configure Sortment to use an IAM user by providing the user's **Access Key ID** and **Secret Access Key**.

If you need help generating these keys, consult the [IAM article](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) on this topic.

Once you have an Access Key ID and Secret Access Key, paste those values into the form and click **Create**.

### Creating Stage in Snowflake

Once the credentials are created, you need to create a stage in Snowflake to complete the S3 connection.

{% hint style="warning" %}
Ensure that the stage name is set as `sortment`.
{% endhint %}

```sql
-- Set variables
set bucket_url='s3://sortment';
set aws_key_id='REPLACE_WITH_YOUR_AWS_KEY';
set aws_secret_key='REPLACE_WITH_YOUR_AWS_SECRET_KEY';
set smt_default_role='SORTMENT_ROLE';

-- Set role for grants
USE ROLE identifier($smt_default_role);

-- Create stage for Sortment
CREATE OR REPLACE STAGE sortment
  URL=$bucket_url
  CREDENTIALS=(AWS_KEY_ID=$aws_key_id AWS_SECRET_KEY=$aws_secret_key)
  file_format = (type = csv field_optionally_enclosed_by='"' compression = none)
```

## Setting up the credentials

Use the credentials generated above to connect Sortment to your S3 bucket and proceed.<br>





