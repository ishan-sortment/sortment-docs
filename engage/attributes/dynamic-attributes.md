# Dynamic Attributes

**Dynamic** attributes are real-time, event-driven user properties. Unlike calculated attributes that are synced during scheduled data warehouse updates, dynamic attributes are continuously updated in real time via journeys —directly responding to user behaviour as it happens.

***

### Dynamic attributes usage

Dynamic attributes are ideal for reactive, live segmentation needs. They are **used entirely within journeys**.

These attributes help personalise communication based on immediate user actions. For example:

* A user books a ride → instantly mark a “Booked Ride” dynamic attribute.
* A user bought a subscription plan → mark the "Pricing Plan"  attribute from the event.

***

### How to create a dynamic attribute?

1. **Go to** Attributes via the ✶ star icon
2. Switch to the **“Dynamic” tab**
3. Click **“New attribute”**
4. Fill in the fields as shown in the UI:
   * **Attribute Name**
   * **Description** _(optional)_
   * **Data Type** (Boolean, Text, Number, Date, etc.)
   * **Initialisation** _(optional)_: Choose a property from warehouse to set base values against each user
5. Click **Create attribute**
