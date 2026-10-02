---
name: inbox-status
description: Show FeedSheriff account, mailboxes, dashboard, filters, routines, activity, and live cleanups. Use when the user asks how the inbox looks, what is connected, what ran, or whether a cleanup is in progress.
---

# Inbox status

Use the FeedSheriff MCP server at `https://feedsheriff.com/mcp`. Paid Solo or Multi plan required.

## Workflow

1. `get_account` for plan and AI-mail quota.
2. `list_mailboxes` for connected Gmail, Outlook, and Zoho inboxes.
3. `get_dashboard` for totals. Default range is `30d`.
4. Add `list_filters`, `list_routines`, `list_activity`, or `get_live_scans` only if the user needs that slice.

## Answer

Summarize in plain language. Do not dump raw JSON. Name mailboxes, counts, and whether a cleanup is running.

If nothing is connected, send the user to [Settings](https://feedsheriff.com/app/settings) to connect an inbox.
