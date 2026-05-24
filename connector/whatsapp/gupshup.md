# Gupshup

This guide explains how to connect your **Gupshup WhatsApp account** with **Sortment** to send WhatsApp campaigns and track message delivery statuses.

***

### Prerequisites

Before starting the integration, ensure the following are already set up in your **Gupshup (gupshup.io)** account:

* An **active WhatsApp business number**
* **WhatsApp templates** created and approved
* Access to **Gupshup API credentials** (API Key, App ID, Bot Name)
* Access to **Gupshup Webhooks** (for delivery status tracking)

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **Gupshup** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, fill in the following details:

#### Custom Name

Provide a name to help you identify this Gupshup sender within Sortment\
&#xNAN;_(Example: “Gupshup – WhatsApp Prod”)_

***

#### API Key

* Log in to your **Gupshup** account
* Navigate to **Settings**
* Copy the **API Key**
* Paste it into the API Key field in Sortment

***

#### Bot Name

* Found under **Settings** in your Gupshup dashboard
* This is the **App Name / Bot Name**
* Paste the exact value into the **Bot Name** field

***

#### App ID

* Navigate to **Settings** in Gupshup
* Copy the **App ID**
* Paste it into the App ID field in Sortment

***

#### From Phone Number

* Enter the registered **WhatsApp Business Number**
* **Do not include the “+” symbol**

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once validation succeeds, the integration will be activated

Your Gupshup WhatsApp sender is now ready to be used in Sortment campaigns 🎉

***

### Message Delivery Status Configuration (Required)

Gupshup requires a **manual webhook configuration** to send message delivery updates to Sortment.

#### Steps to Enable Delivery Status Tracking

1. Log in to your **Gupshup** account
2. From the top navigation bar, click **Webhooks**
3. In the **Callback URL** field:
   * Paste the **Callback URL** shown in the Gupshup integration pop-up in Sortment
4. Scroll to **Message Events Settings**
5. Select **all Message Events and System Events**
6. Save the configuration
