# telSpiel

Before you begin, you will need a telSpiel account already set up, with Sender ID and templates configured.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose telSpiel as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **Username/Account ID**: The username or Account ID of your telSpiel account.
* **API Key**: Email [care@telspiel.com](mailto:care@telspiel.com) to request your API key.
* **Sender**: Enter the Sender ID you want to use.
* **Entity ID**: Enter your DLT registered Entity ID, available from your DLT platform.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

telSpiel does not provide message delivery status by default. To enable tracking:

1. Email [care@telspiel.com](mailto:care@telspiel.com) requesting activation of delivery tracking, and include the Callback URL from the telSpiel integration pop-up in Sortment.
2. Enable "custref" in the webhook URL.

Once this is complete, the delivery status shared by telSpiel will show up in the logs. Click on a log entry and check the Delivery tab.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
