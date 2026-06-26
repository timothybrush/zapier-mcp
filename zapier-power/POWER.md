---
name: "zapier"
displayName: "Zapier"
description: "Connect 9,000+ apps to your AI workflow — discover, enable, and execute Zapier actions directly from your AI assistant."
keywords: ["zapier", "automation", "integrations", "workflow", "ai-actions", "mcp", "no-code", "productivity", "slack", "gmail", "jira", "notion", "hubspot"]
author: "Zapier"
---

# Zapier Power

## Overview

Connect your AI assistant to 9,000+ apps — Slack, Gmail, Google Calendar, Jira, Notion, HubSpot, and thousands more. Once set up, you can search across your tools, take actions, and automate workflows through natural conversation. Zapier MCP is personalized to your workflow: you pick the apps and actions that matter to you, and your AI learns to use them.

**Key capabilities:**

- **Cross-app workflows**: Chain reads and writes across Slack, Gmail, Jira, Notion, HubSpot, and 9,000+ other apps through natural conversation
- **Built-in safety model**: Read actions run without confirmation; write actions require explicit user approval
- **Personalized tool profiles**: Generate persistent AI instructions tailored to the specific set of actions you have enabled
- **OAuth authentication**: No API keys required — authenticate once via mcp.zapier.com and per-app OAuth flows

For how the Zapier MCP server itself works — tool surface, configuration, action management — see [docs.zapier.com/mcp](https://docs.zapier.com/mcp).

## When to Use This Power

Activate this Power when the user:

- Wants to send messages, create records, or trigger workflows in another app (Slack, Gmail, Jira, Notion, HubSpot, etc.)
- Asks "what can I do with Zapier", "set up Zapier", or "show me my Zapier tools"
- Mentions a specific app you don't already have a dedicated MCP server for
- Wants to enable, disable, or audit the actions exposed by their Zapier MCP server
- Wants to generate a personalized tools profile from their enabled actions

## Onboarding

### Step 1: Connect the Zapier MCP server

After installing this power, connect the Zapier MCP server:

- **Connection:** HTTPS endpoint at `https://mcp.zapier.com/api/v1/connect`
- **Authorization:** OAuth via mcp.zapier.com (no API key required)

### Step 2: Get started

- **If Zapier tools are available**: Say **"setup zapier"** to inspect what's configured and walk through next steps
- **If not connected**: Attempt `mcp_auth` on the Zapier MCP server, or follow the manual connection steps above

## Available Steering Files

| File | Purpose |
|---|---|
| [`steering/zapier-setup.md`](./steering/zapier-setup.md) | First-run setup — authentication, mode detection, and onboarding |
| [`steering/zapier-status.md`](./steering/zapier-status.md) | Health check, audit, and diagnose modes for monitoring the setup |
| [`steering/create-my-tools-profile.md`](./steering/create-my-tools-profile.md) | Generate a personalized AI tool profile from enabled Zapier actions |

## When to Load Steering Files

- Setting up Zapier or troubleshooting connection issues → `zapier-setup.md`
- Checking tool health, auditing setup, or diagnosing broken tools → `zapier-status.md`
- Generating a personalized tools profile after setup → `create-my-tools-profile.md`

## Available MCP Servers

### zapier

- **Connection:** `https://mcp.zapier.com/api/v1/connect`
- **Authorization:** OAuth via mcp.zapier.com (no API key required)

For the tool surface exposed by the server, see [docs.zapier.com/mcp](https://docs.zapier.com/mcp).

## MCP Configuration

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

## License and support

This power integrates with [Zapier MCP](https://docs.zapier.com/mcp/home). The plugin distribution is MIT-licensed.

- [Privacy Policy](https://zapier.com/privacy)
- [Support](https://zapier.com/support)
