---
name: copy-jira-ticket
description: Copy a Jira ticket to a temp dir as Markdown and open it. Fire when the user wants to copy or pull a Jira ticket (e.g. "copy jira ticket ABC-123", "pull this jira ticket <key or URL>").
---

# copy-jira-ticket

Copy a Jira issue to a temp directory as Markdown, read it into context, and open it in the OS default app.

## When to use

User wants to copy or pull a Jira ticket. Triggers: "copy jira ticket ABC-123", "pull this jira ticket", a pasted Jira key or URL with intent to copy.

## Instructions

1. Get the issue key or URL from the user. Ask if missing.
2. Make a temp dir: `TMP=$(mktemp -d)` (or `mktemp -d` output).
3. Copy: `npx atlass jira copy <KEY_OR_URL> -o "$TMP"`. Writes a `.md` file into `$TMP`.
4. Find the created file (the `.md` in `$TMP`) and Read it into context.
5. Open in OS default app:
   - win32: `start "" "<file>"`
   - macOS: `open "<file>"`
   - linux: `xdg-open "<file>"`
6. Report the file path.
