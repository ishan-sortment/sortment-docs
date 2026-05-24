# HubSpot → Data Warehouse

## Connection methods and marketing analytics tables

**Sortment internal reference - onboarding playbook**

This document is a definitive reference for every supported method of connecting HubSpot marketing data into a data warehouse, and for every table available in each method. It is structured for merchant onboarding - specifically to determine which tables Sortment can expect to find when it is granted read access to a merchant's data warehouse schema, and how to build accurate email campaign analytics from those tables.

Merchants may be running several data warehouses, including Snowflake, Amazon Redshift, Google BigQuery, AWS Athena, or Databricks. This document covers all common pipeline methods. Where a method or SQL syntax is specific to one warehouse platform, it is explicitly noted.

Each method section includes: (a) a description of how the pipeline works and what it requires, (b) a complete table reference for marketing-relevant tables, and (c) gotchas and caveats that affect query accuracy. The final sections cover the sent → opened → clicked → converted funnel pattern and a decision matrix for matching each merchant to the right method.

***

### 1. Connection methods at a glance

HubSpot data can reach a data warehouse through six distinct paths. The method determines what schema the data lands in, how fresh it is, and critically, what tables are available for marketing analytics.

| Method                               | Provider                       | HubSpot Tier Req.     | Latency                | Data Lands In         |
| ------------------------------------ | ------------------------------ | --------------------- | ---------------------- | --------------------- |
| Native Data Share _(Snowflake only)_ | HubSpot (built-in)             | Ops Hub Professional+ | 15 min (Live) / Daily  | Shared DB (read-only) |
| Fivetran ETL                         | Fivetran                       | Any HubSpot tier      | Configurable (15 min+) | Merchant's own schema |
| Airbyte ETL                          | Airbyte (open-source or Cloud) | Any HubSpot tier      | Configurable           | Merchant's own schema |
| Stitch (Qlik) ETL                    | Qlik/Stitch                    | Any HubSpot tier      | Configurable           | Merchant's own schema |
| Estuary Flow                         | Estuary                        | Any HubSpot tier      | Near real-time         | Merchant's own schema |
| Windsor.ai / Supermetrics            | Windsor / Supermetrics         | Any HubSpot tier      | Daily typical          | Merchant's own schema |

The most common pattern in merchant stacks encountered during Sortment onboarding is Fivetran (managed ETL) followed by HubSpot's Native Data Share (Snowflake accounts only). Airbyte and Stitch are less common but follow the same logical data model and work with any warehouse destination.

***

### 2. Method A: HubSpot Native Snowflake Data Share

> **Snowflake-specific.** This method uses Snowflake's Secure Data Sharing technology and is only available to merchants whose data warehouse is Snowflake. Merchants on Redshift, BigQuery, Athena, or Databricks must use one of the ETL-based methods (B-F) instead.

#### How it works

HubSpot acts as the Snowflake data provider. No data is physically copied - Snowflake's Secure Data Sharing grants the merchant's Snowflake account read-only access to a shared database that HubSpot maintains. The merchant sees the data in their Snowflake instance without any ETL infrastructure.

* **Requires:** Operations Hub Professional or Enterprise
* **Latency:** V2\_LIVE schema refreshes every 15 minutes; V2\_DAILY refreshes once per day
* **Schema naming:** `HUB_{portalId}_DB.V2_LIVE.{TABLE_NAME}` or `.V2_DAILY.{TABLE_NAME}`
* **Read-only:** the merchant cannot write back to this database

V2\_LIVE and V2\_DAILY contain the same tables. V2\_LIVE is preferred for near-real-time queries. V2\_DAILY is preferred for large batch analytics to avoid query cost on a rapidly updating dataset. Some views (`association_definitions`, `owners`, `pipelines`, `pipeline_stages`) are only updated daily even in V2\_LIVE.

#### 2.1 Email event tables

Email event data is sharded: each event type is its own table. You query them separately and join on `OBJECTID` (contact ID) and `PROPERTY_HS_EMAIL_CAMPAIGN_ID`.

