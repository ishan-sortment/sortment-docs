# Smartping

This guide walks through configuring Smartping as an SMS provider in Sortment, including credential setup, DLT compliance requirements, delivery status configuration, and verification steps.

Before you begin, make sure your Smartping account is fully activated and that you've completed DLT registration (mandatory for India SMS traffic).

### Prerequisites

Before starting the integration, confirm you have the following from Smartping:

* Client Domain (API endpoint domain)
* Username associated with your Smartping account
* API Password (API-level credential, not your dashboard login password)
* Sender/Header approved on DLT
* Entity ID registered on the DLT platform
* Access or permission to configure Delivery Report (DLR) callbacks on Smartping

Messages will fail or be blocked by operators if the Sender ID, Entity ID, or templates are not DLT-approved.

### Setup steps

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose Smartping as the provider. This opens the account configuration panel.

#### 2. Configure the integration

Fill in the following fields:

* **Custom name**: A descriptive name to identify this Smartping account inside Sortment. This is internal to Sortment and doesn't affect message delivery. Base it on use case or traffic type, e.g. "Smartping–OTP", "Smartping–Transactional", "Smartping–Promotions".
* **Client Domain**: The Client Domain provided by Smartping, used as the base URL for API requests. Example format: api.smartping.io. Don't include https:// unless Smartping explicitly instructs you to, and don't add trailing slashes.
* **Username**: The API Username provided by Smartping, used to authenticate API requests. A common mistake is using the dashboard login email instead.
* **API Password**: The API Password associated with your Smartping username, used only for API authentication. Copy and paste carefully to avoid leading or trailing spaces, and update this field if the password is regenerated in Smartping.
* **Sender/Header**: The Sender ID/Header approved on your DLT platform. Typically a 6-character alphanumeric code, uppercase recommended. Must be approved on DLT, mapped to your Entity ID, and linked to the SMS templates you plan to use.
* **Entity ID**: The Entity ID registered with your DLT provider, required for India traffic. Operators validate Entity ID, Sender ID, and Template ID together, so a mismatched or missing Entity ID will cause message rejection.

#### 3. Configure the delivery callback URL

At the bottom of the configuration screen, Sortment displays a Delivery Callback URL. This lets Smartping notify Sortment about message delivery events like sent, delivered, failed, or rejected.

To use it:

1. Copy the Delivery Callback URL from Sortment.
2. Log in to your Smartping dashboard or contact Smartping support.
3. Configure this URL as the DLR / Delivery Report Callback endpoint.

Make sure the HTTP method is supported (GET or POST) and that no authentication blocks Smartping from calling the URL. This step is optional but strongly recommended for production use.

#### 4. Save and activate the account

Double-check all fields, then click Save. The Smartping account will appear under Accounts in the SMS integrations section and becomes available for use immediately.

### Sending a test message

After configuration:

1. Create a test notification in Sortment using SMS as the channel.
2. Select Smartping as the provider.
3. Use a DLT-approved template and a valid mobile number.
4. Send the message.

### Verifying delivery status

If the callback URL is configured correctly:

1. Go to Sent Logs in Sortment.
2. Open the message entry.
3. Review the operator response, final delivery state, and delivery timestamps.

Once set up, Smartping enables DLT-compliant SMS delivery through Sortment with full delivery tracking support.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
