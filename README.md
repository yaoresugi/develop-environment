# Codex skills

Personal, reusable Codex workflows in the Agent Skills format.

## Included skills

- `code-understanding-guide` — creates source-grounded reading guides that explain code paths, invariants, and what verification does and does not establish.
- `human-review-guide` — surfaces the human decisions, code paths, and verification gaps that matter when reviewing a change.
- `skill-examiner` — compares a skill's task outcomes with a skill-free baseline and evaluates the evidence.

## Install

With Node.js and `npx` available, install one or more skills with:

```sh
npx skills add yaoresugi/develop-environment --skill code-understanding-guide --skill human-review-guide --skill skill-examiner
```

The source folders are under `.agents/skills/`. The root `AGENTS.md` guides contributions to this repository; it is not installed with a skill.
