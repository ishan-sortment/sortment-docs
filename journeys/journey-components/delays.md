# Delays

Delay blocks help you control the timing of how and when users move through your journey. They are useful when pacing communication, reacting to user actions, or syncing journey steps with real-world events like product drops or reminders.

There are three types of delay blocks:

### 1. **Delay**

The **Delay** block holds a user in the journey for a fixed period of time before they proceed to the next step. This is useful for spreading out messages or ensuring a buffer between touch-points.

#### Configuration:

* **Time delay**: Choose a duration in minutes, hours, days, or weeks.

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

**Example:** Wait 2 days after a welcome email before sending the next onboarding message.

***

### 2. **Wait for action**

The **wait for action** block pauses a user's journey until they perform a specific event — such as opening an email, completing a purchase, or logging into the app. If the action doesn't happen within a set time limit, the user continues down an alternate "Timed Out" path.

#### Configuration:

* **Action to wait for**: Define the event that will release the user (e.g. `email_opened`, `purchase_made`).
* **Timeout after**: Set a time window to wait (in minutes, hours, days, or weeks).

<figure><img src="../../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

#### Output Paths:

* **Qualified**: User completed the required action.
* **Timed out**: User did not complete the action within the given time.

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

**Example:** Wait up to 3 days for a user to click a product link. If they don’t, follow up with a reminder email.

***

### 3. **Wait till date**

The **wait till date** block pauses the user until a specific date and time, which can be dynamic (based on event performed) or fixed (e.g. a launch date).

<figure><img src="../../.gitbook/assets/a8 (2).png" alt=""><figcaption></figcaption></figure>

#### Configuration:

* **Property**: Choose a date (e.g. from an event timestamp or user trait like `membership_renewal_date`).
* **Proceed from this block**:
  * **Immediately** – User proceeds as soon as the block is evaluated.
  * **Before** – Set a time duration before the chosen date (e.g. 1 day before).
  * **After** – Set a time duration after the chosen date.
  * **At specific time** – Wait until an exact time on the selected date.

**Example:** Wait 2 hours before a user's scheduled appointment date to send a reminder SMS.
