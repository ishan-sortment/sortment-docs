# Hubspot

Sortment lets you push customer data from your data warehouse into **HubSpot**, so your CRM, email marketing, and automation stay in sync.

> 📢 **Note:** HubSpot doesn’t support syncing pre-built audience lists directly. Instead, detailed user information and custom traits are synced in HubSpot, enabling you to build dynamic audiences (Active Lists) directly inside HubSpot.

***

### 1. What you can send to HubSpot

* **User Properties:** Primary customer data like name, email, phone number, etc., pulled from your data warehouse. You can send this to HubSpot, where it's added as **Contact property**.
* **Custom traits:** Fields you define from raw data like "Customer Lifetime Value (CLV) Tier" or "Engagement Level" in Sortment. These become **custom properties** in HubSpot.
* **Data for lists and segments:** With detailed user info and calculated traits, Sortment gives HubSpot everything it needs to create dynamic lists and automated workflows.

***

### 2. Setting up your connection

To connect Sortment with HubSpot, you'll need:

* **Private App Access Token** → [How to create a Private App in HubSpot](https://developers.hubspot.com/docs/api/private-apps)
  * &#x20;Required permissions: \
    `crm.objects.contacts.write` \
    `crm.objects.contacts.read`\
    `crm.objects.contacts.write`\
    `crm.objects.companies.read`\
    `crm.objects.companies.write`

> 💡 Tip: Create a dedicated app (e.g., “Sortment Sync App”) and limit access only to what’s needed.

***

### 3. How to connect and sync data

Sortment gives you two ways to send data to HubSpot:

#### 3.1 Direct integration setup

Use this if you want to send contact data at a set frequency without building a journey.

* Go to **Integrations → Add Destination** in Sortment
* Select **HubSpot**
* Paste your **Private App Access Token**
* Click **Connect**
* Choose the data and sync frequency (daily, weekly, etc.)

#### 3.2 Use Sortment journeys with HubSpot connector

Use this for more advanced syncing where you want full control over what’s sent and when.

* Create a **Journey** in Sortment with a valid trigger event.
* Add a **HubSpot API Connector step** inside the journey.
* Add your source data – such as users and traits – from your data warehouse.
* Use the following API endpoint:
  * `POST /crm/v3/objects/contacts/{contactId}`&#x20;
  * Follow the [HubSpot Contacts API Docs](https://developers.hubspot.com/docs/api/crm/contacts) to create the complete URL for your account
* Map the fields (email, name, traits) to HubSpot’s format in the payload.&#x20;
* Set your schedule – daily, weekly, etc. The journey will run automatically and sync fresh data to Hubspot.

***

### 4. How contacts are matched in HubSpot

Contacts are matched using **Email address** (recommended default)

If the email exists, HubSpot updates the contact. If it doesn’t, a new contact is created.

HubSpot automatically creates any new properties it sees in the sync from Sortment.

***

### 5. Verifying data and using it in HubSpot

Once a sync is complete:

* **View contact profiles:** Search by email in HubSpot and check the **Contact properties** tab
* **Lists and segments:** Use traits like “Engagement Level” to build lists
* **Workflows:** Trigger campaigns based on customer attributes from Sortment. &#x20;
* **Reports:** Analyze revenue, LTV, or engagement using your custom traits
