# Data analysis

### How to run an analysis

1. Open the AI assistant (the assistant icon in the top right of Sortment) or the home page.
2. Ask your question in plain language. Be specific about what you want to know and how you want the output framed. For example: "which campaigns had the lowest click-to-open rate last month, give me a table sorted by conversion rate."
3. If the AI needs more detail to answer accurately, it will present a structured clarification card: a labelled question, a set of options pulled from your actual workspace data, a recommended option, and a free-text option if none of the choices fit. You can also just skip the question if it isn't important.
4. Review the result. The AI shows its logic and the SQL it ran, so you can verify the numbers before relying on them.
5. Ask a follow-up in the same thread if you want to refine the analysis. It's a multi-turn conversation, not a one-shot query.

### What the AI actually does

When you ask an analysis question, the AI runs through this sequence automatically:

1. Loads the intelligence blocks for your workspace (business context, data definitions) so it understands what terms like "active user" or "conversion" mean in your business, not just generically.
2. Loads the warehouse schema and table relationships.
3. Fetches the exact table and column names it needs for your question.
4. Writes the SQL required to answer the question and runs it directly against your warehouse.
5. Returns the result as a table or chart, along with a summary of what it found and the SQL logic behind it.

A few things worth knowing about how this works:

* The AI only knows what's in the warehouse schema and your intelligence blocks. If your business context isn't documented anywhere Sortment can see it, the AI will guess at definitions instead of using your actual ones. Setting up a data context intelligence block (table names, column meanings, key values) makes analysis answers much more reliable.
* You can also set this up as a recurring task instead of a one-off question, for example: "every Monday, check which campaigns had below-average click rates last week." Recurring analysis tasks feed directly into the home page insights feed.
* Always validate AI-generated SQL before treating the output as final, especially for anything going into a report or decision. The AI is a co-pilot for analysis, not a replacement for review.

### Saving your output

Once the AI returns a table or chart, you get the option to save it rather than losing it at the end of the conversation. Saved charts and tables live in Analyze, alongside your other dashboards, so they're available to revisit or share later instead of being a one-off answer buried in a chat thread.

