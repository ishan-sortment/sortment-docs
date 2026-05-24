# SES (Amazon Simple Email Service)

Before integrating Amazon SES with Sortment, you will need to have an account already set up with SES.

You must have an Amazon SES SMTP username and password to access the SMTP interface. These credentials are different from your AWS access keys and are unique to each region.

[Steps to create your AWS SMTP credentials](https://docs.aws.amazon.com/ses/latest/dg/smtp-credentials.html)

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profiles. Under the "Email" section, click on the **SES** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **Auth Type:** There are 2 different Auth Types:
  * **Secret Access Key**
    * **Access Key ID:** Log into your Amazon AWS account, open the menu from the top right corner by clicking on your name, and navigate to "Security Credentials". On the page that opens, find "Access Keys" and enter the details.
    * **Secret Access Key:** Same as above — navigate to "Security Credentials" and find "Access Keys".
  * **SMTP Password**
    * **SMTP Username:** Log into your Amazon AWS account and search for SES. Click on 'Amazon Simple Email Service'. Go to SMTP settings in the left navigation pane. Click 'Create SMTP Credentials' and then click 'Create User'. Save or download the SMTP username and password details.
    * **SMTP Password:** Same process as above.
* **Region:** From your Amazon AWS account, find the region either in the browser URL or via the Region drop-down next to your username in the AWS console.
* **Content-Type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (rich content including images, buttons and links will be supported).
* **From Email:** Enter the Email ID from which the emails will be sent. This must be an email ID with a domain that is already registered with Amazon SES.
* **From Name:** Enter the name that would be displayed in the "From" line. It may be a person or a group name.
* **Reply to:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.

> **Note:** You can only send emails to pre-registered email IDs that have been verified within Amazon SES.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

**Message Delivery Status**

While Sortment has the capacity to track the notification delivery status, SES requires a manual update of the Sortment Callback Endpoint in order to receive these reports. To update the Callback manually, follow these steps:

1. Log into your AWS account and navigate to SES. Find **Configuration Sets** from the left navigation menu and click on **Create Set**.
2. For convenience and trackability, name the new set **Sortment-Ses-Configuration-Set** and click on **Create Set**.
3. Once the configuration is saved, click on the configuration and navigate to the **Events Destination** tab on the ribbon menu.
4. Click on **Add Destination**, select all the event types, and click on **Next**.
5. From the Destination options, select **Amazon SNS** and name the destination **Sortment-Ses-Destination**.
6. On the same page, click on **Create SNS topic**. Name it **Sortment-Ses-Sns-Topic** and click on **Create Topic**.
7. Select the topic **Sortment-Ses-Sns-Topic** from the SNS topic drop-down under "Amazon Simple Notification Service (SNS) topic" and click on **Next**.
8. Review your configuration and click on **Add Destination**.
9. Now, access Amazon SNS and navigate to **Topics** from the left navigation pane. Click on **Sortment-Ses-Sns-Topic** and click on **Create Subscription**.
10. On the page that loads, select the protocol as **HTTPS**.
11. For the endpoint, fill in the Callback URL given in the SES Integration popup, check the box marked **Enable raw message delivery**, and click on **Create Subscription**.
12. Your subscription request will automatically be approved by Sortment. To verify, click on **Subscriptions** on the left navigation panel — your subscription will now be listed with a **Confirmed** status.
13. Test your integration by sending a message from the Sortment app. You will be able to see the delivery details under the **Delivery** tab in Sent logs.

> **Troubleshooting:** Ensure that the configuration set is named exactly **Sortment-Ses-Configuration-Set**. Please visit [Amazon SES email sending metrics FAQs](https://docs.aws.amazon.com/ses/latest/dg/faqs-metrics.html) for understanding several metrics about the email you send.
