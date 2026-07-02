# skills

A repo of agent skills, distributed with [`skills`](https://skills.sh).

## Install

Add all skills from this repo to your project:

```sh
npx skills add dan-livingston/skills
```

Add a single skill:

```sh
npx skills add dan-livingston/skills -s new-skill
```

List available skills without installing:

```sh
npx skills add dan-livingston/skills -l
```

## Layout

Each skill is a directory under `skills/` with a `SKILL.md`:

```
skills/
  new-skill/
    SKILL.md
```

`SKILL.md` frontmatter needs `name` and `description`. The `description` is what
the agent matches against to decide when to trigger the skill, so make it precise.

## Add a skill

Run the `new-skill` skill and answer its questions. It scaffolds a lean
`skills/<name>/SKILL.md` for you.
