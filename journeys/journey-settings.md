# Journey Settings

The journey settings panel is divided into the following key sections:

* Scheduling
* Entry limits
* Exit triggers
* Goals

Each section enables you to fine-tune how and when users interact with your journeys.

### **1. Scheduling** <a href="#undefined" id="undefined"></a>

**Purpose:** Define the active periods for your journey-when it starts and optionally when it ends.

**Configuration steps:**

* **Activate this journey at a specific date and time:**
  * Enable this option to schedule the journey’s start.
  * Set the desired start date and time using the calendar and clock controls.
  * The time zone is displayed (e.g., GMT+05:30).
* **Set end date and time (optional):**
  * Enable this checkbox if you want the journey to automatically end at a specified date and time.
  * Specify the end date and time as required.

### **2. Entry limits** <a href="#undefined" id="undefined"></a>

**Purpose:** Control how many times users can enter the journey.

**Configuration options:**

* **No limits:**
  * Users can enter the journey an unlimited number of times.
* **Sunset after a specific number of trips:**
  * Set a maximum number of entries (trips) per user.
  * Once the limit is reached, users will no longer be able to enter the journey.

### **3. Exit triggers** <a href="#undefined" id="undefined"></a>

**Purpose:** Set up criteria for users to exit the journey before completion.

**Configuration steps:**

* **Add exit rules:**
  * Click "Add Rule" to define exit conditions.
  * Select an event from the dropdown menu to specify what triggers a user's exit from the journey (e.g., a user action, inaction, or system event).
* **Multiple rules:**
  * You can add multiple exit rules, each based on different events.

### **4. Goals** <a href="#undefined" id="undefined"></a>

**Purpose:** Assign and track goals for your journey to measure user conversions.

**Configuration steps:**

* **Conversion event:**
  * Select the event that represents a successful conversion for this journey (e.g., purchase completed, signup).
* **Goal deadline:**
  * Define the maximum time (in days) allowed between a user entering the journey and achieving the goal.

### **Summary table** <a href="#undefined" id="undefined"></a>

| Setting       | Description                                        | Options/Inputs                         |
| ------------- | -------------------------------------------------- | -------------------------------------- |
| Scheduling    | Set start/end date and time for journey activation | Date, Time, Time Zone                  |
| Entry Limits  | Restrict number of journey entries per user        | No limits, Sunset after N trips        |
| Exit Triggers | Define conditions for early journey exit           | Add rules based on events              |
| Goals         | Track conversions and set deadlines                | Conversion event, Goal deadline (days) |
