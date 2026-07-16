# Marketo

Sortment enables you to seamlessly transfer customer data - including audiences and user traits - directly to Marketo. This guide outlines the process for integrating Sortment with Marketo, ensuring a secure and reliable connection between the two platforms.

### What you can sync to Marketo

Sortment supports syncing the following data to Marketo:

* **Audiences**: Audiences from Sortment can be synced as leads or static lists in Marketo.
* **User Properties:** User properties stored in your data warehouse are mapped and synced to Marketo lead fields.
* **User Traits:** Custom traits defined in Sortment can be synced to Marketo as custom fields or attributes.

### Connection configuration

To connect Sortment to Marketo, you need the following:

1. **Client ID:** Provided when you create a custom service in Marketo.
2. **Client Secret:** Also provided from your custom service setup in Marketo.
3. **Base URL:** Found in your Marketo Admin under Integration > Web Services.



**To set up Marketo integration with Sortment, follow these steps:**

1. In Marketo, create a API based role and an API Only User with the all API only permissions. Refer to Marketo’s documentation for instructions on creating an [API-based role](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user-role) and [assigning API role access to an email address](https://app.gitbook.com/o/CdalBLUjYzosXMRl8crP/s/mbOMKRXus6KHDbeQALkO/).
2. Custom services provide the credentials needed to authenticate Marketo with Sortment. To generate your Client ID and Client Secret:
   1. Go to Admin > LaunchPoint and select “New Service.”
   2. Provide a descriptive name, select “Custom” from the service list, and choose the API Only User you created earlier.
   3. Click “Create.”
3. After creating the service, note down the Client ID and Client Secret from the LaunchPoint service details.
4. To find your base URL, navigate to Admin > Integration > Web Services under REST API. Use only the part of the URL that comes after `https://` and before `/rest` as your base URL.

### How to connect

1. In Sortment, navigate to Integrations → Add Destination and select Marketo.
2. Enter your Marketo Client ID, Client Secret, and Base URL.
3. Click Connect.

Sortment will verify your credentials and establish a secure connection to your Marketo account. Once connected, you can begin syncing data directly into your Marketo workspace.

### Matching records in Marketo

You can match records in Marketo using either the lead’s Email or Marketo GUID. The appropriate identifier depends on your Marketo setup and use-case. For custom objects, you can match using dedupe fields as configured in your Marketo instance.

**Automated Field Creation:** If a required field or custom attribute doesn’t exist in Marketo, Sortment will create it with the correct data type and format.

### Field mapping

Sortment allows you to map user attributes and traits from your workspace to corresponding Marketo fields. Ensure that your data types match the target fields in Marketo for seamless syncing.<br>

### Need help?

For assistance, please reach out to our support team at [support@sortment.com](mailto:support@sortment.com).
