# Connectly

This guide explains how to connect your **Connectly WhatsApp account** with **Sortment** to send WhatsApp campaigns and track delivery statuses.

***

### Prerequisites

Before starting the integration, ensure the following are set up in your **Connectly** account:

* An **active WhatsApp number**
* **WhatsApp templates** created and approved
* Access to **API credentials** (Business ID and API Key)

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **Connectly** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, enter the following details:

#### Custom Name

Provide a meaningful name to help you identify this Connectly account within Sortment\
&#xNAN;_(Example: “Connectly – WhatsApp Prod”)_

#### Business ID

1. Log in to your **Connectly** account
2. Navigate to **Settings** from the left navigation panel
3. Locate **API Key and Webhook Secret**
4. Click on **Generate API Key**
5. Copy the **Business ID** and paste it into the Business ID field in Sortment

#### From WhatsApp Number

Enter the **registered WhatsApp number** linked to your Connectly account.

You can find this in:

* **Settings → General → Messaging Channels**

#### API Key

1. In **Connectly → Settings → API Key and Webhook Secret**
2. Click **Generate API Key**
3. Copy the **API Key**
4. Paste it into the API Key field in Sortment

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once validation succeeds, the integration will be activated

Your Connectly WhatsApp sender is now ready to be used in Sortment campaigns 🎉

***

### Message Delivery Status Configuration (Important)

By default, **Connectly does not send message delivery statuses automatically**.

To enable delivery status tracking:

1. Contact your **Connectly Account Manager**
2. Ask them to **configure a webhook** using the **Webhook URL** shown in the Connectly integration pop-up in Sortment
3. Once configured, Connectly will start sending message status updates to Sortment
