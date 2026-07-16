# Query Logs Access Configuration

To read query history from Sortment, the connected warehouse role or service account needs additional permissions beyond standard read access, depending on the warehouse.

## **BigQuery**

To read query history from `INFORMATION_SCHEMA.JOBS*` views, you'll additionally need one of:

* BigQuery Resource Viewer (`roles/bigquery.resourceViewer`) — can view metadata about jobs.
* A custom role containing:
  * `bigquery.jobs.listAll`
  * `bigquery.jobs.get`
  * `bigquery.jobs.list`

The key permission is usually `bigquery.jobs.listAll`, which allows viewing jobs run by other users in the project.

## **Snowflake**

To access query history, the role additionally needs access to:

* `SNOWFLAKE.ACCOUNT_USAGE.QUERY_HISTORY` or `INFORMATION_SCHEMA.QUERY_HISTORY`

This is typically granted through:

* `MONITOR` privilege on the account or warehouse
* Or one of the built-in roles:
  * `ACCOUNTADMIN`
  * `SECURITYADMIN` (depending on scope)
  * `MONITOR USAGE`

## **Athena**

To access query history, the principal needs the following Athena permissions:

* `athena:ListQueryExecutions`
* `athena:GetQueryExecution`
* `athena:GetQueryResults`
* `athena:BatchGetQueryExecution`

Access to the Athena workgroups whose history you want to inspect is also required.

Example IAM policy:

json

```json
{
  "Action": [
    "athena:ListQueryExecutions",
    "athena:GetQueryExecution",
    "athena:GetQueryResults",
    "athena:BatchGetQueryExecution"
  ],
  "Effect": "Allow",
  "Resource": "*"
}
```
