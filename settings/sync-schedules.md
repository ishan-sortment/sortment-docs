# Sync Schedules

Sync schedules in Sortment control **how often data is refreshed** from your data warehouse for journey-related use cases. This ensures your segmentation, personalization, and analytics remain accurately available across all communications.

***

#### 5.1 Overview

* Sync Schedules are available under **Workspace Settings → Sync Schedules**
* They define the **frequency and time** when user properties are automatically synced from integrated data sources.
* You can choose between **Daily**, **Weekly**, or **Monthly** syncs, and configure the exact time and date.
* The system time zone is displayed (e.g., IST UTC+05:30), ensuring clarity across teams.

***

#### 5.2 How to Modify a Sync Schedule

1. Go to **Workspace Settings → Sync Schedules**
2. Click **Edit** next to “User Properties Sync”
3. In the pop-up:
   * Select frequency: `Daily`, `Weekly`, or `Monthly`
   * Choose specific day (if applicable)
   * Set the desired time
4. Click **Save** to apply the schedule

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

***

#### 5.3 Best Practices

* **Align sync times** with your data warehouse refreshes (e.g., after daily ETL jobs complete)
* Avoid scheduling during peak business hours to minimize API load or warehouse strain
