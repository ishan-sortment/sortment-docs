# MoEngage

Sortment enables you to efficiently transfer customer data - including audiences and traits - directly to MoEngage. This guide outlines the process for integrating Sortment with Moengage, ensuring a seamless and reliable connection between the two platforms.

### What you can sync to MoEngage

Sortment supports syncing the following data to MoEngage:

* **Audience:** Audiences from Sortment are synced as customers in MoEngage.
* **User Properties:** User properties stored in your data warehouse are automatically mapped and synced as MoEngage user attributes.
* **User Traits:**  Custom traits defined in Sortment can be synced to MoEngage as user attributes. These traits are formatted in snake\_case. For example, “Active Uber Black Riders” will be converted to “active\_uber\_black\_riders” before being transferred to MoEngage.

### Connection configuration

To connect Sortment to MoEngage, you need the following:

1. **MoEngage Data API Key:** Data API Key helps us in sending user details from Sortment to MoEngage servers.
2. **MoEngage Workspace ID:** Workspace ID helps us identify the workspace account in MoEngage.

**To generate your API token from MoEngage:**

1. Navigate to  [API Setting page](https://dashboard-01.moengage.com/v3/#/settings/api/general) in your MoEngage account.
2. Copy the following details:
   * Workspace ID: Under **Workspace ID**, click the copy icon to copy the username.
   * Data API Key: In the **API keys** section, click the copy icon in the **Data** tile to copy the API key.



<figure><img src="../.gitbook/assets/image (144).png" alt=""><figcaption></figcaption></figure>

For detailed instructions on generating a Data API Key and finding your Data API ID, please refer to [MoEngage’s API documentation](https://developers.moengage.com/hc/en-us/articles/4404674776724-Overview#01H815VFPB3Y06MX539856QSK4).

### How to connect

1. In Sortment, navigate to **Integrations → Add Destination** and select **MoEngage.**
2. Enter your MoEngage Data API Key and Data API ID.
3. Click **Connect.**

Sortment will verify your credentials and securely connect to your MoEngage account. Once completed, you can start syncing data directly into your MoEngage workspace.

### Matching customers in MoEngage

You can match customers in MoEngage using the customer\_id. The distinct\_id for users created on Sortment is mapped to the customer\_id in MoEngage.

**Automated Field Creation:** If a user field or custom attribute doesn’t exist in MoEngage, Sortment will automatically create it with the correct data type and format.

### Field mapping

Sortment enables you to map user attributes and traits from the Sortment workspace to MoEngage. Custom attributes are synced as additional properties in ‎⁠snake\_case⁠ format.<br>

### Need help?

For assistance, please reach out to our support team at  [support@sortment.com.](mailto:support@sortment.com)
