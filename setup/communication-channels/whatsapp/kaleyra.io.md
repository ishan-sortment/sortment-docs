# Kaleyra.io

## Overview

Sortment lets you send broadcast messages via your existing Kaleyra account. It is required to set up / have a Kaleyra account before configuring the same on Sortment.&#x20;

### Set up your account on Sortment

1. Navigate to channels. Click **Add channel**
2. Under WhatsApp channel, select **Kaleyra.io** as the provider
3. Setup an integration name (_only alphanumeric allowed, no special characters or spaces_)
4. You need following credentials from Kaleyra (follow steps below)
   1. SID (Security Identifier)
   2. API Key
   3. From Number

#### Configure the Integration

You can get the relevant details from Kalyera account through these steps:

1. **API Key:** Under the "[Developers](https://in.kaleyra.io/api-keys)" tab, you can either copy a  previously created API Key or create a new one.
2. **SID (Security Identifier):** Under the "[Developers](https://in.kaleyra.io/api-keys)" tab, hover on any API key and you will see ellipsis icon in the last column. When you click it, you will see the below options. Click View and you will see the SID details.\
   <img src="../../../.gitbook/assets/image (105).png" alt="" data-size="original">
3. **From Number:** The registered WhatsApp number that you would like to use to initiate conversations. This can be found on the in the "Channels" tab by navigating to the WhatsApp channel and selecting "Manage". Select "Configurations" from the ribbon menu on the top menu to find your configured numbers.
4. **WABA ID:** This can be skipped during the setup. Reach out to your Kalerya account manager to get this value.

#### Complete the Integration

Click on "Add Account" once done, and you are all set!

### Message Delivery Status

While Sortment can track the notification delivery status, Kaleyra.io requires a manual update of the Callback Endpoint in order to receive these reports. To update the Callback manually follow these steps:

1. Log into your Kaleyra.io Account.
2. From the top right corner, under Settings, click on the Settings option in the top ribbon menu.
3. On the page that loads, find **Enable WhatsApp Callback URLs** and configure the Callback URL given in the Kaleyra Integration popup.

