# OneXtel

Before you begin, you will need an active OneXtel account with the required SMS credentials and DLT details configured.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose OneXtel as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured OneXtel account within Sortment.
* **API Key**: The API key generated from your OneXtel account, used to authenticate SMS requests sent through Sortment.
* **Sender/Header**: The Sender ID (Header) approved for your OneXtel account, used when sending SMS notifications.
* **Entity ID**: The DLT-registered Entity ID associated with your organization.
* **Delivery Callback URL**: Copy the callback URL shown in Sortment and configure it in your OneXtel account. This lets Sortment receive delivery reports and update message statuses.

#### 3. Complete the integration

Click Save once all the required details have been entered, and you're ready to send SMS notifications using OneXtel.

### Message delivery status

To receive SMS delivery updates in Sortment, the Delivery Callback URL configured in the integration must also be set up in your OneXtel account.

Once the callback configuration is complete, delivery events shared by OneXtel will show up in the logs. Open the relevant notification and check the Delivery tab for details.

Make sure the callback URL configured in OneXtel matches the one provided in Sortment. A mismatch will prevent delivery statuses from updating.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
