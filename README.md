<div align="center">

<a href="https://feedsheriff.com">
  <img src="assets/logo.png" alt="FeedSheriff" width="120" height="120" />
</a>

# FeedSheriff for AI agents

**Let Claude, Cursor, and VS Code clean your Gmail, Outlook, and Zoho inbox.**
Write filters in plain English, preview every cleanup, undo anything for 30 days.

[![Website](https://img.shields.io/badge/Website-feedsheriff.com-111111?style=for-the-badge)](https://feedsheriff.com)
[![MCP Docs](https://img.shields.io/badge/MCP-Docs-2563eb?style=for-the-badge)](https://feedsheriff.com/docs/mcp)
[![Get API key](https://img.shields.io/badge/Get-API%20key-16a34a?style=for-the-badge)](https://feedsheriff.com/app/settings)

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![MCP](https://img.shields.io/badge/MCP-streamable--http-8b5cf6)](https://modelcontextprotocol.io)
[![Auth](https://img.shields.io/badge/auth-OAuth%202.1%20%7C%20API%20key-111111)](https://feedsheriff.com/docs/mcp)
[![Gmail](https://img.shields.io/badge/Gmail-supported-ea4335?logo=gmail&logoColor=white)](https://feedsheriff.com)
[![Outlook](https://img.shields.io/badge/Outlook-supported-0078d4?logo=microsoftoutlook&logoColor=white)](https://feedsheriff.com)
[![Zoho](https://img.shields.io/badge/Zoho%20Mail-supported-c8202b)](https://feedsheriff.com)

<br />

<a href="https://feedsheriff.com">
  <img src="assets/banner.png" alt="FeedSheriff: clean up junk email in Gmail, Outlook and Zoho" width="720" />
</a>

</div>

<br />

> This repo is the **plugin package** for Cursor and Claude Code. The product runs as a hosted service at **`https://feedsheriff.com/mcp`**. Nothing here runs on your machine.

## Install

<table>
<tr>
<td width="50%" valign="top">

### Cursor

[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=feedsheriff&config=eyJ1cmwiOiJodHRwczovL2ZlZWRzaGVyaWZmLmNvbS9tY3AifQ==)

Or install **FeedSheriff** from the [Cursor Marketplace](https://cursor.com/marketplace) and paste your API key when asked.

</td>
<td width="50%" valign="top">

### VS Code

[![Install in VS Code](https://img.shields.io/badge/VS%20Code-Install%20MCP-007acc?style=for-the-badge&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=feedsheriff&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//feedsheriff.com/mcp%22%7D)

Signs in with OAuth. You pick the scopes in the app.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### Claude Code

```bash
claude mcp add --transport http feedsheriff https://feedsheriff.com/mcp
```

Claude opens a browser for OAuth. Approve `read`, `write`, and (optionally) `cleanup`.

</td>
<td width="50%" valign="top">

### Any MCP client

```json
{
  "mcpServers": {
    "feedsheriff": {
      "url": "https://feedsheriff.com/mcp",
      "headers": {
        "Authorization": "Bearer fs_live_YOUR_KEY"
      }
    }
  }
}
```

[Create a key](https://feedsheriff.com/app/settings)

</td>
</tr>
</table>

You need a **Solo** or **Multi** plan. Cleanup is **off** unless you turn that scope on for the key.

## What your agent can do

| | Tools |
|---|---|
| **Read** | `get_account` `list_mailboxes` `get_dashboard` `list_filters` `list_routines` `list_activity` `list_review_queue` `get_live_scans` |
| **Write** | `draft_filter` `test_filter` `create_filter` `update_filter` `delete_filter` `update_routine` `decide_review` |
| **Cleanup** | `preview_cleanup` `start_cleanup` `undo_action` `undo_scan` |

Try asking:

- "Draft a filter for cold sales pitches and test it on my inbox."
- "Preview a cleanup of my newsletters. How many emails would move?"
- "Show what's waiting in Review."
- "Undo the last cleanup."

## Safe by default

- **Preview first.** `start_cleanup` needs a short-lived confirm token from `preview_cleanup`.
- **Cleanup is opt-in.** It is a separate key scope, off by default.
- **Starred and important mail is never moved.** Uncertain mail waits in Review.
- **Undo for 30 days.** Trash keeps mail 30 days, and every action can be reversed.
- **Email text is untrusted.** Sender and subject in tool output are marked so models don't follow instructions hidden in mail.
- **No mail password.** Inboxes connect through Google, Microsoft, or Zoho sign-in.

## Auth

| Method | Use it for |
|---|---|
| **OAuth 2.1** (dynamic client registration, PKCE) | Claude, VS Code, ChatGPT-style clients |
| **API key** `fs_live_…` | Cursor, scripts, anything that sends a Bearer header |

Metadata: [`/.well-known/oauth-protected-resource`](https://feedsheriff.com/.well-known/oauth-protected-resource) · [`/.well-known/oauth-authorization-server`](https://feedsheriff.com/.well-known/oauth-authorization-server)

## What's in this repo

```
.
├── plugin.json            Agent Plugins manifest (Cursor)
├── mcp.json               Hosted MCP server + API key variable
├── .cursor-plugin/        Cursor plugin manifest
├── .claude-plugin/        Claude Code plugin + marketplace manifest
├── .mcp.json              Claude Code MCP config (OAuth)
├── skills/inbox-cleanup/  Skill: safe cleanup workflow for agents
└── assets/                Logo and banner
```

## Links

[Website](https://feedsheriff.com) · [MCP docs](https://feedsheriff.com/docs/mcp) · [Privacy](https://feedsheriff.com/privacy) · [Terms](https://feedsheriff.com/terms) · [Pricing](https://feedsheriff.com/#pricing) · [X @sarthakguptadev](https://x.com/sarthakguptadev) · [sarthak@feedsheriff.com](mailto:sarthak@feedsheriff.com)

## License

MIT for this plugin package. FeedSheriff the product is a hosted service.
