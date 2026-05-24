# Iterable

Sortment allows you to seamlessly send customer data - including audiences and traits – directly into Iterable. This guide walks you through the steps to set up the Sortment + Iterable integration, ensuring a smooth and reliable connection between platforms.

### What you can sync to Iterable

Sortment supports sending the following data to Iterable:

* **Audiences:** Synced as static lists into Iterable.
* **User Properties:** Sync user properties from the warehouse directly. These get auto-mapped and synced into Iterable user fields.
* **User Traits:**  Custom traits defined on Sortment can be synced to Iterable as user fields.

***

## Connection configuration

To connect Sortment to Iterable, you need the following:

1. **Iterable API Key:** A server side API Key
2. **Project Type Identifier:** Available in your Iterable account under `Settings -> Project Settings`&#x20;

For detailed instructions on generating an API Key and understanding your Project Type Identifier, please refer to Iterable’s [ API Key Guide](https://support.iterable.com/hc/en-us/articles/360043464871-API-Keys-#creating-api-keys) and [Project Type Identifier](https://support.iterable.com/hc/en-us/articles/9216719179796#checking-the-unique-identifier-for-a-project) documentation.

{% hint style="info" %}
We recommend creating a **dedicated Iterable API key** for Sortment, with a clear name and appropriate scopes to ensure security and ease of management.

* The API key should have [**server-side permissions**](https://support.iterable.com/hc/en-us/articles/360043464871-API-Keys-#server-side-keys) to support syncing with sortment.
{% endhint %}

### How to connect

1. In Sortment, navigate to **Integrations** → **Add Destination,** then select **Iterable**.
2. Enter your **Iterable API Key** and **Project Identifier**.
3. Click **Connect**.&#x20;

Sortment will verify your credentials and securely connect to your Iterable account. Once completed, you can start syncing data directly into your Iterable project.

### Matching audience in Iterable

You can match audiences in Iterable using either:

* **Email**
* **User ID**

Pick the relevant identifier based on your Iterable project type (email-based, userID-based, or hybrid). Whenever possible, we recommend matching by **User ID** for greater consistency and to ensure a one-to-one mapping across systems.

**Automated Field Creation:** If a user field doesn’t exist in Iterable, Sortment will automatically create it with the correct data type.

### Need help?

For assistance, please reach out to our support team at [support@sortment.com](mailto:support@sortment.com).
