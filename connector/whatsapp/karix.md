# Karix

This guide explains how to connect your **Karix WhatsApp account** with **Sortment** to send WhatsApp campaigns and track message delivery statuses.

***

### Prerequisites

Before starting the integration, ensure the following are already set up in your **Karix** account:

* An **active WhatsApp business number**
* **WhatsApp templates** created and approved
* Access to **Karix API / Account Key**
* Access to **Karix Managebot** (for webhook configuration)

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **Karix** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, fill in the following details:

#### Custom Name

Provide a name to help you identify this Karix WhatsApp sender within Sortment\
&#xNAN;_(Example: “Karix – WhatsApp Prod”)_

***

#### API / Account Key

1. Log in to **Karix Power APIs**
2. Click **Create Keys**
3. Enter a **Key Name** and **Description**, then save
4. Click the **eye icon** to reveal the generated API key
5. Copy and paste the key into the **API / Account Key** field in Sortment

***

#### From WhatsApp Number

Enter the registered **WhatsApp business number** used to initiate conversations.

To find or add a number:

1. Log in to **Karix Managebot**
2. Navigate to **WhatsApp Campaign → Profiles**
3. If a number already exists, copy the **Mobile Number**
4. Or click **Add WhatsApp Number** to add a new one

Enter this number in Sortment **without the “+” symbol**.

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once validation succeeds, the integration will be activated

Your Karix WhatsApp sender is now ready to be used in Sortment campaigns 🎉

***

### Message Delivery Status Configuration (Required)

Karix requires a **manual webhook configuration** to send message delivery updates to Sortment.

#### Steps to Enable Delivery Status Tracking

1. Log in to **Karix Managebot**
2. Navigate to **WhatsApp Campaign → Webhook\_Config**
3. Under the **Delivery Rule** tab, click **Create New**
4. In the **URL** field:
   * Paste the **Callback URL** shown in the Karix integration pop-up in Sortment
5. Add the following header:
   * **Key:** `Content-Type`
   * **Value:** `application/json`
6. Select **all required delivery events** for tracking
7. Save the configuration
