# Zapier MCP Plugin Distribution

The official home of the [Zapier MCP](https://docs.zapier.com/mcp/home) plugin. We package it and ship it to every marketplace we support, so your favorite AI agent can connect to your 9,000+ apps the moment you install. The MCP server itself lives at `mcp.zapier.com`. This repo is the plugin on your AI's side, the part that turns the raw catalog into something your AI actually knows how to use.

https://github.com/user-attachments/assets/8304058f-67da-40b9-bc4f-5095b2817d61

- **Get started with the plugin** → [`plugins/zapier/README.md`](./plugins/zapier/README.md)
- **Browse the full docs** → [docs.zapier.com/mcp](https://docs.zapier.com/mcp/home)

## What's in this repo

- **[`plugins/zapier/`](./plugins/zapier/)**: the plugin that onboards you to Zapier MCP and supercharges your experience
- **Marketplace registries**: [`.claude-plugin/marketplace.json`](./.claude-plugin/marketplace.json) and [`.cursor-plugin/marketplace.json`](./.cursor-plugin/marketplace.json) at the repo root, so the plugin is discoverable in client marketplaces

## Supported marketplaces

We ship this plugin to the following marketplaces:

- [`anthropics/claude-plugins-official`](https://github.com/anthropics/claude-plugins-official): Anthropic's curated Claude Code marketplace
- [`anthropics/knowledge-work-plugins`](https://github.com/anthropics/knowledge-work-plugins): Anthropic's Claude Cowork marketplace
- [`kirodotdev/powers`](https://github.com/kirodotdev/powers): Kiro's Powers catalog, browsable at [kiro.dev/powers](https://kiro.dev/powers)
- [`cursor/mcp-servers`](https://github.com/cursor/mcp-servers/tree/main/servers/zapier): Cursor's MCP server registry, surfaced at [cursor.com/marketplace/zapier](https://cursor.com/marketplace/zapier)

## For contributors

- [AGENTS.md](./AGENTS.md): guide for AI agents working in this repo
- [CONTRIBUTING.md](./CONTRIBUTING.md): how to contribute
- **Per-client manifests**: [Claude Code](./plugins/zapier/.claude-plugin/plugin.json), [Cursor](./plugins/zapier/.cursor-plugin/plugin.json), and [GitHub Copilot CLI](./plugins/zapier/.github/plugin/plugin.json)
- [`llms.txt`](./llms.txt): LLM discovery index

---

*Zapier MCP is part of the [Model Context Protocol](https://modelcontextprotocol.io/) ecosystem.*
