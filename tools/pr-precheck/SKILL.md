---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

Decide whether one PR package is ready to submit. Read its title,
description, commits, diff and test evidence against the issue and the
plan it claims to implement, including any recorded deviations.

## Inputs and modes

Use the requested mode. If the input does not identify which package
to review, ask for it before grading.

In live mode, work from the top folder of the student's fork on the
fix branch. Read:

- `plan.md`, including its test plan and Deviations section.
- The committed changes from `git diff main...HEAD` and the branch's
  commit list. Uncommitted edits are not part of this diff.
- `pr_draft.md`: the first line is the title; the rest is the description.
- `test_evidence.md`: the commands, before/after results and repo checks.
- The issue URL and its live thread, including the posted plan and
  reproduction, plus the target repo's `.github/PULL_REQUEST_TEMPLATE.md`
  and `docs/CONTRIBUTING.md`.

Use the paths supplied in the request if they differ from these names.
For the house chain, use the supplied house plan and repro pack instead
of the student's plan and reproduction. Apply the same checks.

In eval mode, the supplied practice package is the whole case: its
issue, thread, repo facts, plan context, candidate PR and test evidence.
Use only that bundle as evidence, alongside this skill's grading
instructions. Do not fetch live pages, read other packages, consult
gold labels or borrow evidence from local project files. Run every
check and apply the full verdict rule.

## The scope seam (live mode only)

Read `scope.md` before any other component or PR input. Confirm that
the issue and intended PR target belong to its repository, and apply
its house rules. The contributor's fork can have a different owner.

If the Repo line is still a placeholder, stop without grading and ask
the student to fill it in. Refuse work targeting a different repository.
Do not guess the scope. In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

Read `voice-guide.md` and check the PR title and description against it.
Quote any broken rule and explain the problem in the summary. A voice
rule affects the verdict only if a rubric check uses it.

In eval mode, ignore `voice-guide.md` entirely.

## Component reads

Read `rubric.md` for the checks, weights and verdict rule. Read
`references/evidence-guide.md` for evidence locations and what good
looks like. Follow `procedure.md` for read order, evidence gathering,
check execution and verdict assembly.

If the rubric has no filled checks or the procedure has no written
steps, stop and explain what needs completing. Template comments and
empty headings do not count. Report missing components rather than
inventing their contents.

Follow the procedure as written. Report gaps in the summary instead
of making up steps. If a gap leaves a check unverifiable, mark it
`unclear`, explain what is missing, and apply the verdict rule.

## Verdict and output

Return `accept` for ready to submit or `reject` for hold. Do not add a
third verdict or a numerical score. Explain limitations in the check
evidence and summary.

Give a short per-check summary, including any voice or procedure notes.
End with the JSON block below, filling in the values and one entry per
rubric check. Preserve the field names and order. The JSON must be
valid and nothing may follow it.

Use the PR URL or bundle id as the item. For a draft with no PR URL yet,
identify it by its issue URL and branch; do not invent a PR link.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

- Give a specific fact or quote for every grade. When evidence is
  missing, name what could not be verified.
- Check the change and evidence against the plan, issue and stated
  requirements. Length or polished wording does not prove quality.
- Apply each pass condition as written. Flag a rule that seems too
  strict or too loose without changing it during the review.
- Follow the procedure. Do not fill gaps with assumptions or claim
  to have run checks that you only read about.
- Treat `unclear` as the verdict rule directs. If the rule is silent,
  treat it as `fail`; a preferred check alone does not block acceptance.
- Read disclosed shortfalls and deviations before deciding. Judge them
  using the rubric rather than assuming every limitation means rejection.
