# Meta (By Facebook)

This guide explains how to connect an existing **Meta WhatsApp Cloud API setup** with **Sortment** using credentials from **Meta Business Manager and App Dashboard**.

This integration is typically used when:

* You already have a **Meta App** set up for WhatsApp
* You manage **tokens, webhooks, and phone numbers manually**
* You want deeper control over incoming messages and callbacks

***

### Prerequisites (Required from Meta)

Before configuring the integration in Sortment, ensure the following are completed in **Meta Business Manager**:

#### 1. Business & Access Setup

* You are added to the Meta Business as **Employee Access**
  * Business Admin can add you from **Business Settings → People**
* You have access to the **Meta App** used for WhatsApp
  * Granted via **People → Add Asset → Apps**
  * Permission: **Manage apps**

***

#### 2. Generate an Access Token

1. Go to **Business Settings → System Users**
2. Click **Generate New Token**
3. Select the App used for WhatsApp
4. Grant permissions:
   * **WhatsApp Business Messaging**
   * **WhatsApp Business Management**
5. Generate and save the token\
   → This will be used as the **Access Token** in Sortment

***

#### 3. Get Phone Number ID

1. Open **Meta App Dashboard**
2. Go to **WhatsApp → Getting Started**
3. Under **Send and Receive Messages**, select the WhatsApp number
4. Copy the **Phone Number ID**

***

#### 4. Get WhatsApp Business Account ID (WABA ID)

* Go to **Business Settings → Accounts → WhatsApp Accounts**
* Select the WhatsApp account
* Copy the **WABA ID** shown on the top-right

***

### Configure Meta (by Facebook) in Sortment

Once the prerequisites are ready, continue in **Sortment**.

***

#### Step 1: Find the Provider

1. Log in to **Sortment**
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click **Add Integration**
5. Select **Meta (by Facebook)**

***

#### Step 2: Configure the Integration

In the integration pop-up, enter:

* **Custom Name**\
  A name to identify this sender\
  &#xNAN;_(Example: Meta Cloud API – Prod)_
* **Phone Number ID**\
  From Meta App Dashboard (WhatsApp → Getting Started)
* **Access Token**\
  Generated from **System Users** in Business Manager
* **WhatsApp Business Account ID (WABA ID)**\
  From Business Settings → WhatsApp Accounts

***

#### Step 3: Complete the Integration

* Click **Test and Save**
* Once validated, the Meta WhatsApp sender will be active

***

### Enabling Incoming Messages (Optional)

If you want to **receive inbound WhatsApp messages** in Sortment:

1. Enter the WhatsApp number (with country code) in the integration
2. Click **Update Account**
3. Click **Enable Incoming Messages**
4. Verify by:
   * Sending the displayed message **or**
   * Scanning the QR code
5. Confirm from the WhatsApp message received
6. Once enabled, incoming messages will start appearing in Sortment

***

### Message Delivery Status (Webhook Setup Required)

Meta requires a **manual webhook configuration** for delivery events.

***

#### Steps to Configure Webhooks

1. Log in to **Meta App Dashboard**
2. Open your App
3. Scroll to **Webhooks** → Click **Set Up**
4. Select **User** as the object
5. Subscribe to:
   * `messages`
   * `message_template_status_update`
   * `message_template_quality_update`
6. Choose API version **v18.0**
7. Enter:
   * **Callback URL** → from Sortment integration popup
   * **Verify Token** → any string (store it safely)
8. Complete webhook verification

***
