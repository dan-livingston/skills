---
name: new-skill
description: Create a new skill in this repo as a lean, focused SKILL.md. Use when the user wants to write, create, or scaffold a new skill, add a skill to this repo, or turn a repeated workflow into a reusable skill. Biases hard toward terse, single-purpose output over verbose skills.
---

# new-skill

Author a new skill in `skills/<name>/`. Bias toward less. A skill is terse imperative instructions plus a precise trigger, nothing more.

## When to use

User wants to create, write, or scaffold a new skill in this repo, or turn a repeated workflow into one.

## Instructions

1. Ask first, skipping any already answered. Trigger and task mandatory:
   - Trigger: exact phrases/situations that should fire it
   - Task: what the agent does once fired, the core steps
   - Resources: needs bundled files (template, script, reference data), or instructions-only?
   - Rules: any non-negotiable always/never
2. Pick kebab-case `<name>`. Copy `TEMPLATE.md` to `skills/<name>/SKILL.md`. Write files directly, no npx.
3. Frontmatter: `name` matches dir. `description` states when to fire, in concrete situations, not just what it does.
4. Write `## Instructions` as terse imperative bullets. No preamble, no background prose.
5. Budget: aim under ~50 lines. Hard ceiling ~80 lines or ~250 words for the body. Over means cut or bundle.
6. Cut pass: delete every line that does not change agent behavior.
7. Bundle only for a reused artifact the agent copies, a runnable script, or a reference too big for the body. Else single SKILL.md. Prose never justifies a file.
8. Validate, one line pass/fail each: frontmatter valid and `name` matches dir; description is a trigger not a summary; body within budget or bloat justified; cut pass done; every bundled file earns its place.
