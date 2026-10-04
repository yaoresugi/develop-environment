# Codex skills

Personal, reusable Codex workflows in the Agent Skills format.

## Included skills

- `code-understanding-guide` — creates source-grounded reading guides that explain code paths, invariants, and what verification does and does not establish.
- `human-review-guide` — surfaces the human decisions, code paths, and verification gaps that matter when reviewing a change.
- `review-and-fix` — coordinates independent review, validates findings, fixes confirmed defects, and verifies the repairs. Includes a review protocol for environments without an installed `review-agent` skill.
- `skill-examiner` — compares a skill's task outcomes with a skill-free baseline and evaluates the evidence.

## Install

With Node.js and `npx` available, install one or more skills with:

```sh
npx skills add yaoresugi/develop-environment --skill code-understanding-guide --skill human-review-guide --skill review-and-fix --skill skill-examiner
```

To install only the review workflow:

```sh
npx skills add yaoresugi/develop-environment --skill review-and-fix
```

`review-and-fix` needs an environment with independent subagents to perform independent review. When delegation is unavailable, it performs permitted checks and reports that independent review did not run.

The source folders are under `.agents/skills/`. The root `AGENTS.md` guides contributions to this repository; it is not installed with a skill.
