# Independent review protocol

Use this protocol when resolving a comparison baseline or briefing the independent
reviewer. An installed `review-agent` skill may provide additional review guidance;
it is not required to use this bundled protocol.

## Fix the comparison

For current changes, inspect staged and unstaged diffs and relevant untracked files.
Record the initial state so subsequent repair rounds include the original change
and all repairs. For a commit, inspect its patch and the related current repairs.

For a base-branch comparison, resolve the supplied branch or ref. When a local branch
has a configured upstream that is ahead of it, use that upstream; otherwise use the
local branch. If the local branch cannot be resolved, try its configured upstream.
If neither resolves, report the unavailable baseline without substituting another
branch. Record the resolved ref and the result of `git merge-base HEAD <ref>`, then
inspect `git diff <merge-base-sha>`. Include relevant staged, unstaged, and untracked
changes in the requested scope. Do not compare only against the base branch's tip.

## Reviewer contract

Read applicable repository instructions, the complete requested diff, and enough
surrounding code, callers, and tests to demonstrate the consequences of each finding.
Check behavior against the supplied requirements. Continue through the full target
after finding an issue. Keep the review read-only: do not edit files, run commands
that alter user data, create commits, push, post comments, or delegate further.

Report defects introduced by the target when a concrete affected scenario and
meaningful consequence can be shown. Exclude unsupported possibilities, pre-existing
defects, intentional behavior changes, and cosmetic preferences. Report important
missing verification as a gap rather than claiming it is a demonstrated defect.

For each finding, give a concise title, priority, file and a small relevant line
range, the triggering scenario, its consequence, and supporting code evidence.
Order findings by priority: P0 for a critical release blocker, P1 for an urgent
defect, P2 for an ordinary defect, and P3 for a lower-impact actionable defect.

No findings is a valid result. End with the scope inspected, checks actually run,
and material verification gaps. Do not certify that the change is defect-free.
