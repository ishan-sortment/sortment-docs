# TrustSignal

Before you begin, you will need a TrustSignal account already set up, with Sender ID and templates configured.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose TrustSignal as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **API Key**: In TrustSignal, go to SMS → SMS API in the left navigation.
* **Sender**: In TrustSignal, go to SMS → SMS Settings → Headers, and use the value(s) in the Header column.
* **Type of Route**: Select the route type based on the configuration added in your TrustSignal application.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

Sortment can track notification delivery status, but TrustSignal requires a manual update of the Callback Endpoint to receive these reports. To update it:

1. Log into your TrustSignal Messaging account.
2. Go to SMS → SMS Settings → SMS Webhook.
3. Enter the URL from the TrustSignal integration pop-up in Sortment, and save.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
