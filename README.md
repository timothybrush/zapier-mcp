# zapier-mcp

> Official plugin distribution for [Zapier MCP](https://zapier.com/mcp). Install the plugin in your AI client and your agent gains access to 9,000+ apps and 40,000+ actions via Zapier's hosted Model Context Protocol server.

The hosted server lives at `mcp.zapier.com/api/v1/connect` and is closed source. This repo is the discovery and installation surface: plugin manifests, onboarding skills, and lifecycle rules that help your AI client use the server correctly from the first call.

## What's in this repo

- **Per-client plugin manifests** for [Claude Code](./plugins/zapier/.claude-plugin/plugin.json) and [Cursor](./plugins/zapier/.cursor-plugin/plugin.json), under `plugins/zapier/`
- **Onboarding skills** for auth, action selection, and health checks ([`skills/`](./plugins/zapier/skills/))
- **Lifecycle rules** covering server-mode detection and the read/write safety model ([`zapier-lifecycle.mdc`](./plugins/zapier/rules/zapier-lifecycle.mdc))
- **Brand assets** ([`assets/`](./plugins/zapier/assets/))

What's **not** here:

- The MCP server itself — hosted at `mcp.zapier.com` (closed source)
- The action catalog — managed at [mcp.zapier.com](https://mcp.zapier.com)
- Product documentation — at [docs.zapier.com/mcp/home](https://docs.zapier.com/mcp/home.md)

For a routing guide to specific skills, rules, and manifests, see [AGENTS.md](./AGENTS.md).

## Install

### Claude Code

```
/plugin marketplace add zapier/zapier-mcp
/plugin install zapier
```

### Cursor

Open [cursor.com/marketplace/zapier](https://cursor.com/marketplace/zapier) and click **Install**.

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

## Zapier MCP, briefly

[Zapier MCP](https://zapier.com/mcp) is a hosted Model Context Protocol server that connects AI assistants to 9,000+ apps. Servers run in one of two modes — **Agentic** (action discovery and execution managed in chat through built-in meta-tools) or **Classic** (each enabled action exposed as a dedicated tool). For the full mode-specific built-in tool reference and product overview, see [docs.zapier.com/mcp/home](https://docs.zapier.com/mcp/home.md).

## After install

1. **Enable actions** at [mcp.zapier.com](https://mcp.zapier.com) — each enabled action becomes a tool your AI can call.
2. **Trust but verify writes.** The lifecycle rules require explicit user confirmation before any write action runs. Read actions don't need confirmation.
3. **Run a health check.** Ask your agent to "check Zapier status" to invoke the [`zapier-status` skill](./plugins/zapier/skills/zapier-status/SKILL.md) and see what's configured.

## Documentation & support

- **Product overview**: [zapier.com/mcp](https://zapier.com/mcp)
- **Documentation**: [docs.zapier.com/mcp/home](https://docs.zapier.com/mcp/home.md)
- **Support**: [help.zapier.com](https://help.zapier.com)
- **For AI agents working in this repo**: [AGENTS.md](./AGENTS.md)
- **For contributors**: [CONTRIBUTING.md](./CONTRIBUTING.md)

---

*Zapier MCP is part of the [Model Context Protocol](https://modelcontextprotocol.io/) ecosystem.*