| Table Name (V2\_DAILY / V2\_LIVE)     | Event Type                    | Key Columns                                                                                 |
| ------------------------------------- | ----------------------------- | ------------------------------------------------------------------------------------------- |
| EVENTS\_SENT\_EMAIL\_V2               | Send event per contact        | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID                                     |
| EVENTS\_DELIVERED\_EMAIL\_V2          | Confirmed delivery            | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID                                     |
| EVENTS\_OPENED\_EMAIL\_V2             | Email open                    | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID                                     |
| EVENTS\_CLICKED\_LINK\_IN\_EMAIL\_V2  | Link click                    | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID, PROPERTY\_HS\_CLICK\_ORIGINAL\_URL |
| EVENTS\_BOUNCED\_EMAIL\_V2            | Hard or soft bounce           | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID, PROPERTY\_HS\_BOUNCE\_REASON       |
| EVENTS\_UNSUBSCRIBED\_FROM\_EMAIL\_V2 | Unsubscribe                   | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID                                     |
| EVENTS\_MARKED\_EMAIL\_AS\_SPAM\_V2   | Spam report                   | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID                                     |
| EVENTS\_FORWARDED\_EMAIL\_V2          | Email forward                 | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID                                     |
| EVENTS\_SCHEDULED\_EMAIL\_V2          | Scheduled for send            | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID                                     |
| EVENTS\_DEFERRED\_EMAIL\_V2           | Send deferred (temp. failure) | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID                                     |
| EVENTS\_DROPPED\_EMAIL\_V2            | Dropped before send           | OBJECTID, OCCURREDAT, PROPERTY\_HS\_EMAIL\_CAMPAIGN\_ID                                     |

#### 2.2 Object tables

Object tables hold current-state records for each HubSpot object. Properties are flattened as columns (`PROPERTY_*`).

| Table Name                 | What It Contains                          | Key Columns                                                                                               |
| -------------------------- | ----------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| OBJECTS\_CONTACTS          | All CRM contacts                          | OBJECTID, PROPERTY\_EMAIL, PROPERTY\_FIRSTNAME, PROPERTY\_LASTNAME, PROPERTY\_HS\_LEAD\_STATUS            |
| OBJECTS\_CAMPAIGNS         | Marketing campaign records                | OBJECTID, PROPERTY\_HS\_NAME, PROPERTY\_HS\_GOAL, PROPERTY\_HS\_BUDGET\_ITEMS\_SUM\_AMOUNT                |
| OBJECTS\_MARKETING\_EMAILS | Email asset metadata                      | OBJECTID, PROPERTY\_HS\_NAME, PROPERTY\_HS\_SUBJECT, PROPERTY\_HS\_SEND\_DATE, PROPERTY\_HS\_CAMPAIGN\_ID |
| OBJECTS\_DEALS             | Deal pipeline records (conversion signal) | OBJECTID, PROPERTY\_DEALNAME, PROPERTY\_AMOUNT, PROPERTY\_DEALSTAGE, PROPERTY\_CLOSEDATE                  |
| OBJECTS\_FORMS             | Form submissions (alt. conversion signal) | OBJECTID, PROPERTY\_HS\_FORM\_ID, PROPERTY\_HS\_NAME, PROPERTY\_HS\_CREATED\_AT                           |
| OBJECTS\_COMPANIES         | Company / account records                 | OBJECTID, PROPERTY\_NAME, PROPERTY\_DOMAIN, PROPERTY\_INDUSTRY, PROPERTY\_NUMBEROFEMPLOYEES               |
| OBJECTS\_LISTS             | HubSpot contact/company lists             | OBJECTID, PROPERTY\_HS\_LIST\_ID, PROPERTY\_HS\_NAME, PROPERTY\_HS\_LIST\_TYPE                            |
| OBJECTS\_WORKFLOWS         | Automation workflows                      | OBJECTID, PROPERTY\_HS\_NAME, PROPERTY\_HS\_STATUS                                                        |

