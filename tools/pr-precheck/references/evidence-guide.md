# Evidence guide: where evidence lives in a PR package

In eval mode, use only the supplied package. In live mode, use the
requested files and the issue and repo sources named in SKILL.md.
Keep a quote or source location for each finding. If evidence is missing,
say what could not be checked; do not assume success.

## Plan fidelity (harness category: silent-drift)

**In a practice package:** Read Plan context for the promised work,
excluded work, files and deviations. Compare it with Candidate PR's
Diff, Title and Description. Check claims about results against Test evidence.

**In your own PR:** Compare plan.md, including Deviations, with the
committed git diff main...HEAD output. Read the posted plan in the issue
thread for context. Compare pr_draft.md with that diff and test_evidence.md.
For the house chain, use the supplied house plan and repro pack.

**What good looks like:** Each planned change appears in the diff or has
an explanation in the plan for why it changed or was left out, and each
added change is accounted for. The description accurately states what was
delivered and tested, including limits, without overstating completion.

Supports Matches the plan and Description matches the code. A disclosed
deviation can explain a different approach; it does not excuse unrelated
work under Changes stay focused.

## Test evidence (harness category: not-tested)

**In a practice package:** Compare the reproduction and test plan in Plan
context with Candidate PR's Test evidence: commands, inputs and before/after
results. Find required checks in Repo facts and the plan, and explanations
of failures or limitations in Description.

**In your own PR:** Compare the posted reproduction, or house repro pack,
with plan.md's test plan and the output in test_evidence.md. The saved
Unit 2 output can supply the before result. Read the repo's PR template
and contribution guide for required checks, and pr_draft.md for their
outcomes and limitations.

**What good looks like:** An observable before/after result through the
relevant code supports the claimed fix. Applicable repo and planned checks
have recorded attempts and outcomes, with failures or blockers explained
and their limits disclosed.

Supports Evidence tests the issue and Repository checks are accounted for.
A generic green suite or a test that bypasses the changed behavior is not
proof of the fix. For the live course PR, account for make test-unit,
make test-integration, make lint and make typecheck; report an empty
integration suite as it is. Do not impose those commands on practice repos.

## Diff quality (harness category: unreviewable)

**In a practice package:** Read every hunk under Candidate PR's Diff and
its Commits list. Compare each edit with the issue and Plan context.

**In your own PR:** Read the full git diff main...HEAD output and the
branch's commits relative to main. Use plan.md and the issue to check why
each edit belongs. A file summary can hide debris inside a relevant file.

**What good looks like:** Every edit supports the fix or its relevant tests
and documentation. The diff contains no debug leftovers, dead or commented-out
code, unrelated cleanup or unnecessary formatting changes.

Supports Changes stay focused. Judge the contents, not a fixed limit on
files, lines or commits. Explaining an unrelated edit does not make it necessary.

## Standards and comms (harness category: standards-wall)

**In a practice package:** Read Repo facts for the PR template, contribution
rules and AI-use policy, and Thread highlights for relevant maintainer
instructions. Find where Candidate PR's Title and Description meet those
asks. Read Test evidence alongside testing claims.

**In your own PR:** Read the target repo's .github/PULL_REQUEST_TEMPLATE.md,
docs/CONTRIBUTING.md and the issue thread. Compare their requirements and
the course instructions with pr_draft.md. Use voice-guide.md for the
separate live-mode voice review.

**What good looks like:** Required sections contain useful information,
the issue is referenced, and applicable rules and disclosures are met.
The problem, change, results and limitations are easy to find without
repetition or unrelated text.

Supports Follows submission requirements and Easy to follow. The live
course PR must disclose AI assistance in Notes for Reviewers; practice
packages follow their supplied policies. A stated absence of a policy
is different from an unavailable source. Before opening the live PR,
leave CI unticked and include screenshots when useful or explain why
they are not applicable. Neither replaces evidence from local checks.
