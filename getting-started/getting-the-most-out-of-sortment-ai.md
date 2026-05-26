---
hidden: true
---

# Getting the Most Out of Sortment AI

Sortment has a built-in AI agent that works across the entire product as a team member helping you to builds real things inside Sortment from plain language prompts: audiences, custom properties, templates, campaigns, journeys, and analysis. Everything it creates goes into Draft so you can review before anything goes live.

This guide explains how it works, how to set it up properly, and how to get the most out of it day to day.

***

### What Sortment AI Can Do For You

Think of the AI assistant as three people on your team working simultaneously.

**A data analyst**

The AI can write complex SQL, build audiences from plain language descriptions, create custom attributes, and build and save charts so you have reusable outputs without re-running queries every time. Work that previously needed a data engineer can be done in minutes.

**A campaign strategist**

The AI monitors your campaigns and KPIs continuously. It surfaces recommendations on your home page feed every day, specific suggestions based on what is actually happening in your workspace, not generic tips.

**A marketing co-pilot**

The AI helps you see your data in ways you might not have thought to look. It identifies patterns, spots segments you were not targeting, and connects campaign performance back to business outcomes. It works toward the goals you have defined.

***

### Where to Find It

The AI assistant is accessible from two places:

* The **Assistant** button in the top-right nav, which opens as a slide-over panel
* The **chat input on the home page**, visible as soon as you land on the home page

The home page input also shows quick action chips: Build audience, Create attribute, Analyze data, and more. These are shortcuts to common tasks.

***

### Why It Needs Context to Work Well

The AI knows your schema: the tables, columns, and relationships in your warehouse. But it does not know your business to the precision until it has been taught. Think of Sortment Agent as your team-mate that required KT to work the way required.&#x20;

Without context, if you ask it to "create a re-engagement campaign for lapsed users," it does not know what exactly "lapsed" means in your company, for creating content what tone your brand uses, which channel you prefer for re-engagement, or what a successful conversion looks like for this goal. It will produce something technically valid as per its understanding at an industry level but it may not be tailored to you.

With the right context in place, it knows all of that and produces outputs you can use immediately.

***

### Intelligence Blocks: The Most Important Setup Step

Intelligence blocks are the AI's long-term memory for your workspace. They are how you give it the context it needs to work well. Every time the AI builds something, it reads all the required intelligence blocks first.

Go to Settings, then Sortment AI, then Intelligence to create them.

**The three blocks to create before doing anything with the AI:**

**Business context** What your company does, what your marketing goals are, how you define key segments, and what success looks like. Examples of what to include: "We are a ride-hailing company. Our primary goal is to increase ride frequency among existing riders. A lapsed user is someone who has not taken a ride in 14 days. A high-value user is someone who takes more than 8 rides per month." etc.&#x20;

**Data context**  The best way to do this is by sharing some sample SQL queries and the purpose of the queries directly in a sheet and let Sortment understand the tables and their purpose, the joins used etc. on its own and fill up the required intelligence blocks. \
\
If required - what the important values are, and any data quirks your team knows about. Examples: "The primary table is called users. The rides table has a column called "e\_sts" with values: completed, cancelled, in\_progress to be used for identifying the ride status". Most of this data is also auto ingested during AI chats overtime.

**Content and design guidelines** Your brand tone, preferred structure, color schema, theme CTA style, what to avoid, basically the complete content DNA that you desire Sortment to use. \
\
A few ways to achieve this -&#x20;

* Upload the tempalte on Sortment and just ask the AI to extract the email and content guidelines from the tempalte. Use "@" to refer the template in the AI chat.&#x20;
* If you have an existing doc on your design and content guidelines, upload the doc directly in the Intelligence blocks and let the AI ingest all the informaton to create a block.&#x20;
* If you do not have any existing content and want to start with something, you can always go to the community templates on Sortment and select any that you like from thousands of available template. Ask the AI to make changes on that template as you desire and then let Sortment AI extract the content and design guidelines from the created templates.&#x20;

The same can be done for as many designs as required, just make sure to tell the AI to give a separate name for every template. Moving forward just prompt about your campaign goal, personalisations and the design you seek (if multiple) and let the AI create the template for you.&#x20;

**Building blocks over time**