#### 2.3 Association tables

Association tables are the join layer between objects. You need these to connect email events (which carry a contact ID) to deals or companies.

| Association Table                              | What It Links                                                    |
| ---------------------------------------------- | ---------------------------------------------------------------- |
| ASSOCIATIONS\_CONTACTS\_TO\_DEALS              | Contact → Deal (join for conversion attribution)                 |
| ASSOCIATIONS\_CONTACTS\_TO\_COMPANIES          | Contact → Company (account-level analytics)                      |
| ASSOCIATIONS\_CAMPAIGNS\_TO\_FORMS             | Campaign → Form (form conversion attribution)                    |
| ASSOCIATIONS\_CONTACTS\_TO\_FORMS              | Contact → Form submission                                        |
| ASSOCIATIONS\_MARKETING\_EMAILS\_TO\_CAMPAIGNS | Email asset → Campaign (links the email content to the campaign) |

> **Critical ID mismatch:** the `OBJECTID` in `OBJECTS_CAMPAIGNS` is not the same as `PROPERTY_HS_EMAIL_CAMPAIGN_ID` in event tables. HubSpot uses an internal content/asset ID for that field. Always validate this join in a sample query before building dashboards.

***

### 3. Method B: Fivetran ETL Connector

#### How it works

Fivetran is a managed ETL service that extracts data from HubSpot's APIs and loads it into the merchant's own data warehouse. This is the most feature-complete ETL connector for HubSpot marketing analytics. Fivetran handles schema changes automatically, rate limiting, incremental syncs, and retries. It supports all major warehouse destinations including Snowflake, Redshift, BigQuery, and Databricks.

* **Requires:** any HubSpot tier; Fivetran subscription; data warehouse destination
* All tables land in a schema the merchant names (typically `hubspot` or `hubspot_fivetran`)
* Schema changes in HubSpot propagate automatically without full resyncs
* Email event child tables must be individually enabled in the connector Schema tab

#### 3.1 Email and campaign tables

Fivetran shards email events into separate child tables - one table per event type. Each child table must be explicitly enabled in the Fivetran connector settings, or it will be empty.

| Table Name                 | Sync Mode   | Notes                                                                                            |
| -------------------------- | ----------- | ------------------------------------------------------------------------------------------------ |
| EMAIL\_CAMPAIGN            | Incremental | Campaign-level metadata: name, app\_id, counters (sent, opens, clicks) at time of sync           |
| EMAIL\_EVENT               | Incremental | Parent event table. Must have child tables selected in Schema tab or it won't populate.          |
| EMAIL\_EVENT\_SENT         | Incremental | One row per send. Columns: id, email\_campaign\_id, email\_address, recipient, sent\_by, created |
| EMAIL\_EVENT\_DELIVERED    | Incremental | Delivery confirmation events                                                                     |
| EMAIL\_EVENT\_OPEN         | Incremental | Open events. Includes user\_agent for device/client analysis                                     |
| EMAIL\_EVENT\_CLICK        | Incremental | Click events. Includes url (clicked URL) and user\_agent                                         |
| EMAIL\_EVENT\_BOUNCE       | Incremental | Bounce events. Includes bounce\_type (HARD/SOFT), status, and reason                             |
| EMAIL\_EVENT\_DEFERRED     | Incremental | Temporary delivery deferral events                                                               |
| EMAIL\_EVENT\_DROPPED      | Incremental | Dropped before send (e.g. unsubscribed list). Includes reason field                              |
| EMAIL\_EVENT\_UNSUBSCRIBE  | Incremental | Unsubscribe events. Includes portal\_id, email\_campaign\_id                                     |
| EMAIL\_EVENT\_SPAM\_REPORT | Incremental | Spam complaint events                                                                            |
| EMAIL\_EVENT\_FORWARD      | Incremental | Email forward events                                                                             |
| EMAIL\_EVENT\_PRINT        | Incremental | Print events (rare, browser print action)                                                        |

