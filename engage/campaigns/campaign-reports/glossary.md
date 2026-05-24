# Glossary

### General concepts

* **Campaign Report**\
  A summary view showing performance metrics for campaigns or journeys over a selected date range.
* **Filter Block**\
  Allows segmentation of campaign analytics by specific criteria (e.g., geography, user segment).
* **Chart Type**\
  The visual format of data—e.g., **bar chart**, **line chart**.
* **Count Type**\
  Determines how metrics are displayed:
  * **Absolute**: Raw numbers
  * **Percentage**: Values as a percent of total
* **Frequency vs. Cumulative Chart**
  * **Frequency**: Shows data in time-based slices (e.g., daily opens).
  * **Cumulative**: Aggregates totals over time (e.g., total opens to date).
* **Time Axis Control**\
  Lets users change the granularity of time in visualizations:\
  `Minute | Hourly | Daily | Weekly | Monthly`
* **Total Metrics**\
  Count each action occurrence, regardless of who performs it or how often.
* **Unique Metrics**\
  Count unique users (based on userId) who perform an action, only once per user.
* **Rate Metrics**\
  Represent engagement as a percentage of eligible users or actions (e.g., clicks as % of opens).

***

### Metrics & KPIs

* **Conversions**\
  Number of users who completed a defined conversion event (e.g., purchase, signup).
* **Conversion Rate**\
  `Conversions ÷ Unique Emails Delivered`
* **Revenue**\
  Sum total of purchase values tracked during campaign; defined during conversion tracking setup.
* **Open Rate**\
  `Unique Opens ÷ Unique Emails Delivered`
* **Click Rate**\
  `Unique Users with Clicks ÷ Unique Emails Delivered`
* **Click to Open Rate (CTOR)**\
  `Unique Users with Clicks ÷ Unique Opens`
* **Unsubscribes** _(Email Only)_\
  Count of users who unsubscribed. One unsubscribe per user per campaign.
* **Spam Reports** _(Email Only)_\
  Number of users who marked the email as spam. Users who report are automatically unsubscribed from future emails.
* **Total Sends**\
  Total messages sent (e.g., emails, SMS). May be lower than audience size due to send skips.
* **Delivery Rate**\
  `Unique Deliveries ÷ Unique Emails Sent`
* **Send Skips**\
  Messages not sent due to pre-send conditions (e.g., contact opt-out, invalid channel).
* **Not Delivered**\
  Messages that failed **after** send attempt, due to provider issues (e.g., mailbox full, number unreachable).
* **Total Bounces**\
  Messages rejected by the provider due to invalid addresses, content errors, or prior unsubscribes.
* **Unique Users with Clicks**\
  Unique users who clicked a link (excluding unsubscribe links); used to determine experiment winners.
* **Total Clicks**\
  All link clicks (excluding unsubscribes), including multiple clicks per user.
* **Funnel**\
  A step-by-step visualization of user progression—from campaign entry to final conversion.
