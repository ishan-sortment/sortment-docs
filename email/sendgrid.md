# SendGrid

Before integrating SendGrid with Sortment, you will need to have an account already set up with SendGrid.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profiles. Under the "Add integration" section, click on the **SendGrid** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **API Key:** On the SendGrid app, find and click on the Settings tab on the left-hand navigation menu. In the sub-menu, click on "API Keys". Create a new API Key and copy it. You may also use a previously generated API Key if you have one.
* **From Email:** In your SendGrid account, from the Settings tab on the left navigation menu, find "Sender Authentication" and copy the details of the Sender you intend on using. Alternatively, you can add a domain or a single user on SendGrid from the same page. This can then be entered into Sortment's "From Email" field.
* **From Name:** Enter the name associated with the Sender that was entered in the "From Email" field.
* **Content type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (rich content including images, buttons and links will be supported) depending on the type of content you intend on pushing in the templates.
* **Reply To:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

**Message Delivery Status**

While Sortment has the capacity to track the notification delivery status, SendGrid requires a manual update of the Sortment Callback Endpoint in order to receive these reports. To update the Callback manually, follow these steps:

1. Log in to your SendGrid account.
2. From the left navigation panel, find **Settings** and navigate to **Mail Settings**.
3. On the page that loads, find **Event Webhooks** and click on the edit icon.
4. On the pop-up that loads, select an **Authentication Method** and enter Sortment's Callback URL given in the SendGrid Integration popup.
5. Select the data you want to be sent by checking the relevant boxes and save the configuration.
6. Test your integration by sending a message from the Sortment app. Your notification delivery status will be displayed in the logs, under the **Delivery** tab.