#### 3.2 CRM and supporting tables

| Table Name                | Sync Mode   | Notes                                                                                                            |
| ------------------------- | ----------- | ---------------------------------------------------------------------------------------------------------------- |
| CONTACT                   | Incremental | All contact properties. Companion: CONTACT\_PROPERTY\_HISTORY for historical values                              |
| COMPANY                   | Incremental | Company records + COMPANY\_PROPERTY\_HISTORY                                                                     |
| DEAL                      | Incremental | Deal records. Child tables: DEAL\_PROPERTY\_HISTORY, DEAL\_STAGE. Join to EMAIL events on contact for conversion |
| FORM                      | Full        | Form definitions (not submissions - use FORM\_SUBMISSION)                                                        |
| FORM\_SUBMISSION          | Incremental | Each form fill. Joinable to contacts for conversion tracking                                                     |
| OWNER                     | Full        | HubSpot user/owner records                                                                                       |
| ENGAGEMENT                | Incremental | Parent engagement table. Child tables per type: NOTE, EMAIL, TASK, MEETING, CALL                                 |
| CONTACT\_COMPANY          | Full        | Association: contact ↔ company                                                                                   |
| CONTACT\_LIST             | Full        | HubSpot list definitions                                                                                         |
| CONTACT\_LIST\_MEMBER     | Full        | Which contacts are in which lists                                                                                |
| DEAL\_PIPELINE            | Full        | Pipeline definitions and stages for deal tracking                                                                |
| LINE\_ITEM\_DEAL          | Incremental | Association between line items and deals (e-commerce)                                                            |
| TICKET / TICKET\_PIPELINE | Incremental | Support tickets and their pipeline stages                                                                        |
| WORKFLOW                  | Full        | Automation workflow definitions                                                                                  |
| SUBSCRIPTION\_CHANGE      | Incremental | Email subscription changes per contact (opt-in/opt-out history)                                                  |

#### 3.3 Optional: Fivetran dbt package (`dbt_hubspot`)

If the merchant runs the Fivetran `dbt_hubspot` package on top of the raw tables, they will have a set of pre-built analytics models. These are significantly easier to query for funnel analysis and are the preferred layer when available.

| dbt Model                   | What You Get                                                                                                                               |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| hubspot\_\_email\_campaigns | One row per campaign. Pre-aggregated sent, delivered, open, click, bounce, unsubscribe, spam counts. The go-to table for funnel reporting. |
| hubspot\_\_email\_sends     | One row per sent email enriched with whether that specific send was opened, clicked, or bounced.                                           |
| hubspot\_\_email\_events    | All email events joined with campaign and contact context, ready for analysis without manual joins.                                        |
| hubspot\_\_contacts         | SCD Type 2 contact model - tracks property changes over time, not just current state.                                                      |
| hubspot\_\_companies        | SCD Type 2 company model with engagement activity joined in.                                                                               |
| hubspot\_\_deals            | Deal model joined to contact engagement - use this to attribute closed deals back to campaigns.                                            |
| hubspot\_\_engagements      | All CRM engagement activities (calls, meetings, notes, tasks) normalized and company/contact-joined.                                       |

The dbt package is not auto-installed - a merchant must explicitly configure and run it. Ask during onboarding whether their data team runs dbt on top of Fivetran. If yes, the `hubspot__email_campaigns` model is the best single table for aggregate campaign funnel analytics.

***

### 4. Method C: Airbyte ETL Connector

#### How it works

Airbyte is an open-source (and cloud-hosted) ELT platform. Its HubSpot connector maps each API resource to a stream, which becomes a table in the destination data warehouse. Unlike Fivetran, Airbyte consolidates all email event types into a single `email_events` table with a `type` field - there are no separate child tables per event type. Airbyte supports all major warehouse destinations.

