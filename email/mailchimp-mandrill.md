# Mailchimp (Mandrill)

###

Before integrating Mailchimp with Sortment, you will need to have an account already set up in Mailchimp with Domains and API Keys already created.

> **Note:** Only transactional emails are processed through Sortment for Mandrill (Mailchimp). Campaigns are currently not supported.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profile. Under the "Email" section, click on the **Mailchimp** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **API Key:** Log in to your Mailchimp account. Navigate to the "Transactional email" tab and click on the "Launch App" button in the top right corner. On the new page that opens, from the left navigation pane, click on "Settings". Find the API Keys section and create a new API Key.
* **From Email:** Enter the From Email address you want to use. This email ID has to be a domain that has already been whitelisted in the [Domains](https://mandrillapp.com/settings/sending-domains) section of Mailchimp. If not added, go ahead and add the domain by clicking on "Add" and follow the instructions to complete verification, DKIM and SPF setup.
* **From Name:** Enter the name associated with the Sender Signature that was entered in the "From Email" field.
* **Content type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (rich content including images, buttons and links will be supported) depending on the type of content you intend on pushing in the templates.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

**Message Delivery Status**

While Sortment has the capacity to track the notification delivery status, Mailchimp requires a manual update of the Sortment Callback Endpoint in order to receive these reports. To update the Callback manually, follow these steps:

1. Log in to your Mailchimp account.
2. From the left navigation panel, find and click on "Settings". On the page that opens, find and click on "Webhooks" on the ribbon menu.
3. Click on "Add a Webhook", select all the triggers you need, enter the Callback URL given in the Mailchimp Integration popup, and save.
4. Test your integration by sending a message from the Sortment app. Your notification delivery status will be displayed in the logs, under the **Delivery** tab.
