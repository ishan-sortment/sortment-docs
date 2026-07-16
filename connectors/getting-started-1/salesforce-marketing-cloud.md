# SalesForce Marketing Cloud

Sortment enables you to seamlessly transfer customer data including audiences and user traits directly to Salesforce Marketing Cloud (SFMC). This guide outlines the process for integrating Sortment with SFMC, ensuring a secure and reliable connection between the two platforms.

### What you can sync to Salesforce Marketing Cloud

Sortment supports syncing the following data to SFMC:

* **Audiences:** Audiences from Sortment can be synced as contacts or Data Extensions in SFMC.
* **User Properties:** User properties stored in your data warehouse are mapped and synced to SFMC contact fields or Data Extension fields.
* **User Traits:** Custom traits defined in Sortment can be synced to SFMC as custom fields or attributes.

### Connection configuration

To connect Sortment to Salesforce Marketing Cloud, you need the following:

1. **Client ID:** Provided when you create an installed package in SFMC.
2. **Client Secret:** Also provided from your installed package setup in SFMC.
3. **Subdomain:** Found in your SFMC Admin under the Authentication base URI (the part after ‎`https://` and before ‎`.auth.marketingcloudapis.com/`).

#### How to get Client ID and Client Secret

To obtain the Client ID and Client Secret from SFMC, follow these steps:

1. Log in to your SFMC instance. **Go to Setup.**
2. In the left sidebar, **navigate to Apps** then **Installed Packages** and **click New.**
3. Name your package (for example, “Sortment Integration”) and optionally provide a description. Click Save.
4. Click **Add Component** and **select API Integration** as the component type. Click Next.
5. **Select** **Server-to-Server** as the integration type and **click Next**.

#### Permissions

Make sure to provide the following permissions for the integration:

* **Contacts -> List and subscribers**: Read and Write
* **Data -> Data Extensions:** Read and Write
* **Provisioning -> Accounts:** Read

1. After saving, you will see your new API Integration component in the package details. Copy the Client ID and Client Secret from here.
2. Find your Subdomain in the Authentication base URI (the part after ‎`https://` and before ‎`.auth.marketingcloudapis.com/`).

### How to connect

1. In Sortment, navigate to **Integrations** → **Add Destination** and select **Salesforce Marketing Cloud.**
2. Enter your SFMC Client ID, Client Secret, and Subdomain.
3. Click Connect.

Sortment will verify your credentials and establish a secure connection to your SFMC account. Once connected, you can begin syncing data directly into your SFMC workspace.

### Matching records in SFMC

You can match records in SFMC using either the **Contact Key** or **primary key** of the Data Extension, depending on your setup and use-case. For custom objects or Data Extensions, you can match using the primary key as configured in your SFMC instance.

**Automated Field Creation:** If a required field or custom attribute doesn’t exist in SFMC, Sortment will create it with the correct data type and format.

### Field mapping

Sortment allows you to map user attributes and traits from your workspace to corresponding SFMC fields. Ensure that your data types match the target fields in SFMC for seamless syncing.

### Need help?

For assistance, please reach out to our support team at [support@sortment.com](mailto:support@sortment.com).
