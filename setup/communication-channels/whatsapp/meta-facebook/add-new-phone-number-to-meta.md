# Add new Phone Number to Meta

### Before You Start <a href="#before-you-start" id="before-you-start"></a>

You will need:

* A Meta developer account
* A business app — [learn more about creating apps](https://developers.facebook.com/docs/development/create-an-app/). If you don't see an option to create a **business** app, select **Other** > **Next** > **Business** during app creation).

### Step 1: Add a new phone number <a href="#add-whatsapp-product" id="add-whatsapp-product"></a>

At this point, if you created a new app, you’ll be prompted to **Add products to your app**. Scroll down, and under **WhatsApp**, select **Set up**. Otherwise, select your app from the **My Apps** screen, and you can follow the same instructions again to add the WhatsApp product to your app.

Navigate to the Meta App that is set-up for WhatsApp by going to **developers.facebook.com > My Apps > Select your App.**

1. Use left menu to navigate to the WhatsApp > API Setup panel.
2. On the right pane select Add phone number button under Step 5: Add a phone number.
3. Use the [display name guidelines](https://developers.facebook.com/docs/whatsapp/guides/display-name#display-name-guidelines) to enter a display name for your phone number. This is the name that will show for your business phone number once approved.
4. Select your Timezone. This will be used for WhatsApp Billing and analytics.
5. Select a Category for your business and enter a Business description.
6. Select Next to begin the phone number verification process.
7. Select your country code from the drop down and enter the phone number you would like to register.
8. Select how you would like to receive your verification code, either by Text Message or Phone and click Next to continue. _You will need access to the phone number before selecting Next to receive the verification code._
9. Enter the verification code once received and click Next to continue.
10. The phone number will appear in the From drop down menu of the Send and receive messages section of the panel.
11. Select the newly added phone number to begin sending messages.

### Step 2: Create system user and generate access token

1. Sign into the [Meta Business Suite](https://business.facebook.com/).
2. Locate your business account in the top-left dropdown menu and click its **Settings** (gear) icon.
3. Click **Business settings**.
4. Navigate to **Users** > **System users**.
5. Click the **Add** button and create either an **admin** or **employee** system user.

**Generating System User Access Tokens**

To generate a System User access token after creating a system user:

1. Sign into the [Meta Business Suite](https://business.facebook.com/).
2. Locate your business account in the top-left dropdown menu and click its **Settings** (gear) icon.
3. Click **Business settings**.
4. Navigate to **User** > **System users**.
5. Select the appropriate system user from the list of system users.
6. Click the **Generate new token** button.
7. Select the app that will use the token.
8. Provide access to "WhatsApp Business Messaging" and "WhatsApp Business Management" and generate the token.

### Step 3: Get Phone Number ID

1. Navigate to your [Business Manager](https://business.facebook.com/settings/apps) page and choose the business you want to integrate.&#x20;
2. Select "**Apps**" under "**Accounts**" and find the App you are integrating on the page. On the top right corner, find "[**Open in App Dashboard**](https://developers.facebook.com/apps/)", which will open a new page.
3. Find "**Getting Started**" under "**WhatsApp**" from the left navigation panel.&#x20;
4. In the "Send and Receive Message", find the number you want to use in the "Phone Number" drop-down and select it.
5. This will display the "Phone Number ID" right below the drop-down menu. This will be your "Phone Number ID" on Sortment.

### Step 4: Get WhatsApp Business Account ID

1. Navigate to Business Settings -> Accounts -> WhatsApp accounts -> Account Name.&#x20;
2. On top right corner, you will find the WhatsApp Business Account ID (WABA ID)

### Step 5: Message Delivery Status

To update the Callback URL in Meta, follow these steps:

1. Log in to your Meta account.
2. Navigate to [**App Dashboard**](https://developers.facebook.com/apps/) and find the app you want to connect to and click on it.
3. On the page that loads, scroll down to find **Webhooks** under **Add products to your app** and Click on **Set Up**.
4. On the new page, select **User** from the drop-down and click on **Subscribe to this Object**.
5. Subscribe to these topics - 'message\_template\_quality\_update', 'message\_template\_status\_update' and 'messages'. Choose version as v18.0
6. Enter the Callback URL provided in the Meta Integration popup in the **Callback URL** field and enter a string in the **Verify Token** field. This will be relayed to you by Meta for all your verification requests. 'Verify Token' can be any string.
