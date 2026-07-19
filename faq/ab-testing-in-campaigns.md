# A/B Testing in Campaigns

A/B testing lets you compare two or more variants of a campaign against each other to see which performs best before committing to a single version for your full audience. Use it to validate subject lines, message content, send times, or channel choice with real data instead of guesswork.

## What counts as a variant

A variant is any change you want to test within the same campaign. Common variant types include:

* Subject line or message copy
* Creative or template layout
* Send time or send day
* Sender name or from-address
* Channel (e.g. email vs push for the same audience segment)

{% hint style="info" %}
Keep each test focused on one variable at a time. Testing multiple changes at once (copy *and* send time *and* creative) makes it hard to tell which change actually drove the difference in performance.
{% endhint %}

## How the audience is split

When you set up an A/B test, your campaign audience is divided into groups, one per variant, plus an optional holdout group that receives no message. Sortment randomly and evenly distributes profiles across the groups so each variant gets a comparable, unbiased sample.

* You define the split percentages per variant (e.g. 50/50, or 33/33/33 for three variants).
* A holdout group is useful when you want to measure a variant's true incremental lift against profiles that received nothing.
* Once the audience is split, each profile is locked to its assigned variant for the duration of the test — a profile will never see more than one variant of the same test.

{% hint style="warning" %}
Changing the split percentages after a campaign has already started sending will only affect profiles who haven't yet been assigned to a group. Profiles already assigned keep their original variant.
{% endhint %}

## Defining a success metric

Every A/B test needs a success metric so Sortment can determine a winner. Choose the metric that best reflects the outcome you actually care about:

* **Open rate** — best for testing subject lines or send time
* **Click-through rate** — best for testing creative, copy, or CTA placement
* **Conversion rate** — best for testing anything tied to a downstream event (purchase, signup, etc.), tracked via [Conversion Tracking](../engage/campaigns/conversion-tracking.md)

{% hint style="danger" %}
If you don't have conversion events set up for the metric you want to optimize toward, the test will fall back to engagement metrics (opens/clicks), which may not reflect the business outcome you're actually trying to improve. Set up conversion tracking before launching the test if conversion rate is your goal.
{% endhint %}

## Reading results

Once the test has collected enough data, results show per-variant performance against your chosen success metric, plus the size of each group and a statistical confidence indicator. Use these to decide whether to:

* Declare a winner and roll out that variant to the remaining audience (if you reserved a rollout group)
* Extend the test if results are inconclusive or the sample size is too small
* End the test without a clear winner and revisit your hypothesis

{% hint style="success" %}
Wait for statistical confidence before declaring a winner. Calling a test early on a small sample size is the most common cause of false positives in A/B testing.
{% endhint %}

## Related pages

* [Campaigns Overview](../engage/campaigns/overview.md)
* [Building a Campaign](../engage/campaigns/building-a-campaign.md)
* [Conversion Tracking](../engage/campaigns/conversion-tracking.md)
* [Campaign Reports](../engage/campaigns/campaign-reports/README.md)
