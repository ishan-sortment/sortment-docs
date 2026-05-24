# SES

You must have an Amazon SES SMTP username and password to access the SMTP interface. These credentials are different from your AWS access keys and are unique to each region.

[Steps to create your AWS SMTP credentials](https://docs.aws.amazon.com/ses/latest/dg/smtp-credentials.html)

Follow the steps below to integrate your AWS SMTP account with Sortment.

1. In the Workspace dropdown, click on **Modify Setup** and navigate to Channels.
2. Click on **Add Channel** button and select **SES** from the email list.
3. Following details are required for the integration:
   1. **Name:** Provide a name that would help you identify the configured account in Sortment.
   2. **Access Key ID:** To get the access key ID, log into your Amazon AWS account and from the top right corner, open the menu by clicking on your name and navigate to "Security Credentials". On the page that opens, find "Access Keys" and enter the details.
   3. **Secret Access Key:** To get the access key ID, log into your Amazon AWS account and from the top right corner, open the menu by clicking on your name and navigate to "Security Credentials". On the page that opens, find "Access Keys" and enter the details.
   4. **Region:** From your Amazon AWS account, find the region either in the browser URL or you may also select the Region as per the drop-down next to your username in the AWS console.
   5. **Content-Type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (Rich content including images, buttons and links will be supported) depending on the type of content you intend on pushing in the templates. It is recommended to set this as "Text/HTML".
   6. **From Email:** Enter the Email ID from which the emails will be sent from. This must be an email ID with a domain that is already registered with Amazon SES.
   7. **From Name:** Enter the name that would be displayed in the "From" line. It may be a person or a group name.
   8. **Reply to:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.

> ### 📘You can only send emails to pre-registered email IDs that have been verified within Amazon SES.

### Message Delivery Status

While Sortment has the capacity to track the notification delivery status, SES requires a manual update of the Callback Endpoint in order to receive these reports. To update the Callback manually follow these steps:

1. Log into your AWS account and navigate to SES. Find **Configuration Sets** from the left navigation menu and on the page that loads, click on **Create Set**.
2. Name the new set as "Fyno-Ses-Configuration-Set" and click on **Create Set**.
3. Once the configuration is saved, click on the configuration, and navigate to the **Events Destination** tab on the ribbon menu.
4. On this page, click on **Add Destination**, select all the event types and click on **Next**.
5. From the Destination options on the new page, select **Amazon SNS** and name the destination as "Fyno-Ses-Destination".
6. Next, on the same page, click on **Create SNS topic**. Name it “Fyno-Ses-Sns-Topic” and click on **Create Topic**.
7. Select the topic “Fyno-Ses-Sns-Topic” from the SNS topic drop-down under “**Amazon Simple Notification Service (SNS) topic**” and click on **Next**.
8. Review your configuration and click on **Add Destination** button.
9. Now, you will need to access your Amazon SNS and navigate to **Topics** from the left navigation pane. On the page that loads, click on “Fyno-Ses-Sns-Topic” and click on **Create Subscription**.
10. On the page that loads, select the protocol as **HTTPS** from the menu.
11. For the endpoint, please fill in the following Callback URL and check the box marked **Enable raw message delivery** and click on **Create Subscription**.\
    Callback URL: https://callback.fyno.io/?fyno-provider=ses
12. To verify the subscription request, click on **Subscriptions** on the left navigation panel. Your subscription will now be listed with a **Confirmed** status.

### Troubleshooting

1. Ensure that the configuration set is named as “Fyno-Ses-Configuration-Set”&#x20;
2. Please visit [Amazon SES email sending metrics FAQs](https://docs.aws.amazon.com/ses/latest/dg/faqs-metrics.html) for understanding several metrics about the email you send
