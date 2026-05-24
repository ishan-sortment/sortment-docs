# Mailgun

Before integrating Mailgun with Sortment, you will need to have an account already set up with Mailgun.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profile. Under the "Email" section, click on the **Mailgun** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **SMTP User:** From your Mailgun account, navigate to Settings and select "Overview". On the page that opens, find "SMTP Credentials". You will see the "username" that you need to enter as "SMTP User".
* **Password:** Enter the password associated with the SMTP User entered above.
* **From Name:** Enter the name that you want to be displayed to the recipient on receiving this email.
* **From Email:** In your Mailgun account, from the Settings tab on the left navigation menu, find "Sender Authentication" and copy the details of the Sender you intend on using. Alternatively, you can add a domain or a single user on Mailgun from the same page. This can then be entered into Sortment's "From Email" field.
* **Content type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (rich content including images, buttons and links will be supported) depending on the type of content you intend on pushing in the templates.
* **Reply To:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

**Message Delivery Status**

While Sortment has the capacity to track the notification delivery status, Mailgun requires a manual update of the Sortment Callback Endpoint in order to receive these reports. To update the Callback manually, follow these steps:

1. Log into your Mailgun account and click on the "Sending" tab on the left navigation panel to expand it and find **Webhooks**.
2. Click on **Webhooks** and add Sortment's webhook for each event type by clicking on **Create Webhook**. Please create and add a webhook for all the statuses using Sortment's Callback URL given in the Mailgun Integration popup.
