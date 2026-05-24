# Outlook

Before we get started, we also need to understand the account type being configured.

Accounts may be:

* **Outlook / Office 365 Accounts** — These are almost all of the time belonging to an organisation or company.
* **Microsoft / Live Accounts** — These are personal accounts, created by signing up on Microsoft. They do not belong to a company or organisation.

Depending on the type of account, Outlook configuration involves a few prerequisites.

**Prerequisites for Outlook / Office 365 Accounts**

Firstly, you would need to request your administrator to grant you permission to create an app password so that you can send an email through SMTP Auth.

Your Admin will need to perform the following steps:

1. Log into the [Microsoft 365 Admin Center](https://aka.ms/admincenter).
2. In the left navigation pane, find "Active users" under "Users". On the page that opens, find the name of the person. On selecting it, a pop-up will appear on the right.
3. **To enable SMTP:** In the pop-up, find "Mail" on the ribbon menu and find "Manage Email Apps". In the second pop-up that appears, tick the box against **Authenticated SMTP** and save.
4. **To enable App Password Creation:** In the same pop-up, find "Account" and scroll to the bottom to find "Manage Multifactor Authentication". This will open a fresh page. Click on "Service Settings" on the ribbon menu. Find and select **Allow users to create app passwords to sign in to non-browser apps** and click on **Save**.

**To create an App Password:**

1. Log into your account and navigate to [Account Settings](https://myaccount.microsoft.com/). Find the **Account Info** card and click on "Update Info".
2. On the page that opens, click on "Add Sign-in Method". In the pop-up, select **App Password** and click on **Add**, provide a name and hit **Next**.
3. The App Password will be displayed in the pop-up. This won't be displayed again, so make sure to copy it before clicking on **Done**.

**Prerequisites for Microsoft / Live Accounts**

Microsoft or Live accounts are personal accounts, owned by a single person. Usually, the domain would be the default one and these accounts would not need Admin controls enforced.

**To create an App Password:**

1. Log into your account through [Security Basics](https://account.microsoft.com/security) and click on the "Advanced Security Options" card.
2. Scroll to **App Passwords** and click on **Create New App Password**.
3. Copy the App Password that is displayed on the new page and click on **Done**.

**Integrating with Sortment**

Once you have these details in place, we can proceed with the integration into Sortment's app.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profiles. Under the "Email" section, click on the **Outlook** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name to help you identify the configured account in Sortment's portal.
* **Email:** The email address from which the "From" line or email will be sent. This will be the same Email ID for which the settings were updated by the Admin of your organisation.
* **App Password:** Follow the steps mentioned above to create the App Password.
* **From Name:** The name you want to be displayed in the from field to the recipient. This may be an individual or group name and is optional.
* **Content type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (rich content including images, buttons and links will be supported) depending on the type of content you intend on pushing in the templates.
* **Reply to:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

**Message Delivery Status**

Outlook, by default, does not provide the status of the notification sent out. This is not a configurable feature. As and when this becomes a supported feature, Sortment will integrate the same into the application. In the meantime, for every Trace for Outlook, the **Delivery** tab under Trace will not be seen.
