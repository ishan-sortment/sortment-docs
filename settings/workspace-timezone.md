# Workspace Timezone

The workspace timezone is the default time reference Sortment uses for scheduling syncs, sending campaigns, evaluating journey delays, and displaying timestamps across the platform. Setting it correctly ensures your audiences sync on time and your messages reach users at the right local moment.

## Setting the Workspace Timezone

1. Navigate to **Settings** in the left sidebar.
2. Select the **General** or **Workspace** tab (depending on your plan).
3. Locate the **Timezone** field and choose your timezone from the dropdown.
4. Click **Save**.

{% hint style="warning" %}
Changing the workspace timezone affects all active sync schedules and journey delays immediately. Review any time-sensitive campaigns or journeys before making this change.
{% endhint %}

## How the Timezone Is Applied

| Feature | Effect |
|---|---|
| Sync Schedules | Run times shift to match the new timezone |
| Journey Delays | Delay windows (e.g. "send at 10 AM") use the workspace timezone |
| Campaign scheduling | Scheduled sends are evaluated in the workspace timezone |
| Audit Logs & Reports | Timestamps are displayed in the workspace timezone |

## Recommendations

{% hint style="success" %}
Set the workspace timezone to match the primary market your team operates in. If you serve multiple regions, prefer the timezone where your ops team works — and use audience filters or journey conditions to adjust send times per region.
{% endhint %}

## Related

- [Sync Schedules](sync-schedules.md) — configure when your audiences sync
- [Delivery Controls](delivery-controls.md) — set quiet hours relative to user or workspace timezone
- [Alerts](alerts.md) — alert timing is also governed by the workspace timezone
