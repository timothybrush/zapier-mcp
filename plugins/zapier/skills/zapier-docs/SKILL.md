---
name: zapier-docs
description: Find and fetch the right Zapier documentation, marketing, or integration page for a user's question — without searching the web. Knows where the agent-readable markdown mirrors live, what topic anchors exist in `zapier.com/llms.txt`, and how to fill in URL slugs for per-app and per-integration pages. Use when the user asks "how does Zapier work with [App]", "show me the docs for [feature]", "what's the difference between Zapier [X] and [Y]", "tell me about Zapier MCP/SDK/Agents/Tables", "find me Zapier integration docs", "what apps does Zapier support", or any factual lookup about Zapier products, features, or integrations.
---

# Zapier docs

Find and fetch the right Zapier page for any factual question — product features, app integrations, SDK/API docs, pricing, comparisons. Zapier publishes structured agent-readable markdown for most surfaces; this skill teaches you where to look so you don't have to web-search.

## When to use vs. other skills

- **zapier-docs** (this skill) — *factual lookups.* "Tell me about X." "Does Zapier support Y?" "How do I do Z with the SDK?"
- **zapier-discover** — *role-tailored use cases.* "What can Zapier do for me?" "Suggest workflows for my role." Interview-driven.
- **zapier-setup** — *configuration.* "Set me up." "Help me connect my server."
- **zapier-status** — *health checks.* "Is everything working?"
- **create-my-tools-profile** — *persistent personalization.* "Save what I have."

If the user wants facts, route here. If they want recommendations or setup help, route to one of the others.

## Step 1: Start with `llms.txt`

Always begin by fetching the root map. It's small, free, and tells you where everything else lives:

```
https://zapier.com/llms.txt
```

This file is a topic-keyed index with **stable anchors** (the topics below). For any Zapier-related question, the right URL is usually one anchor-jump away.

For developer-flavored questions (SDK, building integrations, embedding), there's a more detailed subdomain index:

```
https://docs.zapier.com/llms.txt
```

For deeply content-hungry questions (an LLM that wants every paragraph inlined), there's also:

```
https://zapier.com/llms-full.txt
```

## Topic anchors (cheat sheet)

| Topic | Anchor | What's there |
|---|---|---|
| **Zapier MCP** | `#mcp` | Product page, docs home, quickstart, client setup, embedding |
| **TypeScript SDK** | `#sdk` | SDK overview, quickstart, API reference, CLI reference |
| **AI Agents** | `#agents` | Agents product page, AI hub, chatbots |
| **Workflows / Zaps** | `#workflows` | Workflows page, templates, forms |
| **App catalog** | `#integrations` | Full app list, per-app pages, AI actions reference |
| **Authentication** | `#auth` | User connections, integration auth docs, White Label tokens |
| **Tables** | `#tables` | Zapier Tables product page |
| **Powered by Zapier** | `#embed` | Embed overview, embedded MCP, Workflow API, embedded editor, White Label |
| **Developer platform** | `#developers` | Integration build docs, publishing, Partner Program |
| **Open source** | `#opensource` | Public repos, GitHub org |

Deep-link with the anchor (e.g., `https://zapier.com/llms.txt#mcp`) to jump straight to a topic when you're already inside `llms.txt`.

## URL patterns (with slug placeholders)

### Apps and integrations

| Pattern | Example | Markdown mirror? |
|---|---|---|
| Full app catalog | `https://zapier.com/apps` | HTML only |
| Alphabetical app browse | `https://zapier.com/find-apps/{letter}` (e.g. `/find-apps/a`); also `/find-apps/0-9` for numeric | HTML only |
| Per-app via browse | `https://zapier.com/find-apps/{letter}/{app-slug}` (e.g. `/find-apps/a/airtable`) | HTML only |
| Per-app page | `https://zapier.com/apps/{app-slug}` (e.g. `/apps/slack`) | Yes — append `.md` |
| Per-app integrations index | `https://zapier.com/apps/{app-slug}/integrations` (e.g. `/apps/slack/integrations.md`) | Yes — append `.md` |
| Cross-app integration | `https://zapier.com/apps/{app-a}/integrations/{app-b}` (e.g. `/apps/slack/integrations/gmail.md`) | Yes — append `.md` |
| MCP per-app landing | `https://zapier.com/mcp/{app-slug}` (e.g. `/mcp/slack`) | Unconfirmed — try `.md`, fall back to HTML |

