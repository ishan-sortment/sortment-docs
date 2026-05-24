# SMTP

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profiles. Under the "Email" section, click on the **SMTP** button.

**Step 2 — Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **SMTP Host:** Enter the SMTP Host. For example, for Gmail, the fully qualified domain name of the SMTP service is _smtp.gmail.com_.
* **SMTP Port:** Select from one of the port options — 25, 465, or 587.
* **SMTP Username:** Enter the SMTP username from your email service provider.
* **Password:** Enter the password associated with the SMTP User entered above.
* **From Name:** Enter the name that you want to be displayed to the recipient on receiving this email.
* **From Email:** Enter the Email ID from which the emails will be sent. This must be an email ID with a domain that is already registered with your email service provider.
* **Content type:** You can choose either "Text/Plain" (no rich content in emails, simple plain text) or "Text/HTML" (rich content including images, buttons and links will be supported) depending on the type of content you intend on pushing in the templates.
* **Reply To:** This is an optional field. You may enter an alternate email ID so that when the recipient clicks on "Reply", the email ID you have entered in the "Reply To" will be populated. This can be different from the "From" email ID.
* **DSN Support:** Select yes if your delivery service supports it (not all SMTP servers have the DSN extension enabled). Set up the Delivery Callback URL on your SMTP provider for Sortment to receive delivery reports.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and you are all set!
