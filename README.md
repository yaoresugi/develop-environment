# Codex skills

Personal, reusable Codex workflows in the Agent Skills format.

## Included skills

- `human-review-guide` — surfaces the human decisions, code paths, and verification gaps that matter when reviewing a change.
- `skill-examiner` — compares a skill's task outcomes with a skill-free baseline and evaluates the evidence.

## Install

With Node.js and `npx` available, install either or both skills with:

```sh
npx skills add yaoresugi/develop-environment --skill human-review-guide --skill skill-examiner
```

The source folders are under `.agents/skills/`.