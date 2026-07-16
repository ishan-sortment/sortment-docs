# Interakt

This guide explains how to connect your **Interakt WhatsApp account** with **Sortment** to send WhatsApp campaigns and track message delivery statuses.

***

### Prerequisites

Before starting the integration, ensure the following are already set up in your **Interakt** account:

* An **active WhatsApp business number**
* **WhatsApp templates** created and approved
* Access to **Interakt Developer Settings**

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **Interakt** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, fill in the following details:

#### Custom Name

Provide a name to help you easily identify this Interakt WhatsApp sender within Sortment\
&#xNAN;_(Example: “Interakt – WhatsApp Prod”)_

***

#### API Key

1. Log in to your **Interakt** account
2. Open **Developer Settings**
3. Locate the **Secret Key**
4. Copy the **Secret Key**
5. Paste it into the **API Key** field in Sortment

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once validation succeeds, the integration will be activated

Your Interakt WhatsApp sender is now ready to be used in Sortment campaigns 🎉

***

### Message Delivery Status Configuration (Required)

Interakt requires a **manual webhook configuration** to send message delivery updates to Sortment.

#### Steps to Enable Delivery Status Tracking

1. Log in to your **Interakt** account
2. From the **top-right corner**, open **Developer Settings**
3. Under **Configure Webhook**, click **Configure**
4. On the configuration page:
   * Paste the **Callback URL** shown in the Interakt integration pop-up in Sortment into the **Webhook URL** field
   * Enter the **Secret Key**
5. Under:
   * **Template Messages sent via API**
   * **Template Messages sent via Interakt Campaigns**\
     Select **all required options**
6. Click **Submit**

***

####
