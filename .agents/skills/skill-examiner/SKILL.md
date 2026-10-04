---
name: skill-examiner
description: "Evaluate whether an agent skill improves real task outcomes using isolated trials, a skill-free baseline, and evidence-based grading. Use for スキルの試験官, skillの効果を比較したい, skillを検証して, or regressions after skill edits. Not for general application testing, grading people, or rewriting a skill without evaluation."
---

# Skill Examiner

Determine where a skill helps, fails, adds unnecessary work, or cannot yet be judged.
Use actual task outcomes rather than the persuasiveness of its instructions. Respond
in the user's language. A small evaluation is evidence about the sampled cases,
not a guarantee of general effectiveness.

## Fix the question and evaluation boundary

Locate and read the target skill and applicable project instructions. Identify the
target version, intended use, important exclusions, and the user's evaluation
budget or quality concern. Use the provided examples and current task context;
ask only when a material ambiguity cannot be resolved from available evidence.

Separate static inspection, invocation/discovery, and behavioral effectiveness.
Static validity or a manually loaded successful run does not establish automatic
discovery. Do not infer actual activation just because a prompt contains a name.

Before trials, choose observable success criteria from the user's intended outcome
and raw task requirements. Do not let the evaluated skill define its own correctness.
Include important errors and scope violations as separate gates; extra polish must
not compensate for a fabricated result or an unauthorized mutation. Prefer concrete
pass/fail/unknown criteria to a weighted overall score with arbitrary weights.

For a new evaluation, a small starting set often includes an ordinary task, a known
failure-prone task, and a nearby task that should not invoke the skill. Add cases only
to address a distinct uncertainty. Keep evaluator-only expectations and hidden
fixtures outside the subject's supplied context. See
[references/trial-protocol.md](references/trial-protocol.md) when running comparisons
or evaluating trial logs.

## Run a fair comparison when possible

Compare the same task and initial artifacts with and without the skill, keeping the
model, effort, tools, permissions, and budget equivalent wherever controllable.
Use a fresh independent subagent or session for each condition when available and
authorized. Use no inherited conversation history when the interface supports it.
Keep subject workspaces separate, and do not evaluate a changing target.

Give subject agents only the realistic user request, raw artifacts, relevant project
instructions, and the skill for the skill condition. Do not reveal expected findings,
suspected bugs, proposed fixes, grading answers, another run's output, or the author's
reasoning. Tell subjects their allowed output location and side effects. Do not let
them spawn a second experiment. Do not have skill-examiner recursively evaluate
itself unless the user explicitly requests a bounded self-evaluation.

A baseline must not be supplied or silently load the target skill. Observe loading
or tool traces where available. If isolation, tool availability, or other conditions
cannot be confirmed, report the limitation and classify the comparison accordingly.
Never turn an unavailable baseline into a zero score. If independent execution is
unavailable, provide useful static inspection or a runnable evaluation plan and
state that a behavioral comparison was not performed.

Use local synthetic data or already authorized resources. Avoid live sends,
deployments, purchases, destructive tests, or leaking real private data into fixtures.
Skill invocation does not expand external permissions. Respect the user's budget;
without one, begin with a small smoke evaluation and stop when the stated question
has enough evidence. Do not silently launch a large repeated benchmark.

## Judge evidence and improve narrowly

Inspect outputs, changed artifacts, relevant execution traces, and actual check
results. Verify important claims directly where practical. Mark missing evidence
as unknown. Separate agent behavior from infrastructure failures. If a trial is
contaminated by answer leakage or different starting states, exclude it from fair
comparison and explain why; it can still reveal a process defect.

When practical, grade masked condition IDs before identifying which used the skill.
Use the same rubric for both. Report criterion-level results and observed failure
examples, including regressions and unnecessary actions. Measure time or tokens
only from available telemetry with units and scope; do not estimate missing usage
from response length or invent savings.

Say whether the observations support adopting the skill, making a narrow revision,
or collecting more evidence. Equivalent outcomes on a small sample mean no observed
benefit on that sample. One trial per condition does not establish reliability,
statistical significance, or that the skill caused every observed difference.

If the user requested improvement as well as evaluation, make the smallest change
supported by the evidence. Preserve working behavior and scope. Re-run affected
cases and a relevant regression case; add a fresh holdout when tuning could merely
teach the answer. Preserve the original comparison instead of replacing all history
with the latest successful run. Stop when the requested question is answered or
the agreed budget is reached, and report unresolved limitations.

## Handoff

Give a concise verdict, target version, compared conditions, case-level evidence,
critical failures, and the next justified action. A compact comparison table helps.
State which checks actually ran and which were only planned or inspected. Save a
report or changed skill only when requested or already part of the authorized task;
do not create a documentation project during an ordinary evaluation question.
