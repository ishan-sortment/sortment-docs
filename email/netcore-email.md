# Netcore (Email)



Before we get started, you will need to have your Netcore account already set up with the domain mapped and verified and the content type specified.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profiles. Under the "Email" section, click on the **Netcore** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **API Key:** Log into your Netcore application and click on "Integrations" on the left navigation panel. On the page that loads, find the API tab on the ribbon menu and obtain your API Key.
* **From Email:** Enter the Email ID from which the emails will be sent. This must be an email ID with a domain that is already registered with Netcore.
* **Name:** Enter the name that would be displayed in the "From" line. It may be a person or a group name.
* **Content type:** You can choose either "HTML" or "amp-content" based on your preconfigured setup on Netcore.
* **Reply to:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

**Message Delivery Status**

While Sortment has the capacity to track the notification delivery status, Netcore requires a manual update of the Sortment Callback Endpoint in order to receive these reports. To update the Callback manually, follow these steps:

1. Log in to your Netcore Email API account.
2. Navigate to **Settings** and find **Webhooks**. Enter Sortment's Callback URL and save.
3. Test your integration by sending a message from the Sortment app. Your notification delivery details will be displayed in the logs, under the **Delivery** tab.
