# Meta

Sortment supports **multiple Meta WhatsApp account types**, but **we do not sell or provision Meta accounts**.

This page exists to help you:

* Understand the **differences between Meta account types**
* Identify **which Meta WhatsApp setup you already have**
* Know **which integration applies to your setup in Sortment**

***

### The Three Meta WhatsApp Account Types We Support

Meta WhatsApp accounts generally fall into **one of three categories**:

1. **Meta (By Facebook)**
2. **Meta Direct**
3. **Meta Direct Plus**

All three use Meta’s official WhatsApp infrastructure, but differ in **billing**, **usage**, and **coexistence with the WhatsApp Business App**.

***

## How to Identify Your Meta WhatsApp Account Type

Meta does **not clearly label** WhatsApp accounts as _Meta Direct_, _Meta Direct Plus_, or _Meta (by Facebook)_ in their UI.

Instead, your account type is determined by **how it was onboarded**, **who manages billing**, and **how much setup you control**.

This guide helps you identify **which Meta WhatsApp account you already have**.

***

### First: What You Will _Not_ See

You will **not** see labels like:

* “Meta Direct”
* “Meta Direct Plus”
* “Meta Cloud API”

These are **integration-level distinctions**, not names shown inside Meta dashboards.

***

### Step 1: Did you ever create or manage a Meta App?

**Ask yourself:**

> “Did I (or my tech team) create a Meta App and manage tokens, webhooks, and IDs manually?”

#### If YES → **Meta (by Facebook)**

You likely:

* Created a Meta App in **developers.facebook.com**
* Generated **System User access tokens**
* Configured **Webhooks manually**
* Used:
  * Phone Number ID
  * WABA ID
  * Access Tokens

✅ **Account Type: Meta (by Facebook)**

***

#### If NO → Move to Step 2

***

### Step 2: Who bills you for WhatsApp usage?

This is the **strongest indicator**.

#### Billing check

| What you see                                                | What it means    |
| ----------------------------------------------------------- | ---------------- |
| Charges appear **directly from Meta** (Facebook / WhatsApp) | Meta Direct      |
| You receive invoices from a **partner / provider**          | Meta Direct Plus |

***

#### If Meta bills you directly → **Meta Direct**

You likely:

* Added a **credit card** in Meta Business Manager
* Completed **embedded signup**
* Never touched app tokens or webhooks
* Manage templates natively via Meta

✅ **Account Type: Meta Direct**

***

#### If a provider bills you → **Meta Direct Plus**

You likely:

* Could not add an international credit card
* Used a **credit line / partner billing**
* Still onboarded via Meta embedded signup
* Didn’t manage technical details

✅ **Account Type: Meta Direct Plus**

***

### Step 3: Did Sortment ask you to “Login with Facebook”?

| Experience                            | Account type       |
| ------------------------------------- | ------------------ |
| Yes, onboarding was mostly UI-driven  | Meta Direct / Plus |
| No, only IDs and tokens were required | Meta (by Facebook) |

***

### Step 4: Do you manage webhooks yourself?

| Webhook setup                                          | Account type       |
| ------------------------------------------------------ | ------------------ |
| You manually configured Webhooks in Meta App Dashboard | Meta (by Facebook) |
| You never touched webhooks                             | Meta Direct / Plus |

***

### Final Identification Table

| Signal                                  | Meta (by Facebook) | Meta Direct | Meta Direct Plus |
| --------------------------------------- | ------------------ | ----------- | ---------------- |
| Created Meta App manually               | ✅                  | ❌           | ❌                |
| Uses Phone Number ID & tokens           | ✅                  | ❌           | ❌                |
| Embedded signup (“Login with Facebook”) | ❌                  | ✅           | ✅                |
| Billing via Meta                        | Depends            | ✅           | ❌                |
| Billing via provider                    | ❌                  | ❌           | ✅                |
| Manual webhook setup                    | ✅                  | ❌           | ❌                |
| Tech-heavy setup                        | ✅                  | ❌           | ❌                |

***

### Still Not Sure?

If you’re unsure after these checks, ask yourself:

1. **Who sends me invoices for WhatsApp?**
2. **Did I ever open Meta App Dashboard?**
3. **Did I ever generate tokens or webhooks manually?**

Answering just these three usually gives you the answer.

***

### When to Reach Out for Help

If you cannot confidently identify your setup:

* Share **who bills you**
* Confirm **whether your number works in WhatsApp Business App**
* Sortment support can help map your setup to the right integration
