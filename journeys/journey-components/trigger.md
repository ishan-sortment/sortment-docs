# Trigger

Every journey in sortment starts with a **trigger**—this is the condition that determines when a user enters the journey. Without a trigger, the journey doesn’t run. Think of it as the starting gate that opens when certain criteria are met.

<figure><img src="../../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

As shown in the image above, when creating a new journey, you’re first prompted to **set a trigger** using the sidebar on the right. You can pick from various trigger types depending on the goal of your journey.

## Available trigger types

### 1. User action

Use this trigger when you want to start a journey based on specific user behaviour or activity.

#### Step 1: Selecting an event

Use this trigger when you want to start a journey based on specific user behavior or activity.

#### **How it works:**

1. Click **Add a trigger** and select **User action**.
2. Choose from a list of events that have been setup on Sortment. For example, `Ride Completed`,  `User Sign Up`, etc.
3. Optionally, you can filter users based on properties. For example:\
   “Start this journey only if the **number of rides with low rating** is less than 3.”
4. Decide if you want users to re-enter this journey by enabling the **Re-entry** option.

This trigger is ideal for behaviour-based automations — like sending a message after a ride is completed, or triggering a follow-up if a user has had a negative experience.



### Business event

Use this trigger to start a journey based on business events like `Sale announcement`. This allows you to trigger a journey for a common set of people based on some action that happens somewhere else.

#### **How it works:**

1. Select **Business event** as the trigger type.
2. Pick an event from the list — such as `Sale Announcement`, `Referral Events`, or any other event added to Sortment.
3. Apply filters to determine which users should be enrolled for this journey.
4. Enable **Re-entry** if you want users to go through this flow more than once.

This is especially useful for campaign-like journeys or recurring flows based on transactional or funnel-related events.



### Scheduled

Use this trigger to start journeys on a recurring schedule — perfect for batch campaigns or regular touch-points.

**Example use case:** Push a reminder Email every friday for weekend-only offers.

#### **Setup steps:**

* Select **Scheduled** as the trigger.
* Choose a recurring schedule: Daily, Weekly, or Monthly.
* Specify the day and time (e.g., 5th of every week at 8:00 PM).
* Apply filters to determine which users should be enrolled.
* Enable **Re-entry** if this journey should recur for the same users over time.



### Audience entry or exit

Trigger a journey when users enter or exit a dynamic audience segment.

**Example use case:** Send a message when a user qualifies for a loyalty tier or drops out of an active user segment.

#### **Setup steps:**

* Click add a trigger and select Audience entry or exit.
* Choose whether to start a journey when users **Enter audience** or **Exit audience**.
* Define the audience using filters (e.g., users with a specific property).
* Set a **refresh frequency** (e.g., monthly at 12:00 AM) to re-evaluate audience eligibility.
* Enable **Re-entry** if users should re-enter the journey when they re-qualify.



### Other journey

Trigger a journey from another journey using the **Add to journey** block.

**Use case:** Create modular journeys and move users across flows.

#### **Setup:**

* In a separate journey, use the **Add to journey** block to send users here.
* This journey will receive those users.
* Apply filter for incoming users if required.
* Enable **Re-entry** to allow users to revisit this journey if re-sent from another.

