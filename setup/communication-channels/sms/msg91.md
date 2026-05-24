# MSG91

Before we get started, you will need to have an MSG91 account already set up, along with SenderID added.

### Setup your MSG91 account on Sortment

1. Navigate to Integrations.
2. Under SMS section, click on the MSG91 button.
3. In the pop-up, fill in:
   1. **Name**: Provide a name to help you identify the configured account in Sortment.
   2. **Auth Key**: Enter the Auth Key from MSG91 account. Go to navigation menu -> Settings -> Auth Key. Create a new one, or use an existing one.
   3. **Sender**: Enter the Sender ID that you want to use. You can access it from Navigation Menu -> Sender id
   4. **Route**: Select the route from the drop-down depending on the message type - Transactional, Promotional or OTP.
4. Click on "Test Integration" once done. If the account is successfully connected, you will see a success message.

### Message Delivery Status

While Sortment has the capacity to track the notification delivery status, MSG91 requires a manual update of the Sortment Callback Endpoint in order to receive these reports. To update the Callback manually follow these steps:

1. Log in to your MSG91 account.
2. Navigate to **Configuration** and find "**Webhook**" from the left navigation bar
3. Configure the given URL in the MSG91 Integration popup: [https://callback.fyno.io/?fyno-provider=msg91](https://callback.fyno.io/?fyno-provider=msg91)
