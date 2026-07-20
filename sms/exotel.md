# Exotel

Before you begin, you will need an Exotel account already set up, with Sender ID and templates configured.

#### 1. Find the provider

Go to Settings → Engagement Setup → Sender Profiles. Click Add integration, select SMS as the channel, then choose Exotel as the provider.

#### 2. Configure the integration

In the pop-up, fill in:

* **Custom name**: A name to help you identify the configured account in Sortment's portal.
* **API Key**: From your Exotel account, find API Credentials at the top of the application and click on it. On the new page, click Create an API Key, or use an existing one.
* **API Token**: Corresponding to the API Key copied above, copy and paste the API Token as well.
* **Account SID**: From the same API Credentials page, find the Account SID and paste it into Sortment.
* **Sub-Domain**: From the same API Credentials page, find the subdomain and select one: api.exotel.com or api.in.exotel.com.
* **Type of SMS**: Choose the type of SMS you intend to trigger: Transactional, Transactional\_opt\_in, or Promotional.
* **Sender/Header**: Enter the Sender ID you want to use.
* **Entity ID**: Enter your DLT registered Entity ID.

#### 3. Complete the integration

Click Save once done, and you are all set.

### Message delivery status

Exotel does not provide message delivery status by default. You will need to speak with your Exotel account manager to get this configured.

Once the integration is complete, the delivery status shared by Exotel will show up in the logs. Click on a log entry and check the Delivery tab.

