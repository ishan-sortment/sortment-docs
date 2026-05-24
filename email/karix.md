# Karix

Before integrating Karix Email with Sortment, ensure you have an active Karix account with SMTP credentials enabled.

**Step 1 — Find the Provider**

Navigate to the Workspace settings -> Sender profiles. Under the "Email" section, click on the **Karix (Email)** button.

**Step 2 — Configure the Integration**

In the setup panel, fill in:

* **Custom Name:** Provide a recognizable name for this account. _Example: Karix - Production_
* **SMTP User:** Enter your Karix SMTP username. You can obtain it from the Karix support team.
* **Password:** Enter the SMTP password associated with the above user.
* **From Name:** This is the sender name visible to recipients. _Example: Sortment Support_
* **From Email:** Enter the email address used to send emails. **Note:** This must be a verified email/domain in Karix. _Example:_ [_support@yourdomain.com_](mailto:support@yourdomain.com)
* **Content Type:** Defines the email format:
  * `text/html` → Recommended (supports rich email templates)
  * `text/plain` → Plain text emails only
* **Reply To:** Specify the email address where replies should be sent.
* **Delivery Callback URL:** Sortment provides a callback URL. This must be configured in Karix to receive delivery updates.

**Step 3 — Complete the Integration**

Click on **Add Account** once done and your Karix Email account will be connected to Sortment.

**Step 4 — Enable Delivery Tracking**

To receive delivery reports from Karix, you need to enable and configure a callback (webhook) URL on your account.

**Step 5 — Configure Callback in Karix**

Karix does not currently provide a clear self-service option in the dashboard to configure callbacks/webhooks. To enable callback configuration, you will need to reach out to the Karix support team or your account manager. Please share the Sortment Callback URL provided in the Karix integration popup with them — the Karix team will configure this on your behalf.

> **Note:** Karix requires manual configuration of the callback URL to enable delivery tracking. Without this step, delivery status will not be available in Sortment.

**Message Delivery Status**

Sortment can track email delivery statuses only after the callback URL is configured in Karix. To receive delivery reports, ensure the Sortment Callback Endpoint is correctly set in your Karix account.
