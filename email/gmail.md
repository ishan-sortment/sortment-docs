# Gmail

Before we get started, you will need to have 2-factor authentication activated on your Google Account. This can be done by simply navigating to Google's [2 Factor Authentication Guide](https://support.google.com/accounts/answer/185839?hl=en\&ref_topic=2954345).

> In case you do deactivate the 2-factor authentication, the passcode will be rendered inactive, in which case the same process will have to be repeated after re-activating 2 Factor Authentication.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profile. Under the "Email" section, click on the **Gmail** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **Email:** The email address from which the "From" line or email will be sent. This may be a personal or a work email ID with a non-Gmail domain.
* **App Password:** The passcode token can be generated from [Gmail](https://myaccount.google.com/apppasswords) by navigating to Google Account and under the "Security" tab. Go to 2-step verification and find App Passwords under Signing into Google. On the page that loads, enter "Sortment" and click on Generate. Copy the code that appears in the pop-up.
* **From Name:** The name you want to be displayed in the from field to the recipient. This may be an individual or group name and is optional.
* **Content type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (rich content including images, buttons and links will be supported) depending on the type of content you intend on pushing in the templates.
* **Reply to:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

> **Note:** Gmail has a limit on the number of emails that can be sent from personal and corporate email IDs. Read more on [Gmail send limits](https://support.google.com/a/answer/166852?hl=en).

**Message Delivery Status**

Gmail, by default, does not provide the status of the notification sent out. This is not a configurable feature as well. As and when this becomes a supported feature, Sortment will integrate the same into the application. In the meantime, for every Trace for Gmail, the **Delivery** tab under Trace will not be seen.
