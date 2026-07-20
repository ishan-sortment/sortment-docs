# Sinch

Before you begin, you will need a Sinch account already set up, with Sender ID and templates configured.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose Sinch as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **Route Type**: Select the route based on the configuration added in your Sinch application: OTP or Transaction.
* **Application Id**: In your Sinch portal, click the profile icon in the top right and select Access Keys. You'll find the Application ID (Project ID) there.
* **subappid**: Found in the same Access Keys section as the Sub Application ID (subproject ID).
* **UserId**: Enter the user ID.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

Sinch provides message delivery status by default, with no additional setup needed.

Once the integration is complete, the delivery status shared by Sinch will show up in the logs. Click on a log entry and check the Delivery tab.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
