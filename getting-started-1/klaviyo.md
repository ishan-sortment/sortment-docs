# Klaviyo

Sortment allows you to seamlessly sync customer data - audiences and traits - directly into Klaviyo. This guide walks you through the steps to set up the Sortment + Klaviyo integration, ensuring a smooth and reliable connection between platforms.

### What you can sync to Klaviyo

Sortment supports sending the following data to Klaviyo:

* **Audiences:** Synced as lists in Klaviyo. Users can be added to or removed from Klaviyo lists. Sortment can create new lists in Klaviyo as needed.
* **User Properties**: Sync user properties directly from the warehouse. These properties are mapped in Klaviyo as both custom and Klaviyo properties.
* **User Traits:** Traits defined in Sortment are synced to Klaviyo as custom properties

### Connection configuration

To connect Sortment to Klaviyo, you will need the following:

**Klaviyo Private API Key:** Create a private API key in your Klaviyo account with permissions to read and write Profiles and Lists.

<figure><img src="../.gitbook/assets/New Sortment Key 1.png" alt=""><figcaption></figcaption></figure>

**To generate your API key:**

1. Go to the [API Keys page](https://www.klaviyo.com/settings/account/api-keys) in your Klaviyo account.
2. Create a new private API key.
3. Ensure the key has permissions to read/write access to both List and Profiles.

### How to connect

1. In Sortment, navigate to Integrations → Add Destination, then select Klaviyo.
2. Enter your Klaviyo Private API Key
3. Click Connect.

Sortment will verify your credentials and securely connect to your Klaviyo account. Once completed, you can start syncing data directly into your Klaviyo workspace.

### Matching records in Klaviyo

Records can be matched to Klaviyo users using one of the following identifiers:

* Email
* Phone Number
* Klaviyo Unique ID

Whenever possible, we recommend matching by **Unique ID** for greater consistency and to ensure a one-to-one mapping across systems.

**Automated field creation:** If a custom property doesn’t exist in Klaviyo, Sortment will automatically create it with the correct data type.

### Need help?

For assistance, please reach out to our support team at [support@sortment.com.](mailto:support@sortment.com)
