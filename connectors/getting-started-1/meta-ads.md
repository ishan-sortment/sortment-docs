# Meta Ads

Sortment connects to Meta Ads, letting Sortment AI bring your Meta advertising data into Sortment. Once connected, Sortment AI can pull ad account data, campaign structure, and performance insights, and use them alongside your warehouse and engagement data.

This is one of the connectors available under Sortment AI. You authenticate once, and Sortment AI gets access to the Meta Ads data covered by the permissions granted during setup.

***

### How to use

1. Click the workspace name in the top right.
2. Go to **Workspace Settings**.
3. Go to **Connectors**.
4. Find **Meta Ads** and select **Connect**. This connector uses an API key, so you'll need to generate a Meta access token (via Meta Business Manager) and enter it during setup.

#### Permissions the token needs to cover

* `ads_management` — full read/write access to create, edit, and manage campaigns, ad sets, and ads
* `ads_read` — read-only access to ad account data, campaign structure, and settings
* `read_insights` — access to performance/analytics data (impressions, spend, conversions, etc.)
* `business_management` — manage business assets (ad accounts, pages, pixels, catalogs) under a Business Manager

***

### What can this power

* Intelligence Blocks that combine Meta Ads data with warehouse and engagement data
* A single view of the customer journey, from Meta ad exposure through to product login and lifecycle engagement
* Analysis of which ads and campaigns are driving the best downstream outcomes, so ad strategy can be adjusted based on what actually happens after the click
