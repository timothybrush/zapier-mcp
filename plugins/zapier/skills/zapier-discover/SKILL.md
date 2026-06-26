---
name: zapier-discover
description: Discover Zapier MCP use cases tailored to the user's role and the apps they actually use. Asks a short interview about their work and tools, then suggests specific on-demand prompts they can say to their AI assistant — like "find me Jira tickets in this sprint" or "draft a follow-up to my last HubSpot contact." Use when the user asks "what can Zapier do for me", "suggest use cases", "I don't know where to start", "show me ideas", "recommend workflows", "help me figure out what to do with Zapier", "what should I enable", or "give me Zapier examples".
---

# Zapier discover

Help the user figure out what Zapier MCP can actually do *for them* — based on their role, the apps they live in, and the tasks they keep redoing. Output specific, on-demand prompts they can say to their AI assistant, plus the actions they'd need to enable to make each prompt work.

For how the Zapier MCP server itself works, see [docs.zapier.com/mcp](https://docs.zapier.com/mcp).

## When to use

The user is unsure what Zapier can do for them, or doesn't know which actions to enable. They've installed the plugin but want to be pointed at concrete use cases instead of staring at the 9,000-app catalog.

If the user already knows what they want to enable and just needs the setup walkthrough, route to **zapier-setup** instead. If they already have actions enabled and want a profile, route to **create-my-tools-profile**.

## Step 1: Interview

Keep it short — two or three questions, not a survey. Adapt follow-ups based on answers.

Open with:

> "I can help you figure out what to do with Zapier. Quick context first — what do you do for work, and what apps are you in every day?"

Listen for:
- **Role / function** (engineer, PM, sales, marketing, founder, support, creator, ops, recruiter, finance, exec, personal)
- **Named apps** (Slack, Gmail, Jira, HubSpot, etc.)
- **Industry signals** (sole automation builder vs. on a team, B2B vs. consumer, startup vs. enterprise)

If they give you only role *or* only apps, ask one follow-up. If they give you both, optionally ask:

> "Is there a task you keep redoing manually that you'd love to delegate?"

Don't push past three questions. Move on with what you've got.

## Step 2: Generate use cases

Pick the **role library** below that best matches the user's answers (multiple is fine — combine for hybrid roles). For each, surface 4–6 use cases tailored to the apps they mentioned. If they named an app you don't have in the library, default to the closest equivalent (e.g., "Outlook" → use the Gmail patterns; "Monday.com" → use the Asana patterns).

For each use case, output:

- **The prompt** — exactly what the user can say to their AI, in quotes
- **What it does** — one-line explanation
- **Actions needed** — the specific Zapier actions they'd enable to make it work

Format the output as a short prose block per use case, not a table. Group by category if you have 6+ use cases: *Save time on…*, *Stay in the loop on…*, *Stop copying between…*

Don't list more than 6 use cases at once. If you have more, present them in waves — give 4, see if any land, then offer "want more?"

## Step 3: Pick and enable

For the use cases the user reacts to ("yes that one"), produce a consolidated **enable list**:

> "To make those work, you'll need to enable:
> - **Slack:** Send Channel Message, Find Message
> - **Jira:** Find Issue by Key, Create Issue
> - **Google Calendar:** Find Events"

Then offer the handoff:

> "Want me to walk you through enabling them? Run **/zapier-setup** to get them configured. Or, head to [mcp.zapier.com](https://mcp.zapier.com) to add them yourself."

## Step 4: Try it live (optional)

Once they confirm everything is enabled, demo *one* prompt right in the chat. Pick the simplest one. The "oh, this actually works" moment is the whole point.

> "Now try it — say to me: '[their first prompt]' and I'll run it."

## Use case library

Don't read the user every use case verbatim. Pick the most relevant ones for their context and present them as natural recommendations.

### Engineer

- "Find the Jira tickets assigned to me that are still open this sprint." *— Jira: Find Issues via JQL*
- "Get the GitHub PRs waiting on my review." *— GitHub: Find Pull Request*
- "Pull the on-call schedule and tell me when my next shift is." *— PagerDuty: Find On-call*
- "Create a Linear issue from this Slack thread." *— Slack: Get Message + Linear: Create Issue*
- "Find the latest Sentry error for my service and file it as a Jira bug." *— Sentry: Find Issues + Jira: Create Issue*
- "Summarize this week's activity on my GitLab MRs." *— GitLab: Find Merge Requests*

### Product manager

- "Summarize this week's customer feedback from #product-feedback into a Notion doc." *— Slack: Find Messages + Notion: Create Page*
- "Find all Jira tickets tagged 'this-sprint' and post a Slack update for standup." *— Jira: Find via JQL + Slack: Send Channel Message*
- "Look up the HubSpot deal for [customer] and draft a follow-up email." *— HubSpot: Find Deal + Gmail: Create Draft*
- "Convert this Slack thread into a Linear feature request." *— Slack: Read Thread + Linear: Create Issue*
- "Pull my calendar for next week and highlight customer calls." *— Google Calendar: Find Events*
- "Find Linear issues mentioning [feature] and summarize their statuses." *— Linear: Find Issues*

### Sales (AE / SDR)

- "Find the HubSpot contact for [email] and log this call as a note." *— HubSpot: Find Contact + HubSpot: Create Note*
- "Look up [company] in Salesforce and draft a personalized outreach email." *— Salesforce: Find Account + Gmail: Create Draft*
- "Search Pipedrive for deals closing this month." *— Pipedrive: Find Deals*
- "Pull tomorrow's calendar and tell me which meetings are with prospects." *— Google Calendar: Find Events + HubSpot: Find Contacts*
- "Find recent emails from [prospect] and summarize the relationship." *— Gmail: Find Email*
- "Add this LinkedIn profile to HubSpot as a new contact." *— HubSpot: Create Contact*

### Marketing

- "Find the latest Mailchimp campaign stats and post a summary to #marketing." *— Mailchimp: Find Campaign + Slack: Send Channel Message*
- "Pull the Typeform responses from the campaign signup and add them to my campaigns sheet." *— Typeform: Find Responses + Google Sheets: Add Row*
- "Draft promotional Twitter and LinkedIn posts for our latest blog post." *— Webflow/Notion: Find Content + LinkedIn: Create Update + Twitter: Create Tweet*
- "Summarize last week's Google Analytics traffic." *— Google Analytics: Get Report*
- "Add this new lead to ConvertKit and tag them as [segment]." *— ConvertKit: Add Subscriber*
- "Find Klaviyo flow performance for this week." *— Klaviyo: Find Campaigns/Flows*

### Customer success / support

- "Find Zendesk tickets from [customer] in the last 30 days and summarize." *— Zendesk: Find Tickets*
- "Look up this customer's HubSpot record and check their plan and last payment." *— HubSpot: Find Contact + Stripe: Find Customer*
- "Find the Intercom conversation with [user] and pull the latest messages." *— Intercom: Find Conversation*
- "Turn this support ticket into a Linear bug report." *— Zendesk: Find Ticket + Linear: Create Issue*
- "Find Loom videos linked in Slack from this customer." *— Slack: Search Messages*
- "Draft a follow-up email for the customer in this ticket." *— Zendesk: Find Ticket + Gmail: Create Draft*

### Founder / operator (small business)

- "Summarize my Gmail inbox from this morning." *— Gmail: Find Email*
- "Find Stripe payments from this week and post a celebration to Slack." *— Stripe: Find Payments + Slack: Send Channel Message*
- "Look at my QuickBooks invoices and tell me what's overdue." *— QuickBooks: Find Invoices*
- "Find Shopify orders from this week and summarize." *— Shopify: Find Orders*
- "Add this new customer to both HubSpot and Mailchimp." *— HubSpot: Create Contact + Mailchimp: Add Subscriber*
- "Check my calendar and draft an end-of-day Slack update for my team." *— Google Calendar: Find Events + Slack: Send Channel Message*

### Recruiter / HR

- "Find Greenhouse candidates currently in the [stage] pipeline." *— Greenhouse: Find Candidates*
- "Look up the Lever candidate for [name] and check their status." *— Lever: Find Candidate*
- "Add this LinkedIn profile to Greenhouse as a new candidate." *— Greenhouse: Create Candidate*
- "Pull this week's interview schedule from my calendar." *— Google Calendar: Find Events*
- "Find recent BambooHR PTO requests pending approval." *— BambooHR: Find Time Off Requests*

### Finance / accounting

- "Find QuickBooks invoices over [amount] that are unpaid." *— QuickBooks: Find Invoices*
- "Look up the Stripe customer for [email] and check their subscription." *— Stripe: Find Customer*
- "Add a new expense to Xero." *— Xero: Create Expense*
- "Pull this month's revenue from Stripe and summarize." *— Stripe: Find Charges*
- "Find recent Plaid transactions for [account]." *— Plaid: Find Transactions*

### Executive / leader

- "Summarize my Slack DMs from this morning." *— Slack: Find Messages*
- "Find Linear issues tagged 'leadership-priority' and check progress." *— Linear: Find Issues*
- "Get my calendar for next week and flag any conflicts." *— Google Calendar: Find Events*
- "Find Notion docs in the [strategy] workspace updated this week." *— Notion: Find Pages*
- "Draft a weekly team update from my recent Slack and calendar activity." *— Slack: Find Messages + Google Calendar: Find Events + Gmail: Create Draft*

### Creator / content

- "Find scheduled YouTube videos for this week." *— YouTube: Find Videos*
- "Post the same update to Twitter and LinkedIn." *— Twitter: Create Tweet + LinkedIn: Create Update*
- "Add this new email to my ConvertKit list." *— ConvertKit: Add Subscriber*
- "Schedule this blog post in Buffer." *— Buffer: Create Update*
- "Find Substack subscribers added this week." *— Substack: Find Subscribers*

### Operations / project coordinator

- "Find Asana tasks assigned to my team this week." *— Asana: Find Tasks*
- "Add a row to my project tracker sheet." *— Google Sheets: Create Spreadsheet Row*
- "Pull items in [status] from my Monday.com board." *— Monday.com: Find Items*
- "Find the latest meeting notes in Google Docs and summarize." *— Google Docs: Find Documents + Google Docs: Get Content*
- "Create a Trello card from this Slack message." *— Slack: Read Thread + Trello: Create Card*

### General productivity / personal

- "Find emails from [person] in my inbox." *— Gmail: Find Email*
- "Add this to my Notion task list." *— Notion: Create Database Item*
- "What's on my calendar tomorrow?" *— Google Calendar: Find Events*
- "Find Drive files shared with me this week." *— Google Drive: Find File*
- "Search my Notion workspace for [topic]." *— Notion: Find Page*

## Handling edge cases

- **App not in the library:** if the user names an app that isn't represented above (e.g., a niche or vertical tool), assume Zapier supports it — the catalog has 9,000+ apps. Default to "yes, Zapier supports [App]. Common patterns there are Find [Thing] and Create [Thing]." If you want to be sure before recommending it as a starter, tell the user to verify at [zapier.com/apps](https://zapier.com/apps).
- **Multiple roles:** mix categories. A "founder doing marketing" gets a blend from Founder + Marketing. Don't force them into one.
- **No app names given:** the user might just say "I'm a PM" without naming tools. Default to the most common stack for that role (PM → Slack, Jira, Notion, Google Calendar) and ask "does that stack match yours?"
- **Personal / non-work context:** if they describe personal use (managing a home, side project, life admin), draw from **General productivity / personal** plus relevant app-specific suggestions (calendar, finance, fitness, smart home).
- **Server in agentic mode** (`discover_zapier_actions` is available): if the user names something you're unsure about, you can silently call `discover_zapier_actions` to verify before recommending. Don't surface that detail unless the user asks.

## Output template for use cases

When presenting a use case, use this shape — short prose, not a table row:

> **[What the use case does, in plain language]**
>
> Say to me: *"[exact prompt in quotes]"*. I'll [what the action does in one line].
>
> *Actions to enable:* [App]: [Action], [Action]

Group by category if you have 6+ use cases: *Save time on…*, *Stay in the loop on…*, *Stop copying between…*. Don't repeat the category labels in the output unless you're using them as section headers — they're navigation, not content.

## Gotchas

- **Don't ask more than 3 interview questions.** Two is better. Users tune out after that.
- **Don't dump the whole library.** Pick 4–6 use cases relevant to their context and surface them as natural recommendations.
- **Don't list more than 6 use cases at once.** If you have more, offer them in waves: "Want more?"
- **Personal-context users get General Productivity, not a role.** Someone managing a household isn't a "PM" — don't force them into a work role just because the library has more entries there.
- **Don't dismiss apps not in the library.** Default to "yes, Zapier likely supports it" — the catalog has 9,000+ apps. If you want to confirm before recommending it as a starter, verify via `zapier.com/apps/{slug}.md` (see the `zapier-docs` skill for the URL pattern).
- **Frame as MCP prompts, not Zaps.** Zapier templates are written as triggered automations ("When X, then Y"). MCP usage is on-demand ("Say this to your AI"). Always translate.

## Tone

Concrete, never abstract. Avoid "Zapier can help you streamline your workflow." Say instead "Try saying to me: 'Find the latest 3 Slack messages from #product-feedback' and I'll pull them for you." Show, don't pitch.
