# Meta Direct Plus

This guide explains how to set up **Meta Direct Plus** with **Sortment**.

***

### Prerequisites

Before starting, ensure you have:

* Access to **Meta Business Manager**
* An existing or new **WhatsApp Business** account
* Ability to temporarily **disable 2FA** (only if reusing an existing WhatsApp number)
* A **Solution ID** (provided by the Sortment team)

***

### Signup Scenarios

You will fall into **one of the following scenarios**:

1. You already have a WhatsApp Business account with a BSP and want to migrate
2. You want to add WhatsApp to an existing Meta Business account
3. You’re starting from scratch (no Meta Business account, no WhatsApp account)

The embedded signup flow adapts automatically based on your scenario.

***

### Scenario 1: Existing WhatsApp Business Account with a BSP

You already have:

* A verified Meta Business account
* WhatsApp connected via another BSP

You can:

* **Migrate the same WhatsApp number** to Meta Direct Plus
* **Add a new WhatsApp number** under the same Meta Business account

> ⚠️ If reusing the same number, temporarily **disable 2FA** on that WhatsApp number.

***

### How to Set Up Meta Direct Plus in Sortment

#### Step-by-Step Integration

1. Log in to **Sortment**
2. Navigate to **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click **Add Integration**
5. Select **Meta Direct Plus**

***

#### Embedded Signup Flow

6. Enter a **Custom Name**\
   &#xNAN;_(Example: Meta-Direct-Plus-WhatsApp)_
7. Enter the **Solution ID**\
   &#xNAN;_(Contact the Sortment team to obtain this)_
8. Click **Login with Facebook**
9. Complete the Meta embedded signup:
   * Select or create a Meta Business account
   * Create or select a WhatsApp Business account
   * Add and verify phone number (OTP)
   * Complete business profile details
10. Wait for Meta verification (usually under 2 minutes)
11. Return to Sortment and click **Test and Save**

🎉 Your Meta Direct Plus WhatsApp sender is now active.

***

### Enabling MM Lite API (Optional)

**Marketing Messages Lite API (MM Lite API)** improves delivery and analytics for marketing messages.

Enable it if:

* You have a **Meta Ads account**
* You plan to send **marketing messages**

#### Key Benefits

* Higher or comparable delivery vs Cloud API
* Engagement-based dynamic messaging limits
* Template benchmarks & performance insights
* Conversion reporting
* Time-bound (TTL) promotional messages

🔗 Learn more: [https://developers.facebook.com/docs/whatsapp/marketing-messages-lite-api/](https://developers.facebook.com/docs/whatsapp/marketing-messages-lite-api/)

***

### Creating & Syncing WhatsApp Templates

#### Sync Existing Templates

* Go to **Templates → External**
* Click the **Sync** icon
* All Meta templates will be imported into Sortment

#### Create New Templates

* Click **+ Create**
* Submit for approval
* Approvals typically take a few minutes

> ⚠️ Templates can only be tested after **billing is enabled** via the service provider.

***

### Billing with Meta Direct Plus

* Billing is handled via **Sortment’s approved service provider**
* You receive **monthly invoices**
* No international credit card required
* Messaging and templates still operate on Meta’s Cloud API

***

### Scenario 2: Adding WhatsApp to an Existing Meta Business Account

If you already have a Meta Business account but no WhatsApp number:

* Follow the same steps as **Scenario 1**
* The embedded signup flow will guide you automatically

***

### Scenario 3: Starting from Scratch

If you don’t have a Meta Business account or WhatsApp account:

#### You’ll need:

* **GST Registration** (or incorporation proof for exemptions)
* **Company website** showing legal entity name
* **WhatsApp number** (not active on personal WhatsApp)
* No international credit card required (billing via provider)

> ⏱️ Meta verification may take **up to 48 hours**

Once verified, continue onboarding via **Meta Direct Plus** in Sortment.

***

### Important Things to Remember

1. New WhatsApp accounts start at **1,000 messages/day**
2. Good engagement unlocks **10k → 100k** tiers
3. Poor quality (blocks/spam reports) can:
   * Freeze tier upgrades
   * Disable templates
   * Risk account suspension
4. Meta Direct Plus removes **payment friction**, not quality enforcement
