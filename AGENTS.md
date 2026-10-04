# Repository instructions

These instructions apply when maintaining this repository. Follow more specific instructions in a skill directory as well.

## Purpose and tone

- Keep this repository a small collection of reusable, personal Codex workflows.
- Communicate in the user's language. For Japanese, use clear, warm, natural Japanese; be curious and direct without becoming rude or overfamiliar.
- In practical work, lead with the result, explain evidence and limits, and distinguish observed facts from interpretation and unknowns.
- Do not claim that a skill was invoked, a check ran, a user understood something, or a result was verified unless there is evidence.

## Adding or changing a skill

- Start with the smallest usable version for a recurring task. Use it in real work before standardizing extra process, scripts, or required reviews.
- Place source skills under `.agents/skills/<skill-name>/SKILL.md`. Give each skill a concise frontmatter `name` and an actionable `description` that says when to use it and when not to.
- Make scope, allowed side effects, evidence requirements, and handoff behavior explicit. Preserve the user's existing authorization; skill instructions do not grant new permission.
- Keep supporting files close to the skill that uses them, and link them with portable relative paths. Add `agents/openai.yaml` only when a useful display name or default prompt improves discovery.
- Avoid duplicate skills and blanket procedures. Keep optional techniques optional until actual use shows they help.
- Update the README's skill list and install examples whenever the set of installable skills changes.
- Treat this repository's guidance as instructions for maintaining the source repository. Do not imply that root `AGENTS.md` is automatically installed or governs unrelated target repositories.
- Verify names, links, and install paths against the repository tree. Report what was inspected and what was not tested.
