# Tutorial: Creating a journey

This guide shows you how to build an effective nurture journey in **Sortment** to turn free trial users into paying customers within their first 7 days. We’ll walk through how to use blocks like triggers, emails, delays, and filters to create a smart, branching flow that adapts to user behaviour.

***

### **Overview: what you’ll build**

A dynamic journey that:

* Welcomes new trial users
* Encourages product engagement with targeted nudges
* Reacts differently based on user activity (like email clicks)
* Promotes upgrading with incentives
* Ends with either a thank-you message or an off-ramp for non-converters

***

## **Journey walkthrough**

Here is the journey we’ll follow, guiding users from starting a free trial through engagement and potential conversion — followed by a visual representation.

```
Trigger: User starts free trial
→ Email: Welcome
→ Delay: 1 day
→ Email: Top 3 Things to Try
→ Filter: Clicked Email?
    → Yes:
        → Update Trait: Engaged
        → Email: Promo offer
        → Filter: Payment made?
            → Yes: Welcome to Premium → Update Trait: Paid
            → No: Exit journey
    → No:
        → Delay: 2 days
        → Email: Need Help?
        → "Reactivation Journey" after 7 days
```

### **Starting the journey: Detect free trial users**

Begin in the **Journeys** section of sortment. Create a new journey and name it something descriptive, like **“Free trial to paid – conversion flow.”**

Add a **Trigger block** and set the type to **User action**, choosing the **Backend event → Started free trial**.\
This ensures any new user who initiates a trial enters the journey immediately.

_Optional:_ Add filters or set re-entry rules (e.g., re-enter after 7 days) to fine-tune when users qualify.

<figure><img src="../.gitbook/assets/image (130).png" alt=""><figcaption></figcaption></figure>

***

### **Step into the journey: Send a warm welcome mail**

Add a **Send Email block** linked to your trigger.\
Choose the template **“Welcome to your free trial.”**

This email sets the tone—thank the user, explain what to expect, and offer links to resources that help them get started.

Edit the subject, sender, and preview content to match your brand voice.

<figure><img src="../.gitbook/assets/a11 (1).png" alt=""><figcaption></figcaption></figure>

***

### **Give them room to explore: Add a delay**

Next, insert a **Delay block** for **1 day**.\
This creates space for users to try the product on their own before further engagement.

<figure><img src="../.gitbook/assets/a12 (1).png" alt=""><figcaption></figcaption></figure>

***

### **Re-engage with value: Highlight key features**

Follow up with another **Send Email block** using the **“Top 3 things to try today”** template.\
This message gives users a sense of momentum—focus on practical, valuable actions they can take now.

Customise subject lines and email content to reflect your top features or user goals.

<figure><img src="../.gitbook/assets/a13 (2).png" alt=""><figcaption></figcaption></figure>

***

### **Branch based on behaviour: Did they engage?**

Insert a **Filter block** using the **Email link clicked** condition and select “Top 3 things to try today.”\
This splits your journey into two paths: those who engaged (clicked) and those who didn’t.

<figure><img src="../.gitbook/assets/image (132).png" alt=""><figcaption></figcaption></figure>

***

### **For Engaged Users (“Yes” Branch)**

1. **Mark as engaged:**\
   Use an **Update trait block** to flag the user as an **Engaged trial user** by updating their trait to “Engaged Trial.”

<figure><img src="../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

2. **Make the offer:**\
   Add a **Send email block** with the template **“Upgrade now & save 20%.”**\
   Offer a time-sensitive incentive to encourage conversion.

<figure><img src="../.gitbook/assets/image (134).png" alt=""><figcaption></figcaption></figure>

3. **Track redemptions:**\
   Insert a **Filter block** to detect if a user redeemed the promo or made a payment.

<figure><img src="../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

4. **Celebrate success:**\
   If converted, send a **Welcome to premium** email and use another **Update trait block** to set them as a **Paid user**.

***

#### **For Non-Engaged Users (“No” Branch)**

1. **Wait a bit longer:**\
   Add a **2-day Delay block** to allow time for re-engagement. considering only limited time remains in the trial.

<figure><img src="../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>

2. **Send a reminder Email:**\
   Use the **“Need help getting started?”** template to offer assistance and reignite interest.
3. **Shift to reactivation:**\
   Instead of continuing within this journey, use the **Add to journey** block to move the user into a **Reactivation journey**, where you can target them with longer-term, personalised follow-ups.

<figure><img src="../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

***

### **Visual flow summary**

* **Trigger:** User starts free trial
* **Email:** Welcome message
* **Delay:** 1 day
* **Email:** Product engagement tips
* **Filter:** Clicked email → Branch
  * **Yes →** Mark Engaged → Send Promo → Check Payment → Thank You
  * **No →** Wait 2 Days → Reminder Email → "Reactivation Journey" after 7 days
