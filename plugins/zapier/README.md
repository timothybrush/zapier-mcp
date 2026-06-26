# Zapier Plugin

> [Zapier MCP](https://docs.zapier.com/mcp/home) connects your AI assistant to 9,000+ apps. Send a Slack message, update a Jira ticket, query a Google Sheet, find a HubSpot contact — all through natural conversation.

If you want to get up and running fast, say **"onboard zapier"** to your AI assistant. It'll connect the server, route you into a live first action so you can see Zapier work in your chat, and help you expand from there.

https://github.com/user-attachments/assets/8304058f-67da-40b9-bc4f-5095b2817d61

## What you can ask for

You don't have to remember any skill names. Talk to your assistant the way you normally would and it'll pick up the right path.

| What you want | What to say |
|---|---|
| Connect Zapier MCP and figure out the next step | "onboard zapier" |
| See it actually work — one app, one action, in a few minutes | "show me how Zapier works" |
| Set up a toolkit for your day-to-day | "set up my Zapier toolkit" |
| Check that everything's still working | "zapier status" |

Each step builds on the last, so you never have to commit to a full setup before you've seen Zapier do something useful — the demo is there so you can try it with one action first.

## Built-in safety

Read actions (find, search, get) run immediately. Write actions (send, create, update) show you the payload first and wait for your approval. You won't be surprised by an outbound message or a created record.

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

## Example prompts once you're set up

- "Send a Slack message to #launches saying the release is delayed to Friday"
- "Find the Jira tickets assigned to me that are still open this sprint"
- "Add a row to my Q3 campaigns sheet with the data we just discussed"
- "Create a Linear issue from this customer email and label it 'urgent'"
- "What's on my calendar tomorrow?"
- "Find the HubSpot contact for sarah@acme.com and log this conversation as a note"

## Tips

- **Try one action before configuring a whole toolkit.** A few minutes seeing Zapier work beats reading a feature list. The demo is built for exactly that.
- **Prefer native MCP servers for heavy single-app work.** Doing a lot of Slack or GitHub? A dedicated MCP server for that app will usually outperform Zapier's general-purpose action. Use Zapier MCP for breadth — apps without a native server, and cross-app chains.
- **Re-run `"zapier status"` every once in a while.** Catches duplicates, low-value actions, and conflicts with native MCPs as your setup grows.
- **For agent-readable docs**, append `.md` to any `https://docs.zapier.com/<path>` URL — every page has a raw-markdown mirror.

## Documentation & support

- [docs.zapier.com/mcp](https://docs.zapier.com/mcp/home) — full product documentation
- [mcp.zapier.com](https://mcp.zapier.com) — manage your server and actions
- [status.zapier.com](https://status.zapier.com) — check for outages
- [help.zapier.com](https://help.zapier.com) — support