**Slug conventions:** lowercase, hyphenated. `Google Calendar` → `google-calendar`. `HubSpot` → `hubspot`. `Microsoft Teams` → `microsoft-teams`. When unsure, check `zapier.com/llms.txt` or the apps directory.

### Product pages

| Page | URL | Markdown mirror? |
|---|---|---|
| Zapier home | `https://zapier.com/` | HTML only |
| MCP product | `https://zapier.com/mcp` | HTML only (use docs for agent content) |
| AI Agents | `https://zapier.com/agents` | HTML only |
| AI hub | `https://zapier.com/ai` | HTML only |
| Chatbots | `https://zapier.com/ai/chatbot` | HTML only |
| Workflows | `https://zapier.com/workflows` | HTML only |
| Templates | `https://zapier.com/templates` | HTML only |
| Tables | `https://zapier.com/tables` | HTML only |
| Forms | `https://zapier.com/forms` | HTML only |
| Pricing | `https://zapier.com/pricing` | HTML only |
| Enterprise | `https://zapier.com/enterprise` | HTML only |
| Use cases | `https://zapier.com/use-cases` | HTML only |
| Customer stories | `https://zapier.com/customer-stories` | HTML only |
| Guides | `https://zapier.com/resources/guides` | HTML only |
| Open source index | `https://zapier.com/opensource` | Yes — `/opensource.md` |

For HTML-only pages, fetch as HTML and let the agent extract what it needs. Don't apologize to the user about lack of markdown mirroring — just answer the question.

### Documentation (`docs.zapier.com`)

The docs subdomain has comprehensive `.md` mirrors. **Append `.md` to any docs path**:

| Pattern | Example |
|---|---|
| MCP docs home | `https://docs.zapier.com/mcp/home.md` |
| MCP quickstart | `https://docs.zapier.com/mcp/quickstart.md` |
| MCP supported clients | `https://docs.zapier.com/mcp/clients.md` |
| MCP usage and billing | `https://docs.zapier.com/mcp/usage.md` |
| SDK overview | `https://docs.zapier.com/sdk/index.md` |
| SDK API reference | `https://docs.zapier.com/sdk/reference.md` |
| SDK CLI reference | `https://docs.zapier.com/sdk/cli-reference.md` |
| Build an integration | `https://docs.zapier.com/integrations/quickstart/build-integration.md` |
| AI actions reference | `https://docs.zapier.com/integrations/reference/ai-actions.md` |
| Authentication concepts | `https://docs.zapier.com/integrations/build/auth.md` |
| Powered by Zapier overview | `https://docs.zapier.com/powered-by-zapier/index.md` |
| Embedding MCP | `https://docs.zapier.com/powered-by-zapier/embedding-zapier-mcp/getting-started.md` |
| White Label | `https://docs.zapier.com/white-label/getting-started.md` |
| Workflow API auth | `https://docs.zapier.com/powered-by-zapier/authentication/getting-started.md` |
| OpenAPI spec | `https://api.zapier.com/schema` (JSON, not markdown) |

For anything not listed: fetch `https://docs.zapier.com/llms.txt` to get the full developer docs index.

## Common question routing

A starting map. When in doubt, fetch `llms.txt` first and let the topic anchors steer you.

