# FeedSheriff

Hosted [MCP](https://modelcontextprotocol.io/) server for [FeedSheriff](https://feedsheriff.com). Agents can read Gmail, Outlook, and Zoho inboxes, write filters, and (with an opt-in scope) run cleanups.

This repository is the **plugin package** for Cursor and Claude Code. The product itself stays hosted at `https://feedsheriff.com/mcp`.

[Docs](https://feedsheriff.com/docs/mcp) · [Privacy](https://feedsheriff.com/privacy) · [Settings](https://feedsheriff.com/app/settings)

## Install

**Cursor:** install FeedSheriff from the Cursor Marketplace, then paste an API key from [Settings](https://feedsheriff.com/app/settings). Keys start with `fs_live_`.

**Claude Code:** after the plugin is listed, install it from the Claude plugin directory. Claude connects over OAuth. You approve `read`, `write`, and optionally `cleanup` in the app.

Manual MCP config:

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

```bash
claude mcp add --transport http feedsheriff https://feedsheriff.com/mcp
```

You need a Solo or Multi plan. Cleanup is off unless you turn that scope on.

## What the agent can do

Read: account, mailboxes, dashboard, filters, routines, activity, review queue, live scans.

Write: draft, test, create, update, and delete filters; update routines; decide review items.

Cleanup: preview (returns a short-lived confirm token), start, undo. Starred and important mail is never moved. Trash keeps mail for 30 days.

Email sender and subject in tool output are marked untrusted so models do not follow instructions found in mail.

## Auth

- API keys (`fs_live_…`) from Settings, sent as `Authorization: Bearer`.
- OAuth 2.1 with dynamic client registration at `https://feedsheriff.com/oauth/register`.

## License

MIT for this plugin package. FeedSheriff the product is a hosted service.
