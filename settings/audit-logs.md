# Audit Logs

Audit Logs in Sortment provide a detailed, transparent history of user actions across the workspace. They are essential for **governance, security, troubleshooting, and collaboration**, offering visibility into who changed what, and when.

***

#### 6.1 What is Logged and Why It Matters

Sortment automatically logs actions performed by users, including:

* **Created**: New items like campaigns, audiences, traits
* **Updated**: Changes to configurations or logic
* **Deleted**: Removal of assets
* **Accessed** _(if applicable)_: Viewing sensitive sections

Each log entry includes:

* **Timestamp** of action
* **User** who performed it
* **Action type** (create, update, delete)
* **Resource type** (e.g., Campaigns, Audiences)
* **Resource name** for direct reference

&#x20;**Why it matters:**

* Enables **change tracking** for compliance and audits
* Helps **debug issues** like misconfigured traits or campaigns
* Improves **team accountability** in collaborative environments

***

#### 6.2 Navigating Audit Logs

To view Audit Logs:

1. Go to **Workspace Settings → Audit Logs**
2. Logs are displayed in a table, sorted by **most recent**
3. You’ll see:
   * **Date/Time**
   * **User**
   * **Action**
   * **Resource Type** (e.g., Campaigns, Audiences)
   * **Resource Name** (with link, if applicable)

Each row is clickable for deeper inspection or traceability when troubleshooting.

***

#### 6.3 Filtering by User, Date, or Event Type

To quickly locate specific actions:

* Use the **search bar** to filter by resource name
* Use the **User dropdown** to filter actions by individual users
* Use the **Resource Type filter** (e.g., “Campaigns” or “Audiences”)
* Filter by **timeframe** using the top-right filter (e.g., Last 7 days, All time)

💡 **Pro Tip:** Use filtering during team handovers or incident reviews to track recent changes made by others.
