# Related and Events Table

In the uber example, a related table could be an ride Details table with columns for:

* `Fare`: Total fare for the ride
* `Driver_id`: Unique id for the driver
* `phone_number`: Customer phone number for the order for communication purposes
* `Pickup_location`: Pickup location for the ride
* `Dropoff_location`: Drop-off location for the ride
* `customer_name`: Customer name
* `placed_on`: Ride assigned timestamp

For these events, an events model might include columns for:

* `id`: Unique event id
* `timestamp`: Timestamp for occurrence of the event
* `event_name`: Event name
* `user_id`: User id for the customer who did the event. This is the column the events table gets joined on with users table

An events table might include your app events:

* `account_created`
* `account_updated`
* `ride_requested`
* `payment_success`

## Relationships

When you create related or event tables, you simultaneously set up their relationships.

In the uber example, let's say you want to create an audience of customers who booked a ride or who did a particular event action on your app. You need to define a relationship between your primary table (users) and your related table (orders) and events table (events).

Under the hood, Sortment generates SQL `JOINs` between your tables. To make this possible, you must create relationships by selecting the foreign keys between your tables.

![](<../.gitbook/assets/a1 (3).png>)

## Directionality

Relationships are directional. That means you can create and view relationships starting from a parent to a child table.

For example, 1:many relationship can be created from users to events

![](../.gitbook/assets/a4.png)

The schema overview page shows the schema from the perspective of primary table; labels are displayed accordingly.