* **Requires:** any HubSpot tier; Airbyte OSS or Cloud; data warehouse destination
* **Authentication:** HubSpot Private App token or OAuth
* **Sync frequency:** configurable, from minutes to daily
* **Email events:** all types in one table (`type` column = SENT, OPEN, CLICK, BOUNCE, etc.)

| Stream (Table in data warehouse) | What It Contains                                                                                                                        |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| campaigns                        | Campaign metadata from the HubSpot Email Campaigns API                                                                                  |
| marketing\_emails                | Email asset records including subject line, send date, and campaign association                                                         |
| email\_events                    | All email events in a single table (type field distinguishes SENT, OPEN, CLICK, BOUNCE, etc.) - unlike Fivetran's separate child tables |
| contacts                         | Contact records with all properties                                                                                                     |
| contacts\_list\_memberships      | Which lists each contact belongs to                                                                                                     |
| companies                        | Company records                                                                                                                         |
| deals                            | Deal pipeline records for conversion tracking                                                                                           |
| deal\_pipelines                  | Pipeline and stage definitions                                                                                                          |
| engagements\_calls               | Call engagement records                                                                                                                 |
| engagements\_emails              | 1:1 CRM email engagements (not marketing emails)                                                                                        |
| engagements\_meetings            | Meeting engagements                                                                                                                     |
| engagements\_notes               | Notes attached to CRM records                                                                                                           |
| engagements\_tasks               | Task records                                                                                                                            |
| forms                            | Form definitions                                                                                                                        |
| owners                           | HubSpot user/owner records                                                                                                              |
| tickets                          | Support tickets                                                                                                                         |
| workflows                        | Automation workflows                                                                                                                    |
| email\_subscriptions             | Subscription type definitions and contact opt-in status                                                                                 |
| goals                            | HubSpot Goals objects                                                                                                                   |
| line\_items                      | E-commerce line items associated with deals                                                                                             |
| products                         | Product catalogue records                                                                                                               |
| quotes                           | Sales quote records                                                                                                                     |

Airbyte's `email_events` table uses a different query pattern than Fivetran. Instead of joining multiple child tables, you filter on the `type` column: `WHERE type = 'OPEN'`. Confirm this structure before writing any SQL against an Airbyte-sourced schema.

***

### 5. Method D: Stitch (Qlik) ETL Connector

#### How it works

Stitch (now part of Qlik) is a managed ETL tool with a HubSpot connector. Its table structure is similar to Airbyte - a unified `email_events` table - but with fewer streams than Fivetran. An important limitation: replicating the `email_events` table requires Super Admin permissions in HubSpot. If the merchant's integration was set up with a lower-permission user, email events will be absent.

* **Requires:** any HubSpot tier; Stitch subscription; data warehouse destination
* **Super Admin required** in HubSpot for `email_events` replication
* Smaller stream library than Fivetran - some engagement sub-types are absent

| Table Name            | What It Contains                                                                            |
| --------------------- | ------------------------------------------------------------------------------------------- |
| campaigns             | Campaign metadata. Primary key: id                                                          |
| email\_events         | All email events. Requires Super Admin permissions in HubSpot to replicate. Primary key: id |
| contacts              | Contact records with all custom properties flattened. Primary key: canonical\_vid           |
| companies             | Company records. Primary key: company\_id                                                   |
| deals                 | Deal records. Primary key: deal\_id                                                         |
| forms                 | Form definitions. Primary key: guid                                                         |
| keywords              | Portal keywords (SEO tool data). Primary key: keyword\_guid                                 |
| owners                | HubSpot owner/user records. Primary key: owner\_id                                          |
| subscription\_changes | Email subscription opt-in/opt-out change history                                            |
| workflows             | Automation workflow definitions                                                             |

Stitch replicates `email_events` as a unified table with a `type` field - the same pattern as Airbyte. Query pattern: filter on `type` rather than joining separate tables.

***

### 6. Method E and F: Estuary, Windsor, and others

#### Estuary Flow

