---
hidden: true
---

# Setting Up Events Table

Event definition is a one-time step. You can complete event setup by following these steps:

1. Event table must be created in relation to an existing table. Click the + button on any existing table and Select events.

![](https://files.readme.io/d71a538-image.png)

2. Sortment prompts you to select a table in your data warehouse.

![](https://files.readme.io/52b8ff0-image.png)

3. Enter a name for your event table. Use something that helps you identify it easily later
4. Optionally, enter a description.
5. Choose the Primary Key column in your events table.
6. Click Next.

![](https://files.readme.io/83bb3f6-image.png)

7. Choose how your events are stored in the table. If there are multiple events in the same table, choose the field with column names and label your events. This will help in making events data readable when querying on it for Audiences.

![](https://files.readme.io/6895e3f-image.png)

8. Label the fields in your events table. These can be used to filter on events data in Audiences.![](https://files.readme.io/d5c401e-image.png)9. Define the events relationship. Select the relationship's cardinality: 1:1, 1:many, or many:1. In most cases, primary tables have a 1:many relationship with events.10. Click Save to add the table to your schema.

![](https://files.readme.io/6d86d2b-image.png)

![](https://files.readme.io/907d76e-image.png)

The schema overview page shows the schema from the perspective of primary table; labels are displayed accordingly.