| User asks | Fetch |
|---|---|
| "What can Zapier do with [App]?" | `zapier.com/apps/{app-slug}.md` |
| "How does Zapier connect [App A] and [App B]?" | `zapier.com/apps/{app-a}/integrations/{app-b}.md` |
| "Does Zapier support [App]?" | Check `zapier.com/apps/{app-slug}` — 404 means no |
| "Browse apps starting with [letter]" | `zapier.com/find-apps/{letter}` (use `0-9` for numeric) |
| "What is Zapier MCP?" | `docs.zapier.com/mcp/home.md` |
| "How do I install Zapier MCP in [client]?" | `docs.zapier.com/mcp/clients.md` |
| "How much does Zapier MCP cost / what are the limits?" | `docs.zapier.com/mcp/usage.md` |
| "What's the Zapier SDK?" | `docs.zapier.com/sdk/index.md` |
| "How do I build a Zapier integration?" | `docs.zapier.com/integrations/quickstart/build-integration.md` |
| "How do I embed Zapier in my product?" | `docs.zapier.com/powered-by-zapier/index.md` |
| "What are Zapier Agents?" | `zapier.com/agents` (HTML) |
| "What are Zapier Tables?" | `zapier.com/tables` (HTML) |
| "Show me Zapier pricing" | `zapier.com/pricing` (HTML) |
| "Compare Zapier to [competitor]" | Check `zapier.com/use-cases` and `zapier.com/customer-stories`; search docs if needed |
| "What's the difference between Zapier [X] and [Y]?" | Fetch the topic anchors for both X and Y in `llms.txt` |
| "Find me a template that does [X]" | `zapier.com/templates` (HTML, needs HTML parsing) |

## Fallback strategies

- **404 on a `.md` URL:** drop the `.md` and fetch the HTML. The page might just not be mirrored yet.
- **Slug uncertainty:** if you're not sure of an app's slug, fetch `zapier.com/apps` and search the catalog; or check Zapier's `llms-full.txt` for the canonical slug.
- **Topic not in `llms.txt`:** the page might be a marketing or help center page. Try `help.zapier.com` (end-user help), `community.zapier.com` (forums), or `zapier.com/resources/guides`. None have guaranteed markdown mirrors.
- **Completely missing info:** be honest with the user. "I couldn't find a Zapier doc page for that — happy to check `zapier.com/llms.txt` again or look at `help.zapier.com`."

## Gotchas

- **Don't fetch `llms-full.txt` for a single lookup.** It's significantly larger than `llms.txt` and rarely necessary — only reach for it when you need expanded inline content across multiple topics in one shot.
- **Slugs are lowercase-hyphenated.** `Google Calendar` → `google-calendar`, not `GoogleCalendar` or `google_calendar`. `HubSpot` → `hubspot`. When in doubt, check `zapier.com/find-apps/{letter}`.
- **Marketing-page `.md` mirrors are spotty.** `/apps/{slug}.md` works; `/mcp/{slug}.md`, `/pricing.md`, `/tables.md` likely don't. Try `.md`, fall back to HTML, don't assume.
- **Docs subdomain `.md` mirrors are universal.** Anything under `docs.zapier.com/...` has a `.md` mirror — append `.md` to any docs path.
- **Don't paste URLs as answers.** Fetch the page, extract the answer, cite the source link at the end. The user wants an answer, not a homework assignment.
- **Stable anchors in `llms.txt`** (`#mcp`, `#sdk`, `#agents`, `#workflows`, `#integrations`, `#auth`, `#tables`, `#embed`, `#developers`, `#opensource`) are deep-linkable. Use `https://zapier.com/llms.txt#mcp` to jump straight to a topic when you already know the section name.

## Tone

Answer the user's actual question — don't dump URLs at them. Fetch the doc, extract the answer, cite the source link at the end (`Source: docs.zapier.com/mcp/home`). If you used multiple sources, list them.

Don't tell the user about `.md` mirrors, topic anchors, or URL patterns unless they ask how you found something. Those are tools for you; the user just wants the answer.