Estuary is a newer real-time ELT platform with a HubSpot connector. It uses a streaming-first architecture, meaning data can land in the data warehouse with sub-minute latency. Table structure follows the same logical model as Fivetran/Airbyte but varies by configuration. Less common in merchant stacks as of mid-2026 but growing.

* Key tables: `contacts`, `companies`, `deals`, `email_events` (unified), `marketing_emails`, `campaigns`
* Latency: near real-time (minutes, not hours)
* Well-suited for merchants who need very fresh campaign data

#### Windsor.ai / Supermetrics

These are reporting-layer tools, not full ELT pipelines. They typically sync aggregated campaign metrics rather than raw event-level data. As a result, they are useful for high-level reporting but insufficient for contact-level funnel analysis. You cannot trace an individual contact's journey from send to conversion.

* Typical tables: `hubspot_campaigns` (aggregated metrics), `hubspot_ads`, `hubspot_email_performance`
* **Not suitable** for contact-level attribution or funnel analysis
* If a merchant uses only Windsor or Supermetrics, raw event tables will not be present

***

### 7. Building the Sent → Opened → Clicked → Converted funnel

Regardless of which pipeline method the merchant uses, the funnel logic follows the same pattern. What varies is the table names and how events are stored (sharded vs. unified).

| Funnel Stage | Source Table(s)                                                          | Notes                                                                                                                                     |
| ------------ | ------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Sent         | EVENTS\_SENT\_EMAIL\_V2 / EMAIL\_EVENT\_SENT / email\_events             | Count distinct OBJECTID or email\_address per campaign. The denominator for all other rates.                                              |
| Delivered    | EVENTS\_DELIVERED\_EMAIL\_V2 / EMAIL\_EVENT\_DELIVERED                   | Delivery rate = Delivered / Sent. Bounced = Sent - Delivered.                                                                             |
| Opened       | EVENTS\_OPENED\_EMAIL\_V2 / EMAIL\_EVENT\_OPEN                           | Open rate = unique openers / Delivered. Count distinct contact per campaign for unique opens.                                             |
| Clicked      | EVENTS\_CLICKED\_LINK\_IN\_EMAIL\_V2 / EMAIL\_EVENT\_CLICK               | CTOR = unique clickers / unique openers. Also available: which URLs were clicked.                                                         |
| Converted    | OBJECTS\_DEALS + ASSOCIATIONS\_CONTACTS\_TO\_DEALS (or FORM\_SUBMISSION) | No native email-to-deal event exists. Define conversion as: deal created within N days of a click on the campaign, joined via contact ID. |

> **SQL syntax note:** The sample queries below use Snowflake / Redshift-compatible syntax (`DATEADD`). BigQuery uses `DATE_SUB(CURRENT_DATE(), INTERVAL 7 DAY)` and Databricks uses `CURRENT_DATE - INTERVAL 7 DAYS`. Adjust accordingly for the merchant's warehouse.

#### Sample SQL - Fivetran (sharded event tables)

```sql
SELECT
  ec.name                              AS campaign_name,
  COUNT(DISTINCT s.email_address)      AS sent,
  COUNT(DISTINCT d.email_address)      AS delivered,
  COUNT(DISTINCT o.email_address)      AS opened,
  COUNT(DISTINCT c.email_address)      AS clicked
FROM email_campaign ec
LEFT JOIN email_event_sent      s ON s.email_campaign_id = ec.id
  AND s.created >= DATEADD('day', -7, CURRENT_DATE)
LEFT JOIN email_event_delivered d ON d.email_campaign_id = ec.id
  AND d.created >= DATEADD('day', -7, CURRENT_DATE)
LEFT JOIN email_event_open      o ON o.email_campaign_id = ec.id
  AND o.created >= DATEADD('day', -7, CURRENT_DATE)
LEFT JOIN email_event_click     c ON c.email_campaign_id = ec.id
  AND c.created >= DATEADD('day', -7, CURRENT_DATE)
GROUP BY ec.name;
```

#### Sample SQL - Airbyte/Stitch (unified `email_events` table)

