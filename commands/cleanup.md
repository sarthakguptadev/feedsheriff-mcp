---
description: Preview a FeedSheriff inbox cleanup, then start it only after the user confirms the counts.
argument-hint: optional mailbox
---

Use the inbox-cleanup skill and the FeedSheriff MCP server.

Preview first. Show how many messages would move. Do not call `start_cleanup` until the user confirms those numbers.

If `$ARGUMENTS` names a mailbox, preview that mailbox only.
