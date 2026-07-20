# Karix

Before you begin, you will need a Karix account already set up, with Sender ID and templates configured.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose Karix as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **API Key**: From your Karix platform, find Power API and click API Keys. Create a new key or use an existing one.
* **Sender**: Enter the Sender ID you want to use.
* **Entity ID**: Enter your DLT registered Entity ID.
* **Route**: Select the route: Transactional, Promotional, or OTP.
* **Delivery callback payload structure**: Email the Karix support team with the delivery callback URL and the sample payload below to set up callbacks on your Karix account.

Sample payload:

```
{
  "reason": "XXXXXX",
  "dtime": "YYYY-MM-DD hh:mm:ss",
  "mid": "201051790526XXXXXX",
  "stime": "YYYY-MM-DD hh:mm:ss",
  "dest": "XXXXXXXXXXXXXXXXXX",
  "type": "0",
  "circle": "XXXXX",
  "send": "SENDER",
  "cust_ref": "SORTMENT_REFERENCE_ID",
  "operator": "OPERATOR",
  "status": "XXX"
}
```

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

Karix does not provide message delivery status by default. You will need to email [provisioning@karix.com](mailto:provisioning@karix.com) to enable the callback URL and status updates via webhooks.

Once the integration is complete, the delivery status shared by Karix will show up in the logs. Click on a log entry and check the Delivery tab.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