```sql
SELECT
  email_campaign_id,
  COUNT(DISTINCT CASE WHEN type = 'SENT'      THEN recipient END) AS sent,
  COUNT(DISTINCT CASE WHEN type = 'DELIVERED' THEN recipient END) AS delivered,
  COUNT(DISTINCT CASE WHEN type = 'OPEN'      THEN recipient END) AS opened,
  COUNT(DISTINCT CASE WHEN type = 'CLICK'     THEN recipient END) AS clicked
FROM email_events
WHERE created >= DATEADD('day', -7, CURRENT_DATE)
GROUP BY email_campaign_id;
```

#### Sample SQL - Native Data Share (sharded, `V2_DAILY` schema - Snowflake only)

```sql
SELECT
  s.PROPERTY_HS_EMAIL_CAMPAIGN_ID      AS campaign_id,
  COUNT(DISTINCT s.OBJECTID)           AS sent,
  COUNT(DISTINCT d.OBJECTID)           AS delivered,
  COUNT(DISTINCT o.OBJECTID)           AS opened,
  COUNT(DISTINCT c.OBJECTID)           AS clicked
FROM V2_DAILY.EVENTS_SENT_EMAIL_V2 s
LEFT JOIN V2_DAILY.EVENTS_DELIVERED_EMAIL_V2 d
  ON d.OBJECTID = s.OBJECTID
  AND d.PROPERTY_HS_EMAIL_CAMPAIGN_ID = s.PROPERTY_HS_EMAIL_CAMPAIGN_ID
LEFT JOIN V2_DAILY.EVENTS_OPENED_EMAIL_V2 o
  ON o.OBJECTID = s.OBJECTID
  AND o.PROPERTY_HS_EMAIL_CAMPAIGN_ID = s.PROPERTY_HS_EMAIL_CAMPAIGN_ID
LEFT JOIN V2_DAILY.EVENTS_CLICKED_LINK_IN_EMAIL_V2 c
  ON c.OBJECTID = s.OBJECTID
  AND c.PROPERTY_HS_EMAIL_CAMPAIGN_ID = s.PROPERTY_HS_EMAIL_CAMPAIGN_ID
WHERE s.OCCURREDAT >= DATEADD('day', -7, CURRENT_DATE)
GROUP BY 1;
```

***

### 8. Critical gotchas and onboarding checks

These are the most common failure points encountered when querying HubSpot data in a data warehouse across any pipeline method.

<table><thead><tr><th width="248.0234375">Watch Out For</th><th>Detail</th></tr></thead><tbody><tr><td>Campaign ID mismatch (Native Data Share)</td><td>The OBJECTID in OBJECTS_CAMPAIGNS is different from PROPERTY_HS_EMAIL_CAMPAIGN_ID in event tables. HubSpot uses a separate internal content/asset ID. Always verify the join key before writing funnel queries.</td></tr><tr><td>Fivetran child tables must be enabled</td><td>EMAIL_EVENT only populates if the EMAIL_EVENT_* child tables are explicitly selected in the Fivetran connector's Schema tab. A connector set up without them will have an empty EMAIL_EVENT table and missing email data.</td></tr><tr><td>Fivetran 25-hour lookback</td><td>Fivetran re-fetches EMAIL_EVENT_* data 25 hours behind the current sync to catch HubSpot's delayed event processing. Expect some duplication in raw tables - use created as the dedup key.</td></tr><tr><td>Conversion is not a native event</td><td>HubSpot does not emit a 'converted' email event. Conversion must be self-defined: typically a deal created/updated, a form submission, or a purchase event within a time window after a click, joined on contact ID.</td></tr><tr><td>Native Data Share requires Ops Hub Pro+ and Snowflake</td><td>The HubSpot Native Data Share is only available to merchants on Operations Hub Professional or Enterprise <strong>and</strong> using Snowflake as their data warehouse. All other warehouse platforms require a third-party ETL connector.</td></tr><tr><td>Stitch requires Super Admin for email_events</td><td>Stitch specifically requires Super Admin permissions in HubSpot to replicate the email_events table. If the merchant's integration token was set up with a lesser role, email events will be missing.</td></tr><tr><td>Airbyte unified vs Fivetran sharded events</td><td>Airbyte consolidates all email event types into a single email_events table with a type column. Fivetran splits them into EMAIL_EVENT_SENT, EMAIL_EVENT_OPEN, etc. This changes the query pattern - know which pipeline you're on before writing SQL.</td></tr><tr><td>Metadata query syntax varies by warehouse</td><td>The discovery query <code>SHOW TABLES IN SCHEMA hubspot;</code> works in Snowflake. Use <code>INFORMATION_SCHEMA.TABLES</code> for BigQuery and Redshift (<code>SELECT table_name FROM information_schema.tables WHERE table_schema = 'hubspot'</code>). Athena uses Glue catalog; Databricks uses <code>SHOW TABLES IN hubspot</code>.</td></tr></tbody></table>

