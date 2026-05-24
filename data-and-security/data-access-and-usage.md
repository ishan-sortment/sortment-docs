# Data Access And Usage

1.  **How does Sortment manage my data in the warehouse and for event triggered messages?**\
    Sortment connects to your warehouse and builds a schema view of the tables. These tables are used to create audiences and send campaigns with your existing app.\
    For event triggered campaigns, it connects to your app or existing event collection apps like Segment, Rudderstack and sends users personalised messages. For this, personalization variables are cached so that warehouse is ont queried everytime a message is sent.<br>

    <figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>
2. **How do you handle audience-based campaigns in the warehouse?**\
   For audience-based campaigns, a single query is executed at the time of audience creation within the warehouse. When a campaign is to be sent, a query is run on the warehouse to get personalization variables for the users.
3. **Do you maintain a single table for the entire campaign or multiple tables?**\
   Sortment operates with a single table for all campaign data unless specified otherwise.
4. **How are real-time journey events processed?**\
   Real-time journey events are processed directly on our servers and do not interact with the warehouse. For these events, we integrate seamlessly with the client’s application or event collection tools such as Segment or Rudderstack.
5. **Does every event trigger require querying the entire campaign table in the warehouse?**\
   No, when an event is triggered, it does not require querying the entire campaign table in the warehouse.
6. **Are queries run on the warehouse for each event trigger?**\
   No, queries are not run on the warehouse for every event trigger. We maintain a cache of user profile outside warehouse to reduce querying costs&#x20;
7. **How are events sent to the warehouse for campaign analytics?**\
   For campaign analytics, events are batched and sent to the warehouse at regular intervals using a configurable cron job. The default setting is one query per hour, which can be adjusted to once per day, depending on the client’s needs.
8. **Does processing campaign data for a large user table result in high data volumes daily?**\
   No, assuming campaigns are processed once daily, the data volume processed is only proportional to the size of the campaign data, not the total user base. For example, with a 500,000-user table, only 0.5 GB of data would be processed daily.
9. **How does querying old campaign data impact costs?**\
   Querying older campaign data could impact costs due to the potential size of the event tables. However, employing best practices such as partitioning by campaign and timestamp can significantly reduce the volume of data that needs to be processed.
10. **What are the best practices for managing campaign data in the warehouse?**\
    To optimize performance and minimize costs, Sortment recommends partitioning campaign data by campaign and timestamp. This approach ensures efficient querying and reduces the overall data processed for campaign analytics.
