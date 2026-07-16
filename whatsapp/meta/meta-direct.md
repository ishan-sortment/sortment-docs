# Meta Direct

This guide explains how to set up **Meta Direct WhatsApp** with **Sortment**, allowing you to onboard quickly, manage templates seamlessly.

***

### Prerequisites

Before starting, ensure:

* Access to **Meta Business Manager**
* An active or new **WhatsApp Business** account
* Ability to temporarily disable **2FA** (only if reusing an existing number)
* An **international credit card** (or use Meta Direct Plus)

***

### Signup Scenarios

The Meta Direct signup flow differs based on your current setup. You’ll fall into **one of these three scenarios**.

***

### Scenario 1: Existing WhatsApp Business Account with a BSP

You already have:

* A verified Meta Business account
* WhatsApp connected via another BSP

#### Possible paths

1. **Migrate the same WhatsApp number** to Meta Direct via Sortment
2. **Add a new WhatsApp number** under the same Meta Business account (e.g., marketing vs support)

> ⚠️ Disable 2FA on the WhatsApp number if reusing the same number.

***

### Scenario 2: Add WhatsApp to an Existing Meta Business Account

If you already have a Meta Business account but no WhatsApp number attached:

* Log in to **Sortment**
* Go to **Settings → Sender Profiles → WhatsApp**
* Select **Meta Direct**
* Follow the embedded signup flow

The steps are almost identical to Scenario 1.

***

### Scenario 3: Starting from Scratch

If you have **no Facebook Business account and no WhatsApp Business account**, you’ll need to create both.

#### What you’ll need

* **GST Registration** (or incorporation certificate for exemptions)
* **Company website** showing legal entity name
* **WhatsApp phone number** (not already active, or personal WhatsApp must be deactivated)
* **Credit card with international transactions enabled**

> ⏱️ Meta verification may take **up to 48 hours**

Once verified, follow the steps in **Scenario 1** to complete WhatsApp onboarding.

***

### How to Set Up Meta Direct in Sortment

#### Step-by-Step Integration

1. Log in to **Sortment**
2. Navigate to **Settings → Sender Profiles**
3. Open the **WhatsApp** section
4. Click **Add Integration**
5. Select **Meta Direct**

***

#### Embedded Signup Flow

6. Enter a **Custom Name**\
   &#xNAN;_(Example: Meta-Direct-WhatsApp)_
7. Click **Login with Facebook**
8. Complete the Meta signup flow:
   * Select Business Account
   * Create or select WhatsApp Business Account
   * Add and verify phone number (OTP)
   * Complete business profile details
9. Wait for Meta verification (usually < 2 minutes)
10. Return to Sortment and click **Test and Save**

🎉 Your Meta Direct WhatsApp sender is now active.

***

### Enabling MM Lite API (Optional)

**Marketing Messages Lite API (MM Lite API)** improves delivery for high-engagement marketing campaigns.

Enable it if:

* You have a **Meta Ads account**
* You want enhanced marketing delivery & analytics

#### Key Benefits

* Higher delivery potential vs Cloud API
* Engagement-based message scaling
* Template performance benchmarks
* Conversion reporting
* Expiring messages (TTL-based campaigns)

🔗 Learn more: [https://developers.facebook.com/docs/whatsapp/marketing-messages-lite-api/](https://developers.facebook.com/docs/whatsapp/marketing-messages-lite-api/)

***

### Message Limits & Quality Guidelines

* New accounts start at **1,000 messages/day**
* Positive engagement unlocks **10k → 100k** tiers
* Low quality (blocks, spam reports) can:
  * Block tier upgrades
  * Pause templates
  * Lead to account suspension

Maintain good content and targeting hygiene.
