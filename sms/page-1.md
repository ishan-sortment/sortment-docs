# BSNL

Before you begin, you will need a BSNL account already set up, with a Sender ID added.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Click Add integration, select SMS as the channel, then choose BSNL as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **Username**: The username of your BSNL account.
* **Password**: The password of your BSNL account.
* **Sender**: The Sender ID you want to use.
* **Entity ID**: Your DLT registered Entity ID.
* **Circle**: The region or area code. Example: MH.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

Sortment can track notification delivery status, but BSNL requires a manual update of the Callback Endpoint to receive these reports.

Share the Callback URL from the integration page with your BSNL account manager so they can configure it in your BSNL account settings.

Once configured, send a test message from Sortment using BSNL as the Provider and check the delivery logs in your Sent Logs.
