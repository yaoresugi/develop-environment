---
name: code-understanding-guide
description: "Create or update Markdown guides that help a developer understand a codebase or change, identify what to inspect before accepting AI-generated code, and trace requirements to code and tests. Use when asked to save code explanations, reading routes, or understanding and verification guidance as documentation. Not for ordinary explanation-only questions, defect review, or implementation changes."
---

# Code Understanding Guide

Leave a concise, source-grounded guide that helps the reader predict behavior, locate the responsible code, and check important claims. Explain according to the reader's familiarity; understanding a change does not require memorizing syntax or reproducing the whole implementation unaided.

## Scope and output

Read applicable repository instructions and existing documentation. Honor the requested scope, comparison baseline, language, and output location. For a change, resolve and record the baseline and include relevant staged, unstaged, and untracked artifacts. For a whole-project request, explain its main paths without implying a full defect audit. Ask only when an unresolved scope choice would materially change the guide.

Prefer updating an existing relevant guide. Otherwise follow the repository's documentation convention; when none exists, start with `doc/understanding.md`. Use one file unless the material genuinely needs separate pages. Preserve human notes and unrelated content. Link to repository files with portable relative Markdown links and name useful symbols; avoid fragile line-number-only references and inventories of every file.

Only documentation writes are authorized by this skill. Do not modify implementation, tests, dependencies, agent configuration, or git history, and do not push, deploy, merge, or automatically invoke a repair workflow. Report suspected defects separately and ask for repair authority if needed. Use safe read-only inspection and relevant non-mutating checks; respect permissions and side effects when running any checks.

## Ground the explanation

Inspect the actual source, important callers, and corresponding tests rather than relying on PR summaries, author explanations, or an earlier agent's conclusions. Establish intended behavior from the user's requirements and maintained specifications. Do not derive the specification or test expectations solely from what the implementation happens to do.

Separate observed code behavior, documented intent, and inferred design rationale. Source code can show behavior but may not establish why its author chose it. Label uncertainty rather than inventing a persuasive reason. When source and documentation disagree, explain the mismatch without silently selecting one as the intended contract.

Identify the revision and working-tree scope inspected, and distinguish checks actually run from tests merely read. A passing test proves only what its assertions and execution environment cover. Expose material mock, integration, device, concurrency, or failure-path gaps; never turn an explanation or a test count into a correctness guarantee.

## Select what the reader needs

Adapt the organization to the scope, rather than producing a fixed file-by-file tutorial. Cover the following when relevant, combining sections to keep the guide useful:

- Purpose, intended behavior, and invariants that a future change must preserve.
- One representative end-to-end operation, including state/data transitions and ownership.
- Key types and boundaries, with concrete inputs and expected outputs.
- Important design decisions, their tradeoffs, and evidence for claimed rationale.
- A reading route pairing important implementation files with their tests.
- Risk-bearing paths that deserve deeper inspection: for example persistence, validation, permissions, external effects, concurrency, and lifecycle cleanup. Explain failure consequences rather than pasting a universal checklist.
- Verification evidence and remaining checks: relevant environment/setup, operation/input, expected result grounded in requirements, and what the check cannot establish.
- Details that may be deferred, with the assumptions and situations that would make them important. Do not blanket-exempt complex code from review merely because it is obscure.

Distinguish everyday orientation from acceptance review. A reader may initially need only a helper's contract; approving changes to that helper can require inspecting its actual logic, callers, and tests or seeking qualified review. State what this guide covers and what it does not. Keep explanations independent of a conclusion that the change is safe.

## Support active understanding

Offer a few scope-specific checkpoints when useful: predict a concrete output, explain which state changes, trace a failure, or identify the test that would detect an incorrect implementation. Include evidence-backed expected answers or routes for checking them, not rote terminology quizzes. A generated guide does not prove that the reader understands the code; only claim a response was checked when the user actually provided one.

Before handoff, verify file/symbol links and major behavior claims against current source, check for unsupported rationale or acceptance claims, and note unresolved mismatches. Report the guide location, covered scope, and material gaps. Do not claim independent review unless a separate reviewer actually inspected the artifacts.
