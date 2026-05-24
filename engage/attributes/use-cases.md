# Use Cases

**Traits** in Sortment allow teams to define reusable logic for grouping users or computing values that can be applied consistently across audiences, campaigns, and journeys. Traits help enforce consistency, reduce errors, and save time by centralising business logic.

***

#### Why traits matter?

Without shared traits, different teams may interpret the same data differently. For example:

* **Marketing** defines a **High Value Customer (HVC)** as anyone with lifetime spend over $3M.
* **Sales** considers HVCs as those spending $1M+, based on their pipeline goals.

If each team builds their own audience filters, misalignment is inevitable. Someone might use the wrong threshold or field, leading to flawed insights or mistargeted campaigns.

By defining a single trait like `High Value Customer` (e.g., `total_order_value > 3,000,000`), all teams refer to the same logic. Any future updates are made once and reflected everywhere.

***

### Common trait examples

#### Metric based traits

These are based on **numeric conditions**, **aggregations**, or **threshold logic**:

| Trait                   | Logic                                              |
| ----------------------- | -------------------------------------------------- |
| **High Value Customer** | `total_order_value > 3,000,000`                    |
| **Inactive User**       | `last_login_date < now() - 90 days`                |
| **Coupon Abuser**       | `num_coupons_used > 5 in 7 days`                   |
| **Repeat Buyer**        | `completed_orders >= 2`                            |
| **Engaged Visitor**     | `session_count (last 30 days) > 5`                 |
| **Top 10% Spender**     | `total_order_value in 90th percentile`             |
| **Cart Abandoner**      | `cart_created AND NOT checkout_started within 24h` |

#### **Dimension based traits**

These traits are derived from **field combinations**, **SQL logic**, or **categorical bins**—and not aggregates.

| Trait                    | Logic                                                                  |
| ------------------------ | ---------------------------------------------------------------------- |
| **Adjusted Order Total** | `subtotal - discount + tax + shipping`                                 |
| **Buyer Type**           | `CASE WHEN orders = 1 THEN 'First-time' WHEN orders > 1 THEN 'Repeat'` |
| **Order Size Category**  | Bin subtotal into Low/Medium/High ranges                               |
| **Geo Segment**          | `country IN ('US', 'CA') => 'North America'`                           |

These are especially useful for defining categories, applying transformations, or simplifying complex logic into a single field for reuse.

***

### Create traits using AI

Sortment includes a built-in **AI assistant** that can help you define traits faster and more accurately. Just describe the trait you want in plain language—like:

> "Create a trait of users who made more than two purchases in the last 60 days and haven’t interacted with a promotional email in the last week.

and the AI will generate the corresponding logic for you.

This makes trait creation accessible even to non-technical users and ensures best practices are followed behind the scenes.

***

#### Benefits of Using Traits

* **Shared understanding** across teams
* **Consistent targeting** in campaigns and reporting
* **Centralised logic**, updated once and applied everywhere
* **Faster analysis** and fewer manual filters
* **Reduced human error** in segmentation and performance tracking
