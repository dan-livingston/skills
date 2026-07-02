---
name: copy-confluence-page
description: Copy a Confluence page to a temp dir as Markdown and open it. Fire when the user wants to copy or pull a Confluence page (e.g. "copy confluence page <id or URL>", "pull this confluence page <URL>").
---

# copy-confluence-page

Copy a Confluence page to a temp directory as Markdown, read it into context, and open it in the OS default app.

## When to use

User wants to copy or pull a Confluence page. Triggers: "copy confluence page <id>", "pull this confluence page", a pasted Confluence page ID or URL with intent to copy.

## Instructions

1. Get the page ID or URL from the user. Ask if missing.
2. Make a temp dir: `TMP=$(mktemp -d)` (or `mktemp -d` output).
3. Copy: `npx atlass confluence copy <ID_OR_URL> -o "$TMP"`. Writes a `.md` file into `$TMP`.
4. Find the created file (the `.md` in `$TMP`) and Read it into context.
5. Open in OS default app:
   - win32: `start "" "<file>"`
   - macOS: `open "<file>"`
   - linux: `xdg-open "<file>"`
6. Report the file path.
