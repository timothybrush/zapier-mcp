# Zapier Plugin

Connects your AI client to [Zapier MCP](https://zapier.com/mcp) — Zapier's hosted Model Context Protocol server. Configure your actions at [mcp.zapier.com](https://mcp.zapier.com), and each one becomes a tool your AI can call directly.

## Quick Start

After installing the plugin:

1. Connect the Zapier MCP server in your client's settings:
   - **Cursor:** Settings > Cursor Settings > Tools & MCP > click **Connect**
   - **Claude Desktop:** Customize > Connectors > Zapier > click **Connect**
   - **Other clients:** find the Zapier MCP server in your MCP settings and connect
2. Sign in to your Zapier account when prompted
3. Open a chat and say **"setup zapier"** to get started

The plugin auto-detects your server mode and routes to the right onboarding flow.

## What's Included

| Component                         | Description                                                                                                                                                       |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **zapier-lifecycle** rule         | Enforces the safety model for reads vs writes, duplicate detection with native MCP servers, and error handling. Always active.                                    |
| **zapier-setup** skill            | Onboarding and connection management. Diagnoses your setup, branches into the right flow (fresh install, reconnect, add tools), and walks you through end-to-end. |
| **zapier-status** skill           | Three modes: health check (dashboard of connected tools), audit (find duplicates and waste), diagnose (systematic troubleshooting).                               |
| **create-my-tools-profile** skill | Scans your configured action tools and generates a personalized tools profile so your AI knows what tools you have and when to use them.                          |

## Server modes

Zapier MCP servers run in one of two modes; the plugin detects which automatically.

- **Agentic** — Action discovery and execution are managed in chat through built-in meta-tools (`list_enabled_zapier_actions`, `discover_zapier_actions`, `execute_zapier_read_action`, etc.).
- **Classic** — Each enabled action is exposed as a dedicated tool named `app_action_name` (e.g., `gmail_send_email`, `slack_find_message`).

For the full mode-specific tool reference, see [docs.zapier.com/mcp/home](https://docs.zapier.com/mcp/home.md).

## Links

- [Zapier MCP Dashboard](https://mcp.zapier.com) — Manage your server, authenticate apps, view connected tools
- [Zapier MCP documentation](https://docs.zapier.com/mcp/home.md) — Full product docs
- [Zapier status](https://status.zapier.com) — Check for outages

## Support

For issues with the plugin or Zapier MCP, contact [support@zapier.com](mailto:support@zapier.com).
