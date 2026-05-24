# Gupshup Enterprise

This guide explains how to connect your **Gupshup Enterprise WhatsApp account** with **Sortment** to send WhatsApp campaigns and receive message delivery statuses.

***

### Prerequisites

Before starting the integration, ensure the following are already set up in your **Gupshup Enterprise** account:

* An **active WhatsApp business number**
* **WhatsApp templates** created and approved
* Login credentials for your **Gupshup Enterprise account**
* Access to **Gupshup Analytics** (for webhook configuration)

***

### Step 1: Find the Provider

1. Log in to your **Sortment** dashboard
2. Navigate to:\
   **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click on **Add Integration**
5. Select **Gupshup Enterprise** as the provider

***

### Step 2: Configure the Integration

In the integration pop-up, enter the following details:

#### Custom Name

Provide a name that helps you identify this Gupshup Enterprise sender within Sortment\
&#xNAN;_(Example: “Gupshup Enterprise – WhatsApp Prod”)_

#### Username

Enter the **username** used to log in to your Gupshup Enterprise account

#### Password

Enter the **password** corresponding to the same Gupshup Enterprise account

***

### Step 3: Complete the Integration

* Click **Test and Save**
* Once authentication is successful, the integration will be activated

Your Gupshup Enterprise WhatsApp sender is now ready to be used in Sortment campaigns 🎉

***

### WhatsApp Template Handling (Important)

Gupshup Enterprise requires the **message body to be explicitly provided**, even for **template-based messages**.

#### What this means in Sortment

* While using Gupshup Enterprise as a sender, you must:
  * Select the approved WhatsApp template
  * **Also provide the message body/content** when configuring the campaign
* This is a **Gupshup Enterprise–specific requirement** and is expected behavior

***

### Message Delivery Status Configuration (Required)

Gupshup Enterprise requires a **manual webhook setup** to send message delivery updates to Sortment.

#### Steps to Enable Delivery Status Tracking

1. Log in to your **Gupshup Analytics** account
2. From the left navigation panel, click **Integrations**
3. In the left panel, select **Webhooks**
4. Click on **WhatsApp Message Delivery Events**
5. Scroll to the bottom of the page and:
   * Paste the **Notification Callback URL** shown in the Gupshup Enterprise integration pop-up in Sortment
   * Set **Forward Method** to **JSONBODY**
6. Click **Submit**
