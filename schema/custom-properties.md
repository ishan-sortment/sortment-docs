---
hidden: true
---

# Custom Properties

Custom Properties perform aggregation calculations on your data. These can be attached to users, events, or other data that allows marketers to create more tailored messages and experiences.&#x20;

This stores the logic for a new property for a user which does not directly exist in the data warehouse, and is added to queries for segmentation or campaign data.

From the e-commerce example, one may want to get most expensive item ordered in an order. If the value is not directly available in any table in the schema, one can create a custom property **Most expensive item** on **Orders** table, which is **Max of Line Item Price.**

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

### Required Skillset

Building custom properties requires an understanding of your business goals. Usually, business stakeholders like marketers complete this step.

### Creating a custom property

1. Click **+ New Property** on Custom Property page.
2.  Choose the table you want to create custom property against. This is the entity against which aggregation will be created. In the e-commerce example, this will be Orders table.\
    Here, tables at the leaf node in the schema won't be available.<br>

    <figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>
3. Setup a name and description to identify this custom property.
4.  Choose the property from the column list you want to create an aggregation on. In the example above, this will be Product Price, from Line Items table.<br>

    <figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>
5. Choose the aggregation function. The list may be different based on the datatype. The aggregation useful for the e-commerce example is maximum, to get most expensive item.
6.  You can add filters here, to filter specific entries which should be accounted during the aggregation. In this example, most expensive item is being filtered among product "Ice Cream" and "Ice Cubes" only.

    <figure><img src="../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>
7. Once done, create the custom property. You can now use this in audience creation as a filter. This will be displayed as a separate section in the filter dropdown.

#### Aggregate functions

Aggregate functions depend on the datatype of field selected while creating custom property. Here's an exhaustive list:

* Number
  * Sum
  * Percentile
  * Median
  * Average
  * Count
  * Count Distinct
  * Min
  * Max
* Other data types (String, Boolean, Datetime)
  * Count
  * Count Distinct
  * Min
  * Max

