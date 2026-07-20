# ValueFirst

Before you begin, you will need a ValueFirst account already set up, with Sender ID and templates added.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose ValueFirst as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **Username**: The username you use to log into your ValueFirst account.
* **API Key**: Generate a permanent API Key from the Key Management tab in your ValueFirst account. Use this key in the cURL command below to fetch your token:

```
curl --location 'https://http.myvfirst.com/smpp/api/sendsms/token?action=generate' \
--header 'Content-Type: application/json' \
--header 'apikey: {{apikey-from-ui}}' \
--data '{
  "old_token": "{{old-token-from-ui}}"
}'
```

* **Sender**: Enter the Sender ID you want to use.
* **Account Type**: Select SMPP (Short Message Peer-to-Peer) or PSMS (Platform Service Management System).

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

ValueFirst provides message delivery status by default, with no additional setup needed.

Once the integration is complete, the delivery status shared by ValueFirst will show up in the logs. Click on a log entry and check the Delivery tab.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
