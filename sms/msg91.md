# MSG91

Before you begin, you will need an MSG91 account already set up, with Sender ID added.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose MSG91 as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **Auth Key**: Found in your MSG91 account under Configurations → Auth Key. Create a new one or use an existing one.
* **Sender**: Enter the Sender ID you want to use.
* **Route**: Select the route based on message type: Transactional, Promotional, or OTP.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

Sortment can track notification delivery status, but MSG91 requires a manual update of the Callback Endpoint to receive these reports. To update it:

1. Log in to your MSG91 account.
2. Go to Configuration and find Webhook in the left navigation.
3. Configure the POST URL, which you can retrieve from the integration pop-up in Sortment.

Once set up, send a test message from Sortment using MSG91 as the provider and check the delivery logs in your Sent Logs.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