***

### 9. Onboarding decision matrix

At Sortment's end, this is how we determine what connection method applies and what to request access to.

<table><thead><tr><th width="276.6015625">If the merchant has...</th><th>Recommended path for Sortment read access</th></tr></thead><tbody><tr><td>HubSpot Ops Hub Pro+ <strong>and</strong> Snowflake as their data warehouse</td><td>Request access to their Native Data Share (V2_LIVE or V2_DAILY schema). Zero ETL infrastructure required, freshest data. <em>(Snowflake-only feature.)</em></td></tr><tr><td>Fivetran already running to their data warehouse</td><td>Confirm EMAIL_EVENT_* child tables are enabled. Ask for read access to the <code>hubspot</code> schema. If dbt_hubspot is running, prefer the mart models (<code>hubspot__email_campaigns</code> etc.).</td></tr><tr><td>Airbyte running to their data warehouse</td><td>Request read access to their Airbyte destination schema. Key tables: <code>email_events</code> (unified), <code>campaigns</code>, <code>marketing_emails</code>, <code>contacts</code>, <code>deals</code>.</td></tr><tr><td>Stitch running to their data warehouse</td><td>Request read access. Verify Super Admin was used for HubSpot auth (required for email_events). Key tables: <code>email_events</code>, <code>campaigns</code>, <code>contacts</code>, <code>deals</code>.</td></tr><tr><td>No ETL / no warehouse connection yet</td><td>Recommend Fivetran (most feature-complete for HubSpot marketing analytics) - it supports all major warehouse destinations. If they are on Snowflake with Ops Hub Pro+, the HubSpot Native Data Share is the fastest path with no ETL to manage. Fivetran dbt package gives you the cleanest analytics layer out of the box.</td></tr></tbody></table>

***

### Appendix: References

* [Fivetran HubSpot Connector Documentation](https://fivetran.com/docs/connectors/applications/hubspot)
* [Fivetran `dbt_hubspot` Package (GitHub)](https://github.com/fivetran/dbt_hubspot)
* [Airbyte HubSpot Connector Documentation](https://docs.airbyte.com/integrations/sources/hubspot)
* [Stitch HubSpot v4 Documentation](https://www.stitchdata.com/docs/integrations/saas/hubspot)
* [HubSpot Knowledge Base: Query HubSpot Data in Snowflake](https://knowledge.hubspot.com/reports/query-hubspot-data-in-snowflake)
* [HubSpot Knowledge Base: Connect Snowflake Data Share](https://knowledge.hubspot.com/reports/connect-snowflake-data-share)
* [HubSpot Developer Changelog: Snowflake Data Share Column Changes](https://developers.hubspot.com/changelog/snowflake-data-share-changes-to-columns-in-event-tables-and-views)
* [HubSpot Community: Snowflake Data Share ERD](https://community.hubspot.com/t5/128172-RevOps-Discussions/Snowflake-Data-Share-ERD/m-p/898513)
