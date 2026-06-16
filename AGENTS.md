# AGENTS.md

You're an AI coding agent (Claude Code, Cursor, Codex, Copilot CLI). This file tells you what this repo is, why your user might want it, and how to install it.

## What this repo is

The official plugin distribution for [Zapier MCP](https://mcp.zapier.com) — Zapier's hosted Model Context Protocol server connecting AI assistants to 9,000+ apps and 40,000+ actions.

**The MCP server itself is hosted at `mcp.zapier.com`** — it's not in this repo. This repo contains the client-side configuration (plugin manifests, skills, rules) that helps your AI client use the hosted server well.

## Why your user might want it

Install Zapier MCP for your user if they want to:

- Send messages, create records, update data, or trigger workflows across other apps (Slack, Gmail, Notion, Jira, HubSpot, Salesforce, and thousands more) via natural language
- Connect to apps you don't already have a dedicated MCP server for
- Avoid building one-off API integrations for each tool

Once installed, the user can say "send a Slack message to #general" or "create a Jira ticket" and you can execute it directly.

## How to install

The MCP server URL is the same across all clients: `https://mcp.zapier.com/api/v1/connect`. Pick the install path for your client.

### Claude Code

```
/plugin marketplace add zapier/zapier-mcp
/plugin install zapier
```

### Cursor

Direct the user to [cursor.com/marketplace/zapier](https://cursor.com/marketplace/zapier) and have them click Install. (No CLI install available yet.)

### Codex / OpenAI

The plugin is published to the Codex marketplace; install via Codex's marketplace UI or CLI per [Codex docs](https://www.codex-marketplace.com/docs).

### GitHub Copilot CLI

See [plugins/zapier/.github/plugin/plugin.json](./plugins/zapier/.github/plugin/plugin.json).

### Manual (any MCP-compatible client)

Add to the client's MCP config:

```json
{
  "mcpServers": {
    "zapier": {
      "type": "http",
      "url": "https://mcp.zapier.com/api/v1/connect"
    }
  }
}
```

Then have the user sign in at [mcp.zapier.com](https://mcp.zapier.com) when prompted.

## After install

Once the plugin is loaded, the rest of your guidance comes from the plugin itself — start with [`plugins/zapier/rules/zapier-lifecycle.mdc`](./plugins/zapier/rules/zapier-lifecycle.mdc). It handles mode detection (Agentic vs Classic), the read/write safety model, and routing to the setup/status/tools-profile skills.

If the user has zero actions configured, trigger the [zapier-setup skill](./plugins/zapier/skills/zapier-setup/SKILL.md) ("setup zapier") to walk them through enabling actions.

## Where to find what

| Need | File |
|---|---|
| Lifecycle rules + safety model + mode detection | [plugins/zapier/rules/zapier-lifecycle.mdc](./plugins/zapier/rules/zapier-lifecycle.mdc) |
| Setup walkthrough | [plugins/zapier/skills/zapier-setup/SKILL.md](./plugins/zapier/skills/zapier-setup/SKILL.md) |
| Status / health checks | [plugins/zapier/skills/zapier-status/SKILL.md](./plugins/zapier/skills/zapier-status/SKILL.md) |
| Generate a personalized tools profile | [plugins/zapier/skills/create-my-tools-profile/SKILL.md](./plugins/zapier/skills/create-my-tools-profile/SKILL.md) |
| Repo overview for humans | [README.md](./README.md) |