You do not have to create everything at once. The AI can also extract memories from your conversations and suggest saving them as intelligence blocks. Over time, your blocks get richer and the AI gets more accurate.

***

### How to Write a Good Prompt

The more specific your prompt, the better the output.

**For audiences**

Include the criteria explicitly. Time windows, thresholds, and column values help.

Less useful: "Create an audience of lapsed users" More useful: "Create an audience of users whose home city is New York, who have taken at least 5 rides in total, but have not taken a ride in the last 30 days"

**For custom properties**

Describe what you want to calculate and give an example of what the output should look like.

Less useful: "Create a property for ride frequency" More useful: "Create a property that counts the number of completed rides a user has taken in the last 90 days. For a user with 12 rides in that period, it should return 12."

**For campaigns**

Mention the channel, the audience, the goal, and the tone.

Less useful: "Create a re-engagement email" More useful: "Create an email campaign targeting the NYC Lapsed Riders audience with the goal of getting them to book a ride. Friendly and slightly urgent tone. Include a 15% discount offer."

**For journeys**

Describe the trigger, the sequence, and any exit conditions.

Less useful: "Build a post-ride journey" More useful: "Build a journey triggered when a user completes a ride with a rating below 3. Send a WhatsApp apology within 30 minutes. Wait 24 hours. If no response, send an email with a discount code."

***

### What the AI Does When It Needs Clarification

If your prompt is ambiguous or references data that does not exist in the workspace, the AI will ask a clarifying question before proceeding.

Clarifications appear as a structured card with multiple choice options. The options are pulled from actual data in your workspace and it will not suggest cities or values that do not exist in your tables. There is a recommended option, a skip option, and a free-text option if none of the choices fit.

The clarification and your answer are logged in the conversation so you can refer back to them.

***

### Using the AI for Specific Tasks

#### Build audience

Use the quick action chip or describe the audience in the chat. The AI loads your schema, checks existing audiences to avoid duplication, builds the filter logic, and creates the audience as a Draft. Review the logic and the matched users in the audience builder before publishing.

#### Create attribute

Describe the property you want to compute. The AI picks SQL or the UI builder based on complexity. Review the generated logic in the attribute detail view before using it in campaigns.

#### Analyze data

Ask specific questions. "Which campaigns had the lowest click-to-open rate last month?" or "Show me the distribution of ride counts across my user base." Be specific about what you want to understand and how you want the output presented.

#### Create campaign

Give the AI a channel, an audience, a goal, and a tone. It builds the campaign structure and creates a template draft. Review both before publishing.

#### Build journey

Describe the trigger and the sequence of steps. Complex journeys with many branches may need refinement after creation. Use the follow-up input to iterate on the same conversation.

#### Set up KPI tracker

Go to Analyze, then KPI tracker. Describe the metric you want to monitor in plain language. The AI sets up the tracker and it begins feeding your home page feed with trends over time.

#### Set up tasks

From the home page chat, access the Tasks section from the navbar. Describe a recurring job you want the AI to run. Examples: "Every Monday morning, review last week's campaign performance and surface what worked and what did not." Tasks run on schedule and their outputs appear in the home page feed.

***

### The Home Page Feed

The home page feed (Insights, Alerts, Needs input) is powered by the AI working in the background.

**Insights** are proactive recommendations generated from your KPI data, campaign performance, and audience trends.

**Alerts** are notifications when something needs attention: a campaign missed its send date, a journey has an error, a draft is stale.

**Needs input** is where the AI surfaces things it cannot do without a decision from you.

The more you set up (KPI trackers, tasks, intelligence blocks) the richer and more useful the home page feed becomes.

***

### Common Mistakes to Avoid

**Skipping intelligence blocks** The single biggest reason AI outputs are generic. Set up the three core blocks before doing anything else with the AI.

**Prompts that are too vague** "Create a re-engagement campaign" produces something generic. Add the audience, the channel, the goal, and the tone.

**Not reviewing before publishing** The AI always creates as Draft. It is a co-pilot, not an autopilot. Review the logic, the targeting, and the content before anything goes live.

**Expecting the AI to know things not in the schema or intelligence blocks** The AI only knows what is in your workspace. If a table is not mapped or a business definition is not in an intelligence block, the AI is working without that information.
