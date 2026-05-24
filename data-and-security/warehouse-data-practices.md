# Warehouse Data Practices

Sortment is designed to seamlessly connect with data warehouses and external communication channels to help businesses segment audiences, and send targeted campaigns or journeys to their customers. Here's a detail overview on how data is accessed and managed from data security perspective.

### Data Management

#### 1. Warehouse Data Access

* **Audience Creation:** Sortment connects to your data warehouse with read-only access to your datasets and schema. \
  To save audiences, Sortment takes access to a different schema to write back into your warehouse for using in campaigns and journeys.
* **Profile Sync:** User Profiles is modelled and maintained in the warehouse in the schema shared with Sortment for write access. It is synced at regular intervals (as configured in the workspace settings) into your private cloud storage to make user properties accessible for journey setup.
* **Campaigns:** Sortment queries your data tables and creates campaign specific tables at the time of campaign send with personalisation variables. This is sent to respective integration for communication.
* **Analytics:** Campaign analytics is queried on the warehouse tables with data from campaign events table to track analytics for your campaigns and journeys.

#### 2. Data Encryption

* **Data at Rest:** Data resides in warehouse and managed by your data policies and governance.
* **Data in Transit:** Data transmitted between Sortment and external systems is encrypted using TLS (Transport Layer Security), ensuring that data remains secure during transmission.

#### 3. Data Access Control

* **Role-Based Access Control (RBAC):** Sortment implements strict access control mechanisms to ensure that data is only accessible to authorized users.
* **Schema Setup:** During onboarding, Column-based data control is available to limit which columns can be used for filtering. Personally Identifiable Information (PII) can be masked to not show details of customers to users on Sortment.

#### 4. Data Retention and Deletion

* **Retention Policies:** Sortment retains data as long as necessary to fulfil business purposes and complies with user requests for data deletion. The admin maintain full control of deletion of data from warehouse and connected cloud bucket storage.
* **Deletion Requests:** Users can request the deletion of their data, and Sortment ensures that data is permanently removed from both the Sortment platform and external connected systems, as applicable.

5. **Usage of AI**

* Sortment ensures that **only metadata** is processed and sent to the LLMs for analysis. No sensitive user or business data is shared externally. All processing is done securely, and data privacy is strictly maintained throughout. Metadata may include:
  * Table names
  * Column names and descriptions
  * Aggregation functions (e.g., average, sum)
  * User-provided filters and conditions
* Sortment provides users with the option to **opt out** of AI-driven features at any time. If you choose to disable AI functionalities, Sortment will continue to the platform without leveraging LLMs.
