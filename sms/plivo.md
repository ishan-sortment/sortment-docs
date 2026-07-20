# Plivo

Before you begin, you will need a Plivo account already set up, with Sender ID and templates configured.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose Plivo as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **Auth ID**: Log into Plivo, click Messaging in the left navigation, and find Auth ID under Accounts and Payments.
* **Auth Token**: Found in the same place as the Auth ID.
* **Source**: Select one of:
  * Sender ID — alphanumeric, registered on your Plivo account
  * Phone Number — numeric only, registered on your Plivo account
  * Powerpack UUID — created in Plivo under Messaging → Powerpacks; create a new one or use an existing one
* **Sender ID/Phone Number/Powerpack UUID**: Enter the value matching the Source you selected above.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

Plivo provides message delivery status by default, with no additional setup needed.

Once the integration is complete, the delivery status shared by Plivo will show up in the logs. Click on a log entry and check the Delivery tab.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
