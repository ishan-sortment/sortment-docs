# Kaleyra

This guide explains how to connect your **Kaleyra WhatsApp account** with **Sortment** to send WhatsApp campaigns and track message delivery statuses.

***

### Prerequisites

Before starting the integration, ensure the following are already set up in your **Kaleyra** account:

* An **active WhatsApp business number**
* **WhatsApp templates** created and approved
* Access to **Kaleyra API credentials** (SID and API Key)

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **Kaleyra** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, fill in the following details:

#### Custom Name

Provide a name to help you identify this Kaleyra WhatsApp sender within Sortment\
&#xNAN;_(Example: “Kaleyra – WhatsApp Prod”)_

***

#### SID (Security Identifier)

1. Log in to your **Kaleyra** account
2. Navigate to **Developers → API Keys**
3. Open an existing API Key (click the **more / ellipsis** menu)
4. Click **View**
5. Copy the **SID** shown and paste it into the **SID** field in Sortment

***

#### API Key

1. In **Kaleyra → Developers → API Keys**
2. Copy an existing API Key **or** create a new one
3. Paste the key into the **API Key** field in Sortment

***

#### From Number

Enter the registered **WhatsApp business number** used to initiate conversations.

To find the number in Kaleyra:

1. Go to **Channels**
2. Select the **WhatsApp** channel
3. Click **Manage**
4. Open **Configurations** from the top ribbon
5. Copy the configured WhatsApp number

Enter this number in Sortment **without the “+” symbol**.

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once validation succeeds, the integration will be activated

Your Kaleyra WhatsApp sender is now ready to be used in Sortment campaigns 🎉

***

### Message Delivery Status Configuration (Required)

Kaleyra requires a **manual callback configuration** to send message delivery updates to Sortment.

#### Steps to Enable Delivery Status Tracking

1. Log in to your **Kaleyra** account
2. From the top-right corner, click **Settings**
3. On the top ribbon menu, click **Settings** again
4. Locate **Enable WhatsApp Callback URLs**
5. Paste the **Callback URL** shown in the Kaleyra integration pop-up in Sortment
6. Save the configuration
