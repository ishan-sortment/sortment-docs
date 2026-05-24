# MessageBird

This guide explains how to connect your **MessageBird WhatsApp account** with **Sortment** to send WhatsApp campaigns and view message delivery statuses.

***

### Prerequisites

Before starting the integration, ensure the following are already set up in your **MessageBird** account:

* An **active WhatsApp business number**
* **WhatsApp templates** created and approved
* Access to **MessageBird API credentials**
* Access to **WhatsApp channel details** (Channel ID and Namespace)

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **MessageBird** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, fill in the following details:

#### Custom Name

Provide a name to help you identify this MessageBird WhatsApp sender within Sortment\
&#xNAN;_(Example: “MessageBird – WhatsApp Prod”)_

***

#### API Key

1. Log in to your **MessageBird** account
2. Navigate to **Developers → API Access**
3. Create a new API key **or** copy an existing one
4. Paste the API Key into the **API Key** field in Sortment

***

#### From (Channel ID)

1. In MessageBird, go to **Channels**
2. Select **WhatsApp**
3. Choose the WhatsApp number you want to use
4. Copy the **Channel ID**
5. Paste it into the **From** field in Sortment

***

#### Namespace

1. From **Channels → WhatsApp** in MessageBird
2. Select the same WhatsApp number
3. Copy the **Template WhatsApp Namespace ID**
4. Paste it into the **Namespace** field in Sortment

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once validation succeeds, the integration will be activated

Your MessageBird WhatsApp sender is now ready to be used in Sortment campaigns 🎉
