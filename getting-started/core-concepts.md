# Core Concepts

Sortment is warehouse-native engagement platform for companies with their source of truth in the data warehouse. Here's a rundown of some core concepts to help with high-level understanding of Sortment.

### Organization

An organization is created when you sign up in Sortment. Everyone in your company will be part of one organization, with different teams or geographies or use cases being operated through different workspaces. The user who creates an organization is an Organization Admin. All Org Admins have access to all workspaces created in Sortment.

### Workspace

A workspace is a unique instance to manage your own users, data, campaigns, and integrations, allowing for separation between different parts of a business while still being managed within a single Sortment instance.

### Data Warehouse

A Data Warehouse is a centralized repository where large volumes of structured data is stored, organized for advanced analytics and querying. The most frequently used data warehouses include Snowflake, Google BigQuery, Amazon Redshift. This is the source of truth for your customer data and will be connected to Sortment for creating audiences and accessing user variables for campaigns.&#x20;

### Cloud Bucket Storage

Cloud Bucket Storage is specific cloud storage associated with platforms like AWS S3 or Google Cloud Storage, where data is stored in containers called "buckets." These buckets can hold vast amounts of unstructured data, such as files, images, and videos, and provide features like scalability, security, and easy access via APIs. This is used to store campaign related data before sending to marketing platform and manage campaign events.

### Primary Table

Primary Table is the table that holds initial customer data with unique identifiers (User ID). This table will be used to create audiences on your data and uniquely identify users for your campaigns or journeys.

#### User ID

User ID is a unique identifier assigned to each customer, which tracks individual behavior across channels and campaigns. All other identifiers like device id, anonymous id get resolved into a known user id for marketing purposes.

### Schema

Schema defines the structure, organization, and relationships of data stored in the warehouse. It stores information about the tables, the type of data within them and joins between tables to allow querying of the data.

### Related Table

Related Table contains more data about the customer that can be used for segmenting users. These tables may be joined with primary table or to other related tables.

### Events Table

Events Table captures all user interactions, such as clicks, purchases, or app usage. This may include anonmyous events data which is resolved to a unique user through joins directly or indirectly with primary table. This unlocks event-based analysis to create audiences and segment users into different cohorts.

### Audience

Audience is a defined segment of users based on specific criteria, such as demographics, behaviors, or purchase history. These audiences can be created by choosing filters on Sortment, or through conversation with an AI agent on Sortment.

### Custom Properties

Custom Properties are aggregated attributes attached to users, events, or other data that allows marketers to create more tailored messages and experiences. This stores the logic for a new property for a user which does not directly exist in the data warehouse, and is added to queries for segmentation or campaign data.

### Campaign

Campaigns are one time or recurring messages sent to an audience with a clear goal, such as increasing sales or customer retention. Each campaign is sent to a channel, with analytics available to track their effectiveness.

### Journeys

Journeys are multi-step, automated campaigns aimed at engaging users across various channels, such as email, push notifications, in-app messages, and more. They are real-time communications managed with certain events user does on the app, website or other interface.

### Real-time Events

These are specific actions or interactions that users take within an app or website, which can be tracked and utilized to enhance customer engagement and personalized marketing strategies. Events need to be whitelisted on Sortment before they can be used in Journeys to send communications to the user.

### Profiles

Profiles refer to the individual user record in Sortment. It aggregate data about user interactions, preferences, and behaviors.

