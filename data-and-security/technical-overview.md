---
description: >-
  This document explains the technical architecture for Sortment, designed to
  help understand how data flows across the platform.
---

# Technical Overview

<figure><img src="../.gitbook/assets/Sortment - working diagram@2x (1).png" alt=""><figcaption><p>Sortment architecture diagram</p></figcaption></figure>



### **1. Overview** <a href="#id-1.-overview" id="id-1.-overview"></a>

Sortment uses a modular, scalable, and warehouse-native architecture that enables effective omnichannel messaging. This setup ensures that marketing and data teams can efficiently manage user events, campaigns, and messaging workflows while leveraging clean, actionable data directly from the data warehouse.

#### **Key Components** <a href="#key-components" id="key-components"></a>

* **Data Warehouse** (e.g., Snowflake, BigQuery)
* **Bucket Storage** (e.g., S3, Cloud Storage)
* **Segmentation Engine**
* **Journey Orchestrator**
* **Events Consumer** (Kafka-based)
* **Notifications Layer** (Email, WhatsApp, SMS)
* **Data Sources** (Apps, Websites, Segment, Rudderstack)
* **Campaign Automation and Analytics**

### **2. Data Flow Architecture** <a href="#id-2.-data-flow-architecture" id="id-2.-data-flow-architecture"></a>

The data flow within Sortment architecture can be broken into four main phases:

#### **Phase 1: Audience Segmentation and Campaign Orchestration** <a href="#phase-1-audience-segmentation-and-campaign-orchestration" id="phase-1-audience-segmentation-and-campaign-orchestration"></a>

1. **Segmentation Engine**:
   * The team can create user segments on the **Data Warehouse** using visual builder or AI based on event properties and profiles. This engine converts the filters into queries.
   * Segmentation results can be fed into downstream systems for campaign execution.
   * Audience creation supports SQL-based queries and CSV imports for flexibility.
2. **Campaign Automation:**
   * Marketers can use a user-friendly campaign and journey builder to trigger automated messages, reducing reliance on engineering teams.
3. **Journey Orchestrator**:
   * Accesses profiles stored in **Bucket Storage**. This is refreshed at regular sync from **Data Warehouse**
   * Consumes journey-related events from the **Events Consumer**.
   * Orchestrates complex user journeys based on real-time and historical data.

> _Outcome_: Audiences are segmented, and dynamic journeys are triggered based on user behaviors and profiles.

***

#### **Phase 2: Real-Time Event Processing** <a href="#phase-2-real-time-event-processing" id="phase-2-real-time-event-processing"></a>

1. **Data Sources**: Events are generated from multiple sources, including:
   * Applications (mobile or web)
   * Websites
   * Third-party CDPs (Segment, Rudderstack)
2. **Event Delivery**: These real-time events are sent to the **Events Consumer**, which is built on a Kafka-based infrastructure to handle high-throughput data streams.

> _Outcome_: Events are ingested in real-time and persisted for campaign conversion tracking and journey triggers and filters.

***

#### **Phase 3: Event Storage and Campaign Persistence** <a href="#phase-3-event-storage-and-campaign-persistence" id="phase-3-event-storage-and-campaign-persistence"></a>

1. **Events Consumer**:
   * Persists all campaign-related events into **Bucket Storage** (e.g., Amazon S3, Cloud Storage).
   * Sync events to the **Data Warehouse** for analytical querying.
2. **Profiles Sync**:
   * User profiles and event data are regularly synced between the **Data Warehouse** and **Bucket Storage**.
3. **Real-Time Capabilities**:
   * Events can be used to trigger real-time campaigns with sub-second latency via APIs.

> _Outcome_: Data is stored back in warehouse, available for querying, and ready for real-time campaign triggering.

***

#### **Phase 4: Omnichannel Campaign Execution** <a href="#phase-4-omnichannel-campaign-execution" id="phase-4-omnichannel-campaign-execution"></a>

1. **Campaign Event Delivery**:
   * The **Events Consumer** sends campaign events to the **Notifications Layer**.
2. **Notifications Layer**:
   * Distributes messages across multiple channels:
     * **Email**
     * **WhatsApp**
     * **SMS**
3. **Feedback Loop**:
   * Events generated from campaign engagement (e.g., opens, clicks, purchases) are sent back as real-time events to the **Events Consumer** and then **Data Warehouse** for further processing and analysis.

> _Outcome_: Marketing messages are delivered across preferred channels with real-time triggers and automated workflows.

***

### **3. Key Features of Sortment** <a href="#id-3.-key-features-of-sortment" id="id-3.-key-features-of-sortment"></a>

#### **Warehouse-Native Architecture** <a href="#warehouse-native-architecture" id="warehouse-native-architecture"></a>

* Direct integration with data warehouses (e.g., Snowflake, BigQuery) ensures real-time access to clean, actionable data without creating data copies.
* Enables teams to work with accurate and up-to-date data while maintaining security and compliance.

#### **Real-Time Capabilities** <a href="#real-time-capabilities" id="real-time-capabilities"></a>

* Supports real-time message triggering with sub-second latency via APIs.
* High-throughput Kafka-based ingestion ensures scalability for large event volumes and accuracy.

#### **Segmentation and Audience Creation** <a href="#segmentation-and-audience-creation" id="segmentation-and-audience-creation"></a>

* SQL-based and CSV-supported audience creation enables advanced segmentation for campaigns.
* Segmentation engine allows flexible, self-serve queries for building target audiences.

#### **Campaign Automation** <a href="#campaign-automation" id="campaign-automation"></a>

* Intuitive journey builder to automate customer experiences across channels.
* Reduces dependency on engineering teams for campaign execution.

#### **Analytics and Insights** <a href="#analytics-and-insights" id="analytics-and-insights"></a>

* Provides self-serve insights for measuring campaign performance directly from warehouse data.
* Allows for experimentation (A/B testing) to improve campaign strategies.

#### **Privacy and Security** <a href="#privacy-and-security" id="privacy-and-security"></a>

* Warehouse-native architecture eliminates data duplication.
* Granular access control, secure connections, and SOC 2 certification ensure privacy and compliance.

***

### **5. Integration with Existing Client Systems** <a href="#id-5.-integration-with-existing-client-systems" id="id-5.-integration-with-existing-client-systems"></a>

Sortment is designed to integrate seamlessly with existing client data ecosystems. Below are key integration points:

* **Data Ingestion**:
  * Connectors for popular CDPs like Segment and Rudderstack
  * APIs for direct event streaming
* **Data Warehouse Integration**:
  * Support for Snowflake, BigQuery, Redshift
* **Storage Compatibility**:
  * Cloud providers like AWS S3 and GCP Cloud Storage
* **Notification Platforms**:
  * Email providers (e.g., SendGrid, SES)
  * WhatsApp
  * SMS

***

For further details or queries, please [reach out](mailto:support@sortment.com) to us.
