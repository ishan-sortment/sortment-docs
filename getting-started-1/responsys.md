# Responsys

Sortment enables you to seamlessly transfer customer data including audiences, traits, and user attributes directly to Oracle Responsys. This guide outlines the process for integrating Sortment with Responsys, ensuring a secure and reliable connection between the two platforms.

### What you can sync to Responsys

Sortment supports syncing the following data to Responsys:

* **Audiences:** Audiences are synced as segment groups in Responsys.
* **Traits:** Custom traits defined in Sortment are mapped to custom fields or attributes in Responsys.
* **User Attributes:** User attributes stored in your data warehouse are mapped and synced to Responsys profile fields or profile extension tables.

### Connection configuration

To connect Sortment to Responsys, you need the following:

1. **Responsys Credentials:** Obtain your Responsys username and password with API access.
2. **Host URL:** The Oracle system URL that hosts your Responsys account. To find your host URL refer to [Oracle Responsys documentation](https://docs.oracle.com/en/cloud/saas/marketing/responsys-rest-api/SendRequests.html).

**To set up Responsys integration with Sortment, follow these steps:**

1. In Responsys, ensure your user account has the necessary permissions to create and update profiles and profile extension tables via the API.
2. Gather your Responsys login credentials and host URL.

### How to connect

1. In Sortment, navigate to **Integrations → Add Destination** and **select Responsys.**
2. Enter your Responsys username, password, and host URL.
3. Click Connect.

Sortment will verify your credentials and establish a secure connection to your Responsys account. Once connected, you can begin syncing data directly into your Responsys workspace.

### Matching records in Responsys

You can match records in Responsys using any of the following fields:

* Email
* Mobile number
* Customer ID
* Responsys ID (RIID)

For profile extension tables, matching is supported on the same set of fields.

#### Field mapping

Sortment allows you to map user attributes and traits from your workspace to corresponding Responsys fields. Ensure that your data types match the target fields in Responsys for seamless syncing.&#x20;

#### Automated Field Creation

If a required field or custom attribute doesn’t exist in Responsys, Sortment will attempt to create it with the correct data type and format where supported.

####

### Need help?

For assistance, please reach out to our support team at [support@sortment.com](mailto:support@sortment.com).
