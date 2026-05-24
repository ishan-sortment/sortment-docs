# Conversion Tracking

Conversion tracking is helpful when you want to capture user journey beyond the message, like _order placed_ or _subscription purchased_. This can help give you a complete picture of how your campaigns are helping with business goals and metrics.

<figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

### Event Setup (Pre-requisite)

{% hint style="success" %}
Conversion event tracking can be enabled if you have real-time events set in Sortment. In campaign reporting, user actions like message read, link click are already captured.
{% endhint %}

To use **conversion tracking** in a campaign, the required conversion event **should already be sent to Sortment**.

If the required event is not available during campaign setup, you need to [create the event first](../../setup/real-time-events/).

### Configuration setup <a href="#configuration-setup" id="configuration-setup"></a>

To enable conversion tracking within a campaign, users must configure the following on the review page for campaign creation:

**1. Event Selector**

* Enable conversion tracking check box and select the event to track as a conversion event.
* The event should be a predefined action in Sortment

**2. Tracking Duration**

* Users can define how long conversion tracking should remain active after a campaign is delivered.
* Configurable time periods (e.g., 1 day, 7 days, 30 days) ensure flexibility based on campaign goals.

### Reporting <a href="#reporting" id="reporting"></a>

To visualize the conversion data, you can track campaign funnel with conversion step added - this gives you funnel view for the number of users who completed the conversion event within the specified tracking window.
