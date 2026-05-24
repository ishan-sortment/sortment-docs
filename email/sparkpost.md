# Sparkpost



Before integrating Sparkpost with Sortment, you will need to have an account already set up with Sparkpost.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profiles. Under the "Email" section, click on the **Sparkpost** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **Sparkpost Region:** You can choose either Default or EU based on your location.
* **SMTP User:** From your Sparkpost account, navigate to Configuration → SMTP Settings and select SMTP user.
* **Password:** Enter the password associated with the SMTP User entered above.
* **From Name:** Enter the name that you want to be displayed to the recipient on receiving this email.
* **From Email:** Enter the Email ID from which the emails will be sent. This must be an email ID with a domain that is already registered with Sparkpost.
* **Content type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (rich content including images, buttons and links will be supported).
* **Reply To:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

**Message Delivery Status**

While Sortment has the capacity to track the notification delivery status, Sparkpost requires a manual update of the Sortment Callback Endpoint in order to receive these reports. To update the Callback manually, follow these steps:

1. Log into your Sparkpost account and click on the "Configurations" tab on the top navigation panel, then go to **Webhooks**.
2. Add Sortment's webhook for each event type by clicking on **Create Webhook**. Please create and add a webhook for all the statuses using Sortment's Callback URL given in the Sparkpost Integration popup.
