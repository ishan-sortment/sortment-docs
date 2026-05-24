# Overview

Let's work through an example of uber rides. You want to use Sortment to create Audiences to personalise your marketing campaigns based on your customers' activity on your website or app. Before you start creating these audiences, you need to define two essential datasets:

* The set of people who make up your audiences — in other words, your customers
* The characteristics you want to filter these people on. For example, active riders, preferred ride type, actions they've taken on your website or app, etc.

In Sortment, you define the first as the primary table and the second ones as related tables and events. Related tables and events are similar; they're characteristics to filter primary table off of. When you add a table related to your primary table, you define the relationship between them. These tables and the relationships between them are known as your schema.

Schema setup is a one-time configuration process. Once you've set up your schema, you can build your audiences with same set of related tables and events. The schema setup process requires a technical understanding of your data and its relationships. Data or analytics engineers are often involved.

By following along with the setup on this page, you'll learn how to create a schema like this:

![](<../.gitbook/assets/a1 (3).png>)

## Primary table

Primary table is the main dataset you want to build your audiences off. Once your data warehouse connection is set, you will choose your primary table.

In the uber example, the parent model would be the dataset of all customers. It could include the following columns:

* `user_id`: Unique identifier for your customer - this should be the primary key of the table and be used as foreign key for other related tables
* `full_name`: Full name for your customer
* `phone_ number`: Contact number for your customer.
* `email`: Email for the customer
* `created_at`: Timestamp when the customer was created
* `modified_at`: Timestamp when some parameter for the customer was modified

## Primary table setup

Parent model definition is a one-time step you can complete by following these steps:

1. Go to the Schema page.
2. Click Add primary table. You will see list of tables Sortment has access to from your data warehouse. Choose the primary table basis the definition above.

![](https://files.readme.io/70948bd-image.png)

3. Enter the name for your primary table, for example, "Users".
4. Optionally, enter a description.
5. Select a primary key. Make sure this key is unique and consistent across other tables you join it to.
6. Set fields labels and optionally their descriptions. This will help improve readability of your fields when building [Audiences](../engage/audiences/) and [Campaigns](../engage/campaigns/) later.
7. Click _"Looks good!"_ to create your primary table.

![](https://files.readme.io/ff790f5-image.png)



In the uber example, a related table could be an ride details table with columns for:

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

In the uber example, let's say you want to create an audience of customers who ordered a specific ride or who did a particular event action on your app. You need to define a relationship between your primary table (users) and your related table (orders) and events table (events).

Under the hood, Sortment generates SQL `JOINs` between your tables. To make this possible, you must create relationships by selecting the foreign keys between your tables.

![](https://files.readme.io/9f48a5a-image.png)

![](https://files.readme.io/e746904-image.png)

## Directionality

Relationships are directional. That means you can create and view relationships starting from a parent to a child table.

For example, 1:many relationship can be created from users to events

![](https://files.readme.io/907d76e-image.png)

The schema overview page shows the schema from the perspective of primary table; labels are displayed accordingly.

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>
