# Zapier Plugin

> [Zapier MCP](https://docs.zapier.com/mcp/home) connects your AI assistant to 9,000+ apps. Send a Slack message, update a Jira ticket, query a Google Sheet, find a HubSpot contact — all through natural conversation.

This plugin supercharges your Zapier MCP setup with a personalized tools profile your agent uses to know which action fits the request, plus a built-in safety model that confirms write actions before they run.

https://github.com/user-attachments/assets/8304058f-67da-40b9-bc4f-5095b2817d61

## Features

- **Personalized tools profile** — the `create-my-tools-profile` skill scans your enabled actions and writes persistent instructions so your agent knows what's available and when to use each one
- **Built-in write safety** — every write action is shown with its payload and waits for your confirmation; reads run without interrupting context-gathering
- **Health checks and audits** — the `zapier-status` skill diagnoses broken tools, finds duplicate actions, and flags conflicts with other MCP servers you've installed

## Install

### Claude Code

Run inside Claude Code's chat:

```
/plugin install zapier@claude-plugins-official
```

If Anthropic's [official marketplace](https://github.com/anthropics/claude-plugins-official) isn't added yet, add this repo as the marketplace first:

```
/plugin marketplace add zapier/zapier-mcp
/plugin install zapier@zapier-plugins
```

### Cursor

**From the marketplace:** open [cursor.com/marketplace/zapier](https://cursor.com/marketplace/zapier) and click **Install**.

**Manual setup:** add Zapier through **Cursor → Settings → Cursor Settings → MCP** ([config below](#any-other-mcp-compatible-client)).

### GitHub Copilot CLI

Run in your terminal:

```
copilot plugin marketplace add zapier/zapier-mcp
copilot plugin install zapier@zapier-plugins
```

### Kiro

**From the catalog:** open [kiro.dev/powers](https://kiro.dev/powers), find Zapier, and click **Add to Kiro**.

**Manual setup:** add Zapier through Kiro's MCP settings ([config below](#any-other-mcp-compatible-client)).

### Any other MCP-compatible client

Add to your client's MCP config:

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

Then sign in at [mcp.zapier.com](https://mcp.zapier.com) when prompted.

## Using Zapier MCP

Once installed, talk to your AI assistant in plain English. The agent picks the right Zapier action based on your request.

**Example prompts:**

- "Send a Slack message to #launches saying the release is delayed to Friday"
- "Find the Jira tickets assigned to me that are still open this sprint"
- "Add a row to my Q3 campaigns sheet with the data we just discussed"
- "Create a Linear issue from this customer email and label it 'urgent'"
- "What's on my calendar tomorrow?"
- "Find the HubSpot contact for sarah@acme.com and log this conversation as a note"

Write actions show the payload first and wait for your confirmation. Read actions run immediately.

First time? Say **"setup zapier"** to your agent.

## Best practices

- **Generate a tools profile after setup.** The `create-my-tools-profile` skill writes personalized instructions to your client's rules directory. Future conversations know what you've enabled and when each tool should be reached for, without re-explaining.
- **Prefer native MCP servers for single-app deep workflows.** If you do heavy Slack or GitHub work, a dedicated MCP server for that app will usually outperform Zapier's general-purpose action. Use Zapier MCP for breadth — apps that don't have native servers, and cross-app chains.
- **Re-run `zapier-status` periodically.** Find duplicates, low-value actions, and conflicts with native MCPs so the catalog stays lean.
- **For agent-readable docs**, append `.md` to any `https://docs.zapier.com/<path>` URL — there's a raw-markdown mirror behind every doc page.

## Documentation & support

- [docs.zapier.com/mcp](https://docs.zapier.com/mcp/home) — full product documentation
- [mcp.zapier.com](https://mcp.zapier.com) — manage your server and actions
- [status.zapier.com](https://status.zapier.com) — check for outages
- [help.zapier.com](https://help.zapier.com) — support
