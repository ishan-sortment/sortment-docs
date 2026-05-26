---
hidden: true
---

# Sortment for beginners

## How Sortment Works

Sortment is a warehouse-native customer engagement platform. It connects to your data warehouse, reads your customer data directly from it, and uses that data to send messages across channels like Email, WhatsApp, SMS, and Push.

The data never moves. Sortment reads from your warehouse when it needs to evaluate an audience, personalise a message, or run a journey. Nothing is copied or stored on Sortment's side.

***

### Where Your Data Lives

#### Data Warehouse

Your [data warehouse](../setup/data-warehouses/) is the starting point. It is where your customer records, transaction history, behavioural data, and events all live. Sortment connects to it with read access and uses it as the source of truth for everything. Sortment supports **Snowflake, Google BigQuery, Amazon Redshift, Databricks**, and **PostgreSQL**.

#### Cloud Bucket Storage

Alongside the warehouse, Sortment also connects to a [cloud bucket](../setup/cloud-bucket-storage/) (AWS S3, Google Cloud Storage, or Azure Blob Storage depending on your setup). The bucket is used to stage real-time event data before it gets loaded into the warehouse, and to store campaign-related assets.

***

### The Three Types of table Sortment Works With

#### Primary Table

Your core customer table, with one row per user and a unique user ID. Everything in Sortment is anchored to this table. Audiences are built from it, campaigns are addressed to users in it, and all other data is connected back to it. The user ID is how Sortment identifies each individual across channels and campaigns.

#### Related Tables

Tables that contain more information about your customers. They might hold order history, subscription records, support tickets, ride data, or booking records. Related tables are joined to the primary table (or to each other) so that segmentation can draw on all of this data together.

For example, if you want to target users who placed more than three orders in the last 30 days, that logic runs across the primary table and the orders related table.

#### Events Table

Events capture what users do in your app, on your website, or through other interfaces. Each event has a user ID, an event name, and a timestamp. Examples: app opened, item purchased, booking abandoned, payment failed.

The events table enables audience building based on user behaviour over time. Events in the warehouse are available after the next data sync. They are not real-time. For real-time journey triggers, Sortment has a separate mechanism covered below.

> **What is a warehouse sync?** A warehouse sync is the process your data team has set up to move data from your app or product into the warehouse on a schedule. Think of it like a regular update. Your warehouse is refreshed every few minutes, hours, or once a day depending on how your team has configured it. Sortment reads from the warehouse after each of these updates, which means anything that happened between two syncs will only be visible to Sortment once the next sync completes. If you are unsure how frequently your warehouse syncs, your data engineering team will know.

***

### How the Data Comes Together

#### Schema

Before Sortment can use your data, it needs to understand how it is structured. This is done through [schema setup](../schema/overview.md), a one-time mapping that tells Sortment which table is the primary table, which tables are related, and how they connect to each other through joins.

Once the schema is defined, Sortment generates SQL queries automatically based on the relationships you have mapped.

***

### What Sortment Does With the Data

#### Audiences

An [audience](../engage/audiences/) is a defined group of users who meet specific criteria. Those criteria can be based on anything in the primary table, any related table, or any events table. The audience is evaluated by querying the warehouse directly, so it always reflects the current state of your data.

Audiences can be built using a visual filter builder, by writing SQL directly, or by describing what you want to the AI assistant in plain language.

#### Campaigns

A [campaign](../engage/campaigns/) is a message, one-time or recurring, sent to an audience across a channel. The message content can be personalised using any data from the warehouse, with values calculated live at send time. Sortment routes the message through the channel provider you have configured.

#### Journeys

A [journey](../journeys/) is a multi-step automated flow that moves users through a sequence of messages and logic. Journeys can be triggered in several ways:&#x20;

* When a user performs an action, on a defined schedule (for example, every hour targeting users who have not completed a booking)
* When a user enters or exits a specific audience
* When a user exits another journey.
* Via [API events](../setup/real-time-events/) - This allows users to enter the journey immediately as soon as the event is received on Sortment (Realtime journeys)&#x20;

#### Attributes

Not every data point you need for personalisation or segmentation exists as a column in your warehouse. Custom [attributes](../engage/attributes/) let you define computed values, such as aggregations, calculations, or conditional logic, that Sortment evaluates live at query time.

For example, "number of completed rides in the last 90 days" is not a column that exists in most warehouses. It is a calculation across the rides table per user. You define it once as a custom property and from that point it is available everywhere in Sortment, in audience filters, in message personalisation, analysis and in profiles.

Custom attributes are never stored. The logic is saved, but the value is always calculated fresh from the warehouse when it is needed.

***

### Real-Time Events

In addition to the events table in your warehouse, Sortment supports [real-time event](../setup/real-time-events/) ingestion through an API. Your app or server sends events directly to Sortment as they happen. These events are user for immediately triggering journeys/real-time usecases.

**Why to setup API events?** - Warehouse events are available after the next warehouse sync. Real-time API events are available the moment they are received and allow entering a journey instantly and receiving a campaign immediately when a user performs an action.

***

### The AI Assistant

Sortment has a built-in AI assistant that works across all of the above. It can build audiences, create attributes, write SQL, design templates, create campaigns, and build journeys, all from a plain language prompt.

The AI works with three things:

* **Schema** - so it knows what tables and columns exist
* **Intelligence blocks** - context you give it about your business, your data definitions, and your brand
* **Existing entities in your workspace** - so it does not duplicate work that already exists

The more context you give it through intelligence blocks, the more accurately it can work.
