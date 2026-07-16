# AiSensy

This guide explains how to connect your **AiSensy WhatsApp account** with **Sortment** to send WhatsApp campaigns.

***

### Prerequisites

Before starting the integration, ensure the following are already set up in your **AiSensy** account:

* An **active WhatsApp business number**
* **WhatsApp templates** created and approved
* An **API Campaign** created in AiSensy using the desired template
* Access to your **AiSensy API Key**



> ⚠️ AiSensy requires campaigns to be created as **API Campaigns**.\
> Sortment can only trigger WhatsApp messages against these API Campaigns.

**IP Allowlisting (Required) -**&#x54;o allow Sortment to trigger WhatsApp messages via AiSensy, the following IPs must be **whitelisted in your AiSensy account**:

* `3.7.109.206`
* `15.206.24.102`

If these IPs are not allowlisted, message delivery requests from Sortment will fail.

> 📌 If you’re unsure where to add this, please contact **AiSensy support** or your **AiSensy account manager** to whitelist the above IPs.

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **AiSensy** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, fill in the following details:

#### Custom Name

Provide a name to help you identify this AiSensy WhatsApp sender within Sortment\
&#xNAN;_(Example: “AiSensy – WhatsApp Prod”)_

***

#### API Key

1. Log in to your **AiSensy** account
2. Navigate to **Manage** from the left navigation panel
3. Click on **API Key**
4. Copy the **API Key**
5. Paste it into the **API Key** field in Sortment

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once validation succeeds, the integration will be activated

Your AiSensy WhatsApp sender is now ready to be used in Sortment campaigns 🎉
