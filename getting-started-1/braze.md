# Braze

Sortment lets you push customer data from your data warehouse into Braze, so your messaging, segmentation, and personalization stay in sync.

📢 **Note:** Braze doesn’t support syncing pre-built audience lists directly. Instead, Sortment syncs detailed user information and custom traits into Braze, enabling you to build dynamic (always updating) segments within Braze itself.

***

### 1. What you can send to Braze

* **User Properties:** Core customer data like `external_id`, email, phone number, etc., pulled from your data warehouse. This gets added to Braze user profiles.
* **Custom Traits:** Fields you define from raw data in Sortment—such as “Customer Lifetime Value (CLV) Tier” or “Engagement Score.” These are sent as custom attributes in Braze.
* **Data for Segments:** With user info and traits available, you can create and manage dynamic segments and trigger personalized campaigns in Braze.

***

### 2. Setting up your connection

To connect Sortment with Braze, you'll need:

* **Braze REST API Key** with permission: `users.track` →  Braze's official [API Key Guide](https://www.braze.com/docs/api/basics/#braze-rest-api-collection).&#x20;
* **Braze REST Endpoint URL** → Take a look at the [Braze Instances documentation](https://www.google.com/search?q=https://www.braze.com/docs/api/basics/%23braze-instances).

{% hint style="info" %}
Create a dedicated key (e.g., “Sortment Sync Key”) and limit access only to what’s needed.
{% endhint %}

***

### 3. How to connect and sync data

Sortment gives you two ways to send data to Braze:<br>

**3.1 Direct integration setup**

* Go to **Integrations → Add Destination** in Sortment
* Select **Braze**
* Paste your API Key and Endpoint URL
* Click **Connect**
* Choose the data and sync frequency (hourly, daily, etc.)<br>

**3.2 Use Sortment journeys with the Braze connector**

* Create a **Journey** in Sortment with a valid trigger event
* Add a **Braze API Connector** step inside the journey
* Add your source data — such as users and traits — from your warehouse
* Use the following API endpoint:\
  `POST /users/track` → Braze [doc for reference](https://www.braze.com/docs/api/endpoints/user_data/post_user_track)&#x20;
* Map the fields (`external_id`, traits, etc.) to Braze’s expected JSON format
* To avoid creating new users, include this flag:\
  `"update_existing_only": true`
* Set the schedule daily, weekly, etc. and the journey will sync the data automatically.

***

### 4. How users are matched in Braze

Braze matches users using one of:

* `external_id` (recommended)
* Email
* Phone number

If a matching user exists, Braze updates the profile. If not, a new one is created. Braze also auto-creates new custom fields if they don’t already exist.

***

### 5. Verifying data and using it in Braze

Once a sync is complete:

* **View user profiles:** Log in to Braze and search by `external_id`, email, or phone number. Check the **Custom Attributes** section for synced traits.
* **Create segments:** Use synced traits like “Engagement Score” or “CLV Tier” to define dynamic audiences.
* **Trigger campaigns:** Leverage traits in personalization rules or campaign workflows.
* **Analyze:** Use the synced data in Braze reports to track behavior, value, and engagement.
