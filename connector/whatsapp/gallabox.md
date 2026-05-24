# Gallabox

This guide explains how to connect your **Gallabox WhatsApp account** with **Sortment** to send WhatsApp campaigns and track message delivery statuses.

***

### Prerequisites

Before starting the integration, ensure the following are already set up in your **Gallabox** account:

* An **active WhatsApp business number**
* **WhatsApp templates** created and approved
* Access to your **Gallabox Access Token**

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **Gallabox** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, fill in the following details:

#### Custom Name

Provide a name to help you easily identify this Gallabox WhatsApp sender within Sortment\
&#xNAN;_(Example: “Gallabox – WhatsApp Prod”)_

***

#### Access Token

1. Log in to your **Gallabox** account
2. From the left navigation panel, go to **Integrations → Configuration**
3. Copy the **Access Token**
4. Paste the token into the **Access Token** field in Sortment

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once the test is successful, the integration will be activated

Your Gallabox WhatsApp sender is now ready to be used in Sortment campaigns 🎉

***

### Message Delivery Status Configuration (Important)

Gallabox requires a **manual webhook configuration** to send message delivery statuses to Sortment.

#### Steps to Enable Delivery Status Tracking

1. Log in to your **Gallabox** account
2. Navigate to **Integrations** from the left navigation panel
3. Open the **Configuration** tab
4. In the **Status URL** field:
   * Paste the **Callback URL** shown in the Gallabox integration pop-up in Sortment
5. Save the configuration

Once this is completed, Gallabox will start sending delivery status updates to Sortment.
