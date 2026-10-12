# Unit 4 — Test and Submit

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/176

**Branch**

`fix/69-json-array-fallback`

## Eval iterations

**Run history**

The first and only full Unit 4 harness run on October 12, 2026 matched
19/20 packages. Every category had at least one match. The saved report says:

> agreement: 19/20 scored items  (bar: 18/20: PASS)

> categories: clear-accept 6/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3

There were no execution errors. I kept the rules after this run, so there
were no targeted reruns or additional full runs. The submitted skill files
match the report's fingerprints, and eval-run.txt is copied without edits.

**Package analysis**

For pkg-08, my rubric returned reject while the gold label was accept.
The PR fixes a stash prompt that silently does nothing when only untracked
files exist. It includes before/after results, a tracked-file control,
and passing integration and Go tests.

The disagreement came from Repository checks are accounted for. The
checker said:

> Description asserts 'code formatted' under Requirements with no corresponding command/output in Test evidence.

All six other checks passed. The checker wanted separate proof of the
formatting step, while the gold label accepted the package as written.
I understand the rejection under our evidence rule, but it was stricter
than the answer key on this detail.

**Check rationale**

This is the check as it appears in my submitted rubric:

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Repository checks are accounted for | Recorded check commands and outcomes compared with the repo's required checks and the plan's verification steps; see Test evidence. | Applicable checks were attempted and their outcomes are shown. Failures, setup blockers or empty test suites are explained, with the resulting limits disclosed in the description. Skipped checks presented as completed, missing required results or unsupported success claims fail. | required |

I wanted a reviewer to see which checks were actually attempted and what
happened. I rejected an "everything must be green" rule: an empty suite or
an explained blocker can still be reported usefully. The separate check
for evidence of the fix prevents an honest explanation from replacing
proof that the relevant behavior changed.

**Trade-offs**

Requiring recorded outcomes makes unsupported success claims harder to
accept, but it can also reject a useful PR over a routine checklist item.
That happened in pkg-08: its fix and tests were supported, but its formatting
claim lacked separate output. I kept that trade-off for this submission.
The rule also allows an explained failed command, so acceptance does not
mean every check passed; the description still has to state the limits.
