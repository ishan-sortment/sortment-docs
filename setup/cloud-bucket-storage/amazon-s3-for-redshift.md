# Amazon S3 for Redshift

As discussed in [cloud bucket storage setup](./), Amazon S3 is required for several data-related use cases in Sortment.

{% hint style="success" %}
In AWS, accessing S3 via Redshift requires IAM Role ARN to prevent exposing user or access key details via SQL query.

For APIs, access is managed via Access Keys.
{% endhint %}

## Connection configuration

Following details are requied on Sortment for S3 connection for Redshift:

* **AWS Region:** The geographical region where your AWS services, including S3 and Redshift, are deployed. Examples include us-east-1 (N. Virginia) or ap-south-1 (Mumbai). In your [AWS Console](https://console.aws.amazon.com/console/home) → Click on your profile (top-right) → See the selected region.
* **AWS S3 Bucket Name:** A globally unique name assigned to an S3 bucket where you store and retrieve data. On [AWS Console](https://console.aws.amazon.com/console/home) → Go to S3 → Locate your bucket under “Buckets” list.
* **Access Key ID:** A unique identifier for an AWS IAM user or service that allows programmatic access to AWS services. On [AWS Console](https://console.aws.amazon.com/console/home) → IAM → Users → Select your user → Security Credentials tab → Generate Access Key.
* **Secret Access Key:** A secret key paired with the Access Key ID, used for signing API requests securely. Generated alongside the Access Key ID in IAM (only shown once). If lost, you must generate a new pair.
* **IAM Role ARN:** A unique identifier for an IAM Role that allows Redshift to interact with S3. On [AWS Console](https://console.aws.amazon.com/console/home) → IAM → Roles → Find your role → Copy the Role ARN.

## AWS credentials setup

{% hint style="danger" %}
This region for S3 Bucket should be same as your Redshift region for lower data egress costs.
{% endhint %}

Follow these steps to setup an S3 bucket for Sortment:

#### Creating a bucket

1. Sign in to the AWS Management Console and [navigate to the S3 service](https://console.aws.amazon.com/s3/home).
2. Click on "Create bucket."
3. Enter a unique bucket name (globally unique across AWS).
4. Select an AWS region for the bucket. This should be same as your Redshift cluster region.
5. Create the bucket.

#### Creating a policy

1.  From your AWS console navigate to **Identity and Access Management (IAM)** > **Access Management** > **Policies**<br>

    <figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>
2. In the JSON policy editor, use the following policy. Update `{$bucket-name}` to the bucket created above. Give your policy a name and create the policy.

{% hint style="info" %}
For Redshift to load data into an S3 bucket, it needs access to list all buckets it has access to. This is covered with resource level policy below.
{% endhint %}

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

#### Creating a role

1.  Now, navigate to **Identity and Access Management (IAM)** > **Access Management** > **Roles** and click **Create Role**.<br>

    <figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>
2.  Give access to the policy created for Sortment.<br>

    <figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>
3. Next, setup the name and description and create the role.
4. Copy the role ARN. This will be used in S3 setup form on Sortment.

#### Associating role with your Redshift cluster or serverless namespace

**Serverless**

Attach the IAM role at the **Namespace** level.

1. In AWS Console, open **Amazon Redshift** (correct region).
2. Go to **Serverless → Namespaces**.
3. Click your namespace (often `default-namespace`).
4. Open the **Security and encryption** tab.
5. Under **Permissions → IAM roles**, click **Manage IAM roles**.
6. Select the IAM role you created for Sortment (e.g., `sortment_role`) and click **Add**.
7. (Optional) Set it as **Default** for COPY/UNLOAD to use this role automatically.
8. Save. The role should show **in-sync** with its ARN.\
   <br>

**Provisioned clusters**

Attach the IAM role at the **Cluster** level.

1. Go to **Amazon Redshift → Clusters** and open your cluster.
2. Click **Actions → Manage IAM roles**.
3. Add the role and save.
4. (Optional) Set a default role for COPY/UNLOAD.

**Verification (optional)**

Confirm Redshift can write to S3 using the role:

```sql
UNLOAD ('SELECT 1 AS test_col')
TO 's3://<your-bucket>/sortment/smoke/test_'
IAM_ROLE 'arn:aws:iam::<account-id>:role/<role-name>'
ALLOWOVERWRITE;
```

#### Configuring Access Key

The **Access Key** access type allows you to configure Sortment to use an IAM user by providing the user's **Access Key ID** and **Secret Access Key**.

If you need help generating these keys, consult the [IAM article](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) on this topic.

Once you have an Access Key ID and Secret Access Key, paste those values into the form and click **Create**.<br>
