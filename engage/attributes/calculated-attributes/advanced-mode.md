# Advanced Mode

**Sortment’s Advanced Mode** empowers data-savvy users to define custom attributes using either a **visual expression builder** or **SQL logic**, depending on the attribute type. This functionality allows you to create powerful, structured metrics and dimensions that go beyond natural language-based AI prompts.

> 💡 **Tip:** For most users, AI-based attribute creation is sufficient. Use Advanced Mode when you wish to define attributes manually.

## Creating a calculated attribute using advanced mode

Sortment provides an **Advanced option** to create calculated attributes

### Open the attributes section:

1. Click the **star-shaped icon** (`✶`) in the left or top navigation bar.
2. This opens the **Attribute** page, where you can view, manage, and create new attributes.

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### Step 1: Click “New Attribute”

Start by clicking the **“+ New Attribute”** button at the top right of the Attribute page. Choose calculated attributes.

### Step 2: Choose attribute type

Select "Advanced Mode" as the creation method

### Step 3: Define attribute settings

* Attribute type: Select [dimension](../use-cases.md#dimension-based-traits) or [metric](../use-cases.md#metric-based-traits).
* Data source: Choose the relevant table (Eg., `Users`, `Accounts`)

### Step 4: Attribute details:

You'll be presented with the new calculated attribute screen, enter:

1. Attribute Name : Enter descriptive name of the attribute (e.g., `Max Premium Ridefare`)
2. Description _(Optional):_ Provide additional context or purpose of the attribute. (e.g., `Highest fare a user has paid in a ride`)
3. Tags _(Optional):_ Add relevant tags to categorise or identify the attribute.

### Step 5: Define attribute logic

#### Metric attributes (Visual builder - No code) Use the dropdown-based builder to define logic without SQL:

1. Property : Select the property from the dropdown (e.g, `Ridefare`)
2. Function : Choose the aggregate function (e.g., `Max` ).
3. Filter _(Optional):_ Add filters to restrict the data in the calculation (e.g., `Ride Type = Premium`)

#### Dimension attributes  (SQL Editor) Use SQL logic to create more advanced or real-time attributes.

> Example syntax for a dimension attribute:

```
CASE
    WHEN spend > 1000 THEN 'High Value'
    WHEN spend BETWEEN 500 AND 1000 THEN 'Medium Value'
    ELSE 'Low Value'
END AS account_segment
```

### Step 6: Finishing the attribute

1. Use the preview results button to verify the output.
2. Click finish to save the attribute.

