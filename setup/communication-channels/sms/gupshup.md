# Gupshup

Before we get started, you will need to have a Gupshup account already set up, along with SenderID and Templates.

1. In the Workspace dropdown, click on **Modify Setup** and navigate to **Channels**.
2. Click on **Add Channel** button and select **Gupshup** from the SMS list.
3. Following details are required for the integration:
   1. **Custom name**: Provide a name that would help you identify the configured account in Sortment.
   2. **UserID**: The CustomerID that is displayed on your Gupshup Account when you log in and view the dashboard
   3. **Password**: Password used to log into the Customer ID entered in the previous field
   4.  **Sender**: The Mask (SenderId) that is being used by you to send out messages. You can get the Mask (SenderId) by going to _DLT Template (in the top nav)-> Download approved templates._ In the downloaded file, get the source from the 'Mask' column.<br>

       <figure><img src="../../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>
4. Click on "Add Account" once done, and you are all set!

### Message Delivery Status

While Sortment can track the message delivery status, Gupshup requires a manual update of the Callback Endpoint in order to receive these reports. To update the Callback manually follow these steps:

1. Log into your Gupshup Messaging Account.
2. Click on **Settings** on the Menu bar and find **SMS Settings**.
3. On the page that opens, find **Realtime Delivery URL** setting and configure the given URL: _https://callback.fyno.io/?fyno-provider=gupshup_
4. Click Save to complete the setup.

<figure><img src="../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
