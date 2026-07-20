# Syniverse

Before you begin, you will need a Syniverse account already set up, with a Sender ID and registered numbers assigned. Alternatively, you can use the numbers publicly available on the platform for testing.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Select the SMS channel, then click Add integration and choose Syniverse as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **Access Token**: Log into Syniverse, go to the Applications page, and click the application you want to connect. Find the Auth Keys section, expand it, and copy the Access Token into the field in Sortment.
* **Sender Address/Channel**: Log into Syniverse, go to the Applications page, and click Voice and Messaging Console. Select the relevant account. From the left navigation, expand Messaging Account → Private Channels, select the channel you want to connect, and copy the channel ID. In Sortment, enter "channel:" followed by that ID.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

Sortment can track notification delivery status, but Syniverse requires a manual update of the Callback Endpoint to receive these reports. To update it:

1. Log into Syniverse. On the homepage, expand Event Manager and click Delivery Configurations.
2. Click New Delivery Configuration. Give it a name, enter the Sortment Callback URL, set Delivery Protocol to REST and Delivery Format to JSON, then save.
3. From the Event Manager menu, click Subscriptions, then New Subscription, and fill in:
   * Topic: SCG-Message
   * Event Type: All types
   * Delivery Configuration: the one you just created
   * Matching Criteria: leave blank
   * Start Time: enter a time and date
   * End Time: leave blank so the callback URL doesn't expire
4. Click Create.

You can now send a test message from Sortment using Syniverse as the provider and check the delivery logs in your Sent Logs.

#### Artifacts

Sortment sms bsnlDocument · MD&#x20;
