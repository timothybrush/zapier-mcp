# zapier-mcp

Source of truth for the official [Zapier MCP](https://docs.zapier.com/mcp/home) plugin — packaged per client and distributed through plugin marketplaces.

**Looking to install or use the plugin?** See [`plugins/zapier/README.md`](./plugins/zapier/README.md) for features, install paths, and example prompts. Or grab it directly from your client's marketplace:

- **Claude Code** — `/plugin install zapier@claude-plugins-official`
- **Cursor** — [cursor.com/marketplace/zapier](https://cursor.com/marketplace/zapier)
- **GitHub Copilot CLI** — `copilot plugin install zapier@zapier-plugins`
- **Kiro** — [kiro.dev/powers](https://kiro.dev/powers)

## What's in this repo

- **[`plugins/zapier/`](./plugins/zapier/)** — the canonical plugin source: skills, lifecycle rule, brand assets, and per-client manifests for [Claude Code](./plugins/zapier/.claude-plugin/plugin.json), [Cursor](./plugins/zapier/.cursor-plugin/plugin.json), and [GitHub Copilot CLI](./plugins/zapier/.github/plugin/plugin.json)
- **[`zapier-power/`](./zapier-power/)** — Kiro Power bundle: `POWER.md` manifest, scoped `mcp.json`, and `steering/` symlinks for [Kiro.dev](https://kiro.dev) consumption
- **[`server.json`](./server.json)** — MCP Registry manifest so the hosted server is discoverable in the [official MCP Registry](https://registry.modelcontextprotocol.io)
- **[`llms.txt`](./llms.txt)** — LLM discovery index
- **Marketplace registries** — [`.claude-plugin/marketplace.json`](./.claude-plugin/marketplace.json) and [`.cursor-plugin/marketplace.json`](./.cursor-plugin/marketplace.json) at the repo root

What's **not** here:

- The MCP server itself — hosted at `mcp.zapier.com` (closed source)
- The action catalog — managed at [mcp.zapier.com](https://mcp.zapier.com)
- Product documentation — at [docs.zapier.com/mcp/home](https://docs.zapier.com/mcp/home)

## Downstream marketplaces

This repo is the source of truth for the plugin. It's vendored or mirrored into:

- [`anthropics/claude-plugins-official`](https://github.com/anthropics/claude-plugins-official) — Anthropic's curated Claude Code marketplace (vendors `plugins/zapier/` via `git-subdir` pinned to `main`)
- [`anthropics/knowledge-work-plugins`](https://github.com/anthropics/knowledge-work-plugins) — Anthropic's Claude Cowork marketplace (vendors `plugins/zapier/` via `git-subdir` pinned to `main`)
- [`kirodotdev/powers`](https://github.com/kirodotdev/powers) — Kiro's Powers catalog, browsable at [kiro.dev/powers](https://kiro.dev/powers); mirrors `POWER.md` and the steering files
- [`cursor/mcp-servers`](https://github.com/cursor/mcp-servers/tree/main/servers/zapier) — Cursor's MCP server registry, surfaced at [cursor.com/marketplace/zapier](https://cursor.com/marketplace/zapier)

## For contributors

- [AGENTS.md](./AGENTS.md) — guide for AI agents working in this repo
- [CONTRIBUTING.md](./CONTRIBUTING.md) — how to contribute

---

*Zapier MCP is part of the [Model Context Protocol](https://modelcontextprotocol.io/) ecosystem.*
