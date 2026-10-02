---
description: Show FeedSheriff account, mailboxes, dashboard, and whether a cleanup is running.
---

Use the inbox-status skill and the FeedSheriff MCP server to summarize the user's inbox.

If `$ARGUMENTS` names a mailbox or range (7d, 30d, 90d), use that. Otherwise default to all mailboxes and 30d.

Return a short human summary: plan, connected inboxes, cleaned this month, inbox size, live scans. No raw JSON.
