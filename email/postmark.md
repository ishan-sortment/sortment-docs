# Postmark

Before integrating Postmark with Sortment, you will need to have an account already set up in Postmark with Servers and Sender Signatures already created.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profiles. Under the "Email" section, click on the **Postmark** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **Server Token:** Log into Postmark and navigate to "Servers" and find the server you would like to integrate. Find the tab "API Tokens" on the ribbon menu and click on it to obtain the Server API token.
* **From Email:** Enter a Sender Email that has been pre-registered as a [Sender Signature](https://account.postmarkapp.com/signature_domains) in the Postmark application.
* **From Name:** Enter the name associated with the Sender Signature that was entered in the "From Email" field.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

**Message Delivery Status**

While Sortment has the capacity to track the notification delivery status, Postmark requires a manual update of the Sortment Callback Endpoint in order to receive these reports. To update the Callback manually, follow these steps:

1. Log in to your Postmark account.
2. Click on **Servers** and select the server you want to connect.
3. On the page that opens, select the **Message Stream**. On the new page, click on **Webhooks** on the ribbon menu and click on the **Add Webhooks** button.
4. Enter Sortment's Callback URL given in the Postmark Integration popup, select the relevant notifications required, and save.
5. Test your integration by sending a message from the Sortment app. Your notification delivery status will be displayed in the logs, under the **Delivery** tab.
