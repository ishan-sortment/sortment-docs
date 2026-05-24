# Azure Blob Storage for Snowflake

As discussed in [cloud storage setup](./), Azure Blob Storage is required for several data-related use cases in Sortment.

## Connection configuration

The following details are required on Sortment for Azure Blob Storage connection with Snowflake:

* **Azure storage account name:** The unique name assigned to your Azure storage account. Locate this on the Azure Portal → Storage Accounts → Select your storage account.
* **Azure blob container name:** A container within the Azure storage account used to store and retrieve data. Azure Portal → Storage Accounts → Select your account → Containers → Identify or create your container.
* **Storage account access key:** A key providing access to your Azure storage resources. Azure Portal → Storage Accounts → Select your account → Security + networking → Access keys → Copy one of the available keys.
* **Snowflake stage name:** A specific stage to read and write data between Snowflake and Azure Blob Storage. Follow the [steps below](azure-blob-storage-for-snowflake.md#creating-stage-in-snowflake) to create this stage, using the name `sortment`.

## Azure credentials setup

Follow these steps to set up Azure Blob Storage for Sortment:

### Creating a storage account

1. Sign in to the [Azure Portal](https://portal.azure.com/).
2. Click "Create a resource" → Search for "Storage account" → Click "Create."
3. Enter a unique storage account name, select your subscription, resource group, and region matching your Snowflake instance region.
4. Review and create the storage account.

### Creating a blob container

1. Navigate to your newly created storage account.
2. Click on "Containers" under "Data Storage."
3. Click "+ Container," name your container (e.g., `sortment`), and set the public access level to "Private."
4. Click "Create."

### Retrieving access keys

1. Go to your storage account on Azure Portal.
2. Under "Security + networking," click on "Access keys."
3. Copy the "Storage account name" and one of the available "Key" values.

## Creating stage in snowflake <a href="#creating-stage-in-snowflake" id="creating-stage-in-snowflake"></a>

After obtaining your Azure credentials, create a stage in Snowflake to finalize your Blob Storage connection:

{% hint style="warning" %}
Ensure the stage name is set as `sortment`.
{% endhint %}

```sql
-- Set variables
set azure_account='REPLACE_WITH_YOUR_STORAGE_ACCOUNT';
set azure_container='sortment';
set azure_sas_token='REPLACE_WITH_YOUR_STORAGE_ACCOUNT_KEY';
set smt_default_role='SORTMENT_ROLE';

-- Set role for grants
USE ROLE identifier($smt_default_role);

-- Create stage for Sortment
CREATE OR REPLACE STAGE sortment
  URL='azure://' || $azure_account || '.blob.core.windows.net/' || $azure_container
  CREDENTIALS=(AZURE_STORAGE_ACCOUNT_KEY=$azure_sas_token)
  file_format = (type = csv field_optionally_enclosed_by='"' compression = none);
```

### Setting up the credentials

Use the credentials generated above to connect Sortment to your Azure Blob Storage container and proceed.
