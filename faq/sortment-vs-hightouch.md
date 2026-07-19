# Sortment vs. Hightouch

Sortment and Hightouch both connect to your data warehouse, but they solve different problems. Hightouch is a reverse ETL tool built to sync warehouse data into downstream business tools. Sortment is a customer engagement platform built to activate warehouse data directly into marketing campaigns, journeys, and AI-driven audience workflows — without needing a separate engagement tool on top.

This page breaks down the core differences to help you decide which fits your use case.

## Core Positioning

**Hightouch** is a data activation / reverse ETL platform. It moves data from your warehouse into SaaS tools (CRMs, ad platforms, support tools, etc.) so those tools can act on it. Hightouch itself doesn't send emails, SMS, WhatsApp messages, or push notifications — it hands data off to other systems that do.

**Sortment** is a full customer engagement platform that runs natively on your data warehouse. It builds audiences, orchestrates multi-channel campaigns and journeys, and sends messages directly — while also using AI to help marketers build audiences, campaigns, and templates without needing SQL or engineering support for every request.

In short: Hightouch gets your data to other tools. Sortment gets your data to your customers.

## Where They Differ

| | Sortment | Hightouch |
|---|---|---|
| **Primary function** | Customer engagement platform (audiences, campaigns, journeys) | Reverse ETL / data activation |
| **Sends messages directly** | Yes — Email, SMS, WhatsApp, Push, and more | No — syncs data to third-party tools that send messages |
| **Journey / campaign orchestration** | Built-in journey builder, campaign builder, delays, flow control | Not available — requires a separate engagement tool |
| **AI-assisted workflows** | AI audience creation, AI email templates, AI-assisted data editing | Not a core focus |
| **Audience building** | No-code audience builder, SQL builder, calculated & dynamic attributes | Audience/cohort definitions primarily for syncing to destinations |
| **Warehouse-native** | Yes — Snowflake, BigQuery, Redshift, Databricks, Athena, PostgreSQL | Yes — Snowflake, BigQuery, Redshift, Databricks, and others |
| **Best fit** | Marketing teams who want to build and send campaigns straight from warehouse data | Data teams who want to pipe warehouse data into existing downstream SaaS tools |

## When to Use Which

Use **Hightouch** if you already have a marketing/engagement tool (or several) and just need a reliable way to keep them in sync with your warehouse.

Use **Sortment** if you want your data warehouse to be the source of truth *and* the engine behind your actual customer communications — audiences, campaigns, journeys, and AI-assisted workflows in one platform, with no separate destination tool required.

{% hint style="info" %}
Some teams use both: Hightouch to sync warehouse data into internal tools like CRMs, and Sortment to handle customer-facing engagement (email, SMS, WhatsApp, push) directly from the same warehouse.
{% endhint %}

## Related Reading

- [Core Concepts](../getting-started/core-concepts.md)
- [Audiences](../engage/audiences/README.md)
- [Campaigns Overview](../engage/campaigns/overview.md)
