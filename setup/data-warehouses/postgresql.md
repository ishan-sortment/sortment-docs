# PostgreSQL

Sortment does not directly support PostgreSQL as a data source. In case you don't have a data warehouse, you will need to setup a sync between your PostgreSQL to a data warehouse of your choice. This document outlines different approaches and the best practices for setting up an automated ETL pipeline.

## Choosing the right method for ETL

There are several ways to setup data pipeline from PostgreSQL, but we've covered the two most common ones here:

### **Option 1: Using Managed ETL Tools (No-Code/Low-Code)**

If you prefer a managed solution with minimal engineering effort, this is the preferred approach. If your data volume is low, this is a cost effective way to get your pipeline up and running quickly. You can use any of the following tools:

| **Tool**                  | **Pricing Model**        | **Pros**                                   | **Cons**                       |
| ------------------------- | ------------------------ | ------------------------------------------ | ------------------------------ |
| **Airbyte (Self-hosted)** | Free (infra costs apply) | Open-source, customizable                  | Requires engineering effort    |
| **Stitch**                | $100/month (10M rows)    | Easy setup, cost-effective for small-scale | Limited connectors, batch only |
| **Hevo**                  | $249/month               | Real-time sync, no maintenance             | Costs rise with volume         |
| **Fivetran**              | $500+/month              | Fully managed, enterprise-grade            | Most expensive option          |

These tools handle incremental syncs, schema changes, and monitoring automatically, but can be costly if the data volume is huge.

#### Best Practices

* **Use Incremental Syncs:** Avoid full data loads to optimize costs and performance.
* **Monitor Data Pipeline:** Set up logging and alerts for failures.
* **Optimize Storage Costs:** Use compressed formats like Parquet.
* **Schema Evolution:** Ensure the ETL tool can handle schema changes automatically.



### Option 2: Cloud-native Solution (Engineering required)

For a fully managed and scalable data pipeline, cloud-native ETL solutions offer a reliable way to migrate PostgreSQL data to Redshift or BigQuery. We have linked respective documentations for migrating data from PostgreSQL to cloud data warehouses.

* AWS Database Migration Service into Redshift ([Guide](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Target.Redshift.html))
* BigQuery Data Transfer Service ([Guide](https://cloud.google.com/bigquery/docs/dts-introduction))

#### Best Practices

* **Use Incremental Loading:** Reduce costs by syncing only changed data.
* **Monitor & Alert:** Set up monitoring via CloudWatch (AWS) or Stackdriver (GCP).
* **Optimize Storage:** Use Parquet or Avro for efficient processing.
* **Automate Schema Evolution:** Ensure schema changes don’t break the pipeline.

### &#x20;Support

If you need help with choosing what is the best option for your company, feel free to reach out to ishan@sortment.com

