# Creating an A/B Test (Experiment)

A/B testing lets you compare two or more variants of a campaign against a portion of your audience to see which one performs best before rolling out to everyone. Use it to validate subject lines, content, send times, or channel choices with real engagement data instead of guesswork.

## Before you start

- You need an existing [Audience](../engage/audiences/README.md) to run the experiment against.
- Decide what you're testing — a single variable (subject line, message copy, send time) per experiment gives you the clearest read on results.
- Decide your success metric up front (e.g. open rate, click rate, conversion) so you know how to declare a winner.

## Steps to create an A/B test

1. Go to **Engage → Campaigns** and click **Create Campaign**.
2. Give the campaign a name and select the audience you want to test against.
3. When you reach the content step, enable **A/B Test** (instead of the default single-variant setup).
4. Create your variants:
   - Add a **Variant A** and **Variant B** (you can typically add more, depending on your plan).
   - Change only the element you're testing between variants — for example, keep the audience and send time identical, and only vary the subject line.
5. Set the **traffic split** between variants (e.g. 50/50, or 10/10 with the remainder held back for the winner).
6. Choose your **success metric** (open rate, click rate, or conversion, depending on what's available for the channel).
7. Set the **test duration** or **sample size** — how long the experiment runs, or how many recipients are needed, before a winner is determined.
8. Review and launch the campaign.

## After launch

- Once the test window closes, Sortment (or your configured rule) determines the winning variant based on the success metric you selected.
- The winning variant is then sent to the remaining audience, if you configured a holdout.
- Check [Campaign Reports](../engage/campaigns/campaign-reports/README.md) for variant-level performance breakdowns.

{% hint style="info" %}
A/B testing is configured per-campaign. If you want to test a decision point across a multi-step flow (e.g. wait 1 day vs. wait 3 days before the next message), use [Flow Control](../journeys/journey-components/flow-control.md) in Journeys instead.
{% endhint %}

{% hint style="warning" %}
Keep your test to one variable at a time. Changing multiple things between variants (copy, image, send time) makes it impossible to know which change drove the result.
{% endhint %}

{% hint style="warning" %}
Make sure your audience is large enough to reach statistical significance for your chosen metric — very small audiences may not produce a reliable winner.
{% endhint %}
