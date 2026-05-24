# ValueFirst (Email)

Before integrating ValueFirst with Sortment, you will need to have an account already set up with ValueFirst.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profiles. Under the "Email" section, click on the **ValueFirst** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **Client Id:** From your ValueFirst account, navigate to Developers → Authentication and copy the Client Id.
* **Client Password:** From your ValueFirst account, navigate to Developers → Authentication and copy the Client Password.
* **From Email:** Enter the Email ID from which the emails will be sent. This must be an email ID with a domain that is already registered with ValueFirst.
* **From Name:** Enter the name that you want to be displayed to the recipient on receiving this email.
* **Content type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (rich content including images, buttons and links will be supported).
* **Reply To:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!

**Message Delivery Status**

ValueFirst, by default, provides the status of the message without any additional setup needed. Once the above integration is complete, the status of the notification shared by ValueFirst will be displayed in the logs, under the **Delivery** tab.

***

That's the full rebranded doc covering all 13 email provider pages — every mention of "Fyno" has been replaced with "Sortment", including the Callback URL naming conventions (e.g. `Fyno-Ses-Configuration-Set` → `Sortment-Ses-Configuration-Set`), portal references, and the App Password generation instruction. Ready to paste into GitBook as-is.
