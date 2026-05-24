# Audit Logs

Companies require action tracking for users to comply with **Information Security (InfoSec)** policies. Since users of Sortment interact with customer data, it is crucial to maintain an audit history across all entities that can be created, modified, or deleted within Sortment.

### Tracking Scope

For every change, Sortment captures:

* **Who** performed the action
* **When** the action occurred
* **What Resource** was affected
* **What Change** was made

{% hint style="info" %}
This is available in Workspace settings under Audit logs tab.
{% endhint %}

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

#### **Metadata Logging**

The metadata is saved with the action, to track the updated payload. Comparison between consecutive logs' metadata allows understanding of exact change that was made. Metadata logs are available for acces on request from Sortment team.

### **Filtering Logs**

Users can filter logs based on specific entities and actions. The filters support:

* Viewing logs for particular entities (e.g., **Audiences, Campaigns, Journeys**)
* Filtering by time window when they happened (e.g., **Last 7 days, Last 90 days**)

### **Managed Changes Across Entities**

| Entity                | Actions                                                                                                         |
| --------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Schema Management** | Add to schema, Update relationship, Delete table                                                                |
| **Audiences**         | Create audience, Update audience, Create run, Update run, Delete run                                            |
| **Campaigns**         | Create campaign, Update campaign (including recurring campaigns)                                                |
| **Templates**         | Create template, Update template, Delete template                                                               |
| **Journeys**          | Create journey, Update journey                                                                                  |
| **Custom Properties** | Create custom property                                                                                          |
| **Settings**          | Manage Data connection, Blob storage, Channels, Subscription groups, Delivery controls (Create, Update, Delete) |
