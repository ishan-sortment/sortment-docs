# Infobip

This guide explains how to connect your **Infobip WhatsApp account** with **Sortment** to send WhatsApp campaigns and view delivery statuses.

***

### Prerequisites

Before starting the integration, ensure the following are already set up in your **Infobip** account:

* An **active WhatsApp business number**
* **WhatsApp templates** created and approved
* Access to **Infobip API credentials**
* Required **API scopes enabled** for WhatsApp

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **Infobip** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, fill in the following details:

#### Custom Name

Provide a name to help you identify this Infobip WhatsApp sender within Sortment\
&#xNAN;_(Example: “Infobip – WhatsApp Prod”)_

***

#### From Number

Enter the registered **WhatsApp business number** used to initiate conversations.

To find or add a number in Infobip:

1. Log in to your **Infobip** account
2. Go to **Channels and Numbers → Numbers**
3. If a WhatsApp number is already added, you’ll see the **Mobile Number** and **Sender Name**
4. To add a new number, click **Buy Number**

Enter the selected number in Sortment **without the “+” symbol**.

***

#### Base URL

* You can find this on the **Infobip home page**
* Format:\
  `xxxxx.api.infobip.com`
* Copy and paste this value into the **Base URL** field in Sortment

***

#### API / Account Key

1. In Infobip, go to **Menu → Developer Tools → API Keys**
2. Copy an existing API Key **or** click **Create API Key**
3. Paste the key into the **API / Account Key** field in Sortment

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once validation succeeds, the integration will be activated

Your Infobip WhatsApp sender is now ready to be used in Sortment campaigns 🎉

***

### Enable Required API Scopes (Mandatory)

To send WhatsApp messages and **sync WhatsApp templates** with Sortment, the API Key must have the required scopes enabled.

#### Steps to Enable API Scopes

1. In Infobip, go to **Developer Tools → API Keys**
2. Create a new API Key **or** open an existing one
3. In **Available API Scopes**, search for **WhatsApp**
4. Enable the following scopes:
   * `whatsapp:manage`
   * `whatsapp:message:send`
5. Click **Save**

Once enabled, Sortment will be able to:

* Send WhatsApp messages
* Sync WhatsApp templates from Infobip

***

### Message Delivery Status

**No additional setup is required.**

Infobip provides message delivery statuses by default.

