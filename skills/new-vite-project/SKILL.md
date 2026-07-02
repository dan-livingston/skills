---
name: new-vite-project
description: Scaffold a new Vite+ project with `vp create`. Fire when the user wants to start, create, or scaffold a new Vite+ monorepo, application, or library (e.g. "new vite project", "scaffold a vite app", "spin up a vite library").
---

# new-vite-project

Scaffold a Vite+ project, apply house fmt config, format, open in Zed, grill for purpose, seed the README.

## Instructions

1. Get from user (ask only what is missing):
   - Template: `vite:monorepo`, `vite:application`, or `vite:library`
   - Project name (used as target directory)
2. Scaffold:
   ```
   vp create <template> --directory <name> --no-interactive --no-git --hooks --editor zed --package-manager pnpm --no-agent
   ```
3. Init git so the configured pre-commit hook can attach: `cd <name> && git init && vp config`
4. In `vite.config.ts`, replace the empty `fmt: {}` with:
   ```
   tabWidth: 4,
   useTabs: true,
   trailingComma: "all",
   sortImports: {
       groups: [
           "type-import",
           ["value-builtin", "value-external"],
           "type-internal",
           "value-internal",
           ["type-parent", "type-sibling", "type-index"],
           ["value-parent", "value-sibling", "value-index"],
           "unknown",
       ],
   },
   ```
5. Format + lint + typecheck: `cd <name> && vp check --fix`
6. Open: `zed <name>`
7. Grill for purpose: invoke the `grill-me` skill to nail down what the project is for.
8. Fill `<name>/README.md`: title, one-line purpose (from step 7), and a scripts table:
   | script | command | does |
   | --- | --- | --- |
   | `pnpm dev` | `vp dev` | dev server |
   | `pnpm build` | `tsc && vp build` | production build |
   | `pnpm preview` | `vp preview` | preview build |
   | `vp check` | | format + lint + typecheck |
   | `vp fmt` | | format |
