# Twilio

Before you begin, you will need a Twilio account already set up, with a Messaging Service SID.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose Twilio as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **Account SID**: In Twilio, under the Account tab in the top right, find API Keys and Tokens. Use the live credentials.
* **Auth Token**: In the same section, use the eye icon to reveal the Auth Token. Use the live credentials.
* **Messaging Service SID**: In Twilio, under Develop in the left navigation, go to Messaging → Services. Create a new Messaging Service or use an existing one.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

Twilio provides message delivery status by default, with no additional setup needed.

Once the integration is complete, the delivery status shared by Twilio will show up in the logs. Click on a log entry and check the Delivery tab.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
