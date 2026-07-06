---
name: render-spine
description: Fire when the user wants to inspect or render an exported Spine skeleton (.skel/.json + .atlas), e.g. "render this spine", "spine to webp", "animate this skeleton", "what animations/skins does this spine have". Uses `npx spine-cli`.
---

# render-spine

Inspect and render exported Spine assets to animated webp (or other formats) via `npx spine-cli`.

## When to use

User points at a Spine skeleton and wants info about it or a rendered animation/still. Trigger phrases: "render this spine", "spine to webp/gif/mp4", "animate this skeleton", "what animations/skins does this spine have".

## Instructions

1. Always run `info` first to discover animations, skins, and version:
   `npx spine-cli info <skeleton>` (add `--json` to parse, `--verbose` for per-animation detail).
   Atlas auto-resolves beside the skeleton; pass `--atlas <path>` only if it does not.
2. Pick `--animation` from the info output. Required when the skeleton has more than one; use `-a all` to render every animation.
3. Render:
   `npx spine-cli render <target> -a <name> -f webp -o <out.webp>`
   - Default format `webp` with `--quality 80` unless the user asks otherwise (omit `--quality` for lossless; other formats: pngseq, png, gif, mp4, webm, apng).
   - Background defaults to transparent; set `--background <css-color>` if the user wants a fill.
   - Size via `--scale`, or `--width`/`--height` (these override scale). Timing via `--fps` (default 30), `--duration`, `--loops`.
   - `--skin <name>` to apply a skin; `--frame <t>` with `-f png` for a single still.
4. Batch: pass a directory or glob as `<target>` with `--out-dir <dir>`; use `-a all` and `--concurrency <n>` for speed.
5. Preview intent first with `--dry-run` for batch or destructive-looking renders. Report the output path(s) when done.
