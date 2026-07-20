# JioCx

Before you begin, you will need a Jio account already set up, with Sender ID and templates configured.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose JioCx as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **Org Name**: The organisation name Jio assigns for this integration.
* **Username**: The username shown on your Jio account dashboard when you log in.
* **Password**: The password used to log into the account entered above.
* **Sender/Header**: Enter the Sender ID you want to use.
* **DLT Entity ID**: Enter your DLT registered Entity ID.
* **Route**: Select the route: Transactional, Promotional, or OTP.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

JioCx does not provide message delivery status by default. You will need to contact Jio to enable the Callback Endpoint and status updates via webhooks.

Once the integration is complete, the delivery status shared by JioCx will show up in the logs. Click on a log entry and check the Delivery tab.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
