# Trial protocol

Use this reference for paired trials or when evaluating recorded runs. Adapt the
record format to available tools; these are the useful fields, not a mandatory API.

## Minimal experiment record

- Target skill path and content hash or revision; any supporting files it can load.
- Raw user task, case ID, fixture revision, and permitted outputs/side effects.
- Observable criteria fixed before running; keep grading answers out of subject
  context. Record critical criteria separately from presentation preferences.
- For each condition: fresh context, supplied skills, model/effort, tools,
  permissions, initial workspace snapshot, and applicable instruction files.
- Actual output, artifact changes, executed checks and results, loading/tool traces
  when available, and real elapsed-time/token telemetry when available.
- Validity status: comparable, limited, contaminated, or not executed, with reason.

Use null/unknown for absent measurements; distinguish these from a measured zero.
Never call an experimental output independently verified because another LLM merely
repeated it. Inspect artifacts or use a deterministic check when it can settle a
criterion. Qualitative judgment is acceptable when clearly labeled and supported.

## Isolation and routing

For a behavioral comparison, the skill condition receives the skill body or an
explicit invocation plus confirmed access. The baseline receives the same user task
without that skill. Do not include the target skill directory in baseline discovery
paths. Applicable repository instructions stay the same in both conditions.

Subagents may share a filesystem even with fresh conversation context. Give each
subject a separate writable output directory, raw inputs it may inspect, and a clear
instruction not to inspect sibling runs, evaluator records, or hidden grading files.
Prefer filesystem isolation if available; if only instructional isolation is
available, disclose that and inspect traces rather than claiming technical isolation.

An automatic-invocation trial is different: present a natural user request without
explicitly naming or manually loading the skill, then observe whether it is selected
and whether loading is justified. Try a positive use case and a plausible near miss.
If the host cannot supply or observe discovery, mark routing as untested; reviewing
the description alone is a static routing assessment.

## Subject brief

Supply a concrete version of this brief; omit the skill line for a baseline:

```text
Complete this user request: [unaltered realistic request]
Raw task artifacts: [case-local absolute path and files]
Applicable instructions: [relevant instructions common to both conditions]
Skill for this run: [path to SKILL.md; only in the skill condition]
Allowed side effects: [read-only inspection, permitted local checks, output location]
Use only these inputs. Do not inspect sibling runs or evaluator materials, alter the
input fixture, or delegate. Report what you actually inspected, executed, and could
not establish. Write your output to [unique output directory], if requested.
```

Do not append an answer key or a list of expected defects. Avoid suggestive case
names such as `missing-owner-check`; use neutral IDs.

## Comparison and stopping

Assess task success, factual grounding, appropriate scope, and material effort.
Explain which criterion changed, using a specific output or artifact. Retain critical
failures even if a run performs well on other criteria. Separate contaminated runs
from valid comparisons rather than averaging their scores together.

If fixing an instruction after a demonstrated failure, retest the affected behavior
and at least one behavior the correction could regress. Do not keep tuning on the
same answer until it passes and then claim generalization. A fresh case or explicit
limitation is needed. Repetition is useful for uncertain or variable behavior, but
expand trials only when the remaining uncertainty justifies the additional cost.
