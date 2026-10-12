# Rubric: is this pull request ready to submit?

A reviewer should be able to see what changed, why it belongs in this PR,
and what the tests actually showed. Check the evidence, not the length
or confidence of the description.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Matches the plan | Diff files and changed behavior compared with the plan's scope, promised work and deviation notes; see Plan fidelity. | The diff delivers the planned work, or the plan records what changed or was left out and why. Nothing is silently added or omitted. A disclosed change in approach or scope can pass this check. | required |
| Description matches the code | PR title and description compared with the diff, plan and recorded results; see Plan fidelity. | The description accurately states what the change does, what was tested and any remaining limitations. It does not claim behavior, coverage or completion that the evidence contradicts or cannot support. | required |
| Evidence tests the issue | Before/after commands, inputs and results compared with the original reproduction and the plan's test plan; see Test evidence. | Evidence through the relevant code shows an observable before/after result for the claimed fix. The check could expose the reported problem, and the output supports the claimed improvement. A generic passing suite, a mock that bypasses the changed behavior or a bare "tests pass" is insufficient. | required |
| Repository checks are accounted for | Recorded check commands and outcomes compared with the repo's required checks and the plan's verification steps; see Test evidence. | Applicable checks were attempted and their outcomes are shown. Failures, setup blockers or empty test suites are explained, with the resulting limits disclosed in the description. Skipped checks presented as completed, missing required results or unsupported success claims fail. | required |
| Changes stay focused | Diff hunks and commits compared with the issue's needs and the plan's boundary; see Diff quality. | Every change supports the fix or its relevant tests and documentation. There are no debug leftovers, dead or commented-out code, unrelated cleanup or unnecessary formatting changes. Explaining an unrelated edit does not make it part of the fix. | required |
| Follows submission requirements | PR title and description compared with the supplied template, contribution policy and relevant maintainer instructions; see Standards and comms. | Required sections contain useful information, the issue is referenced, and applicable submission rules and AI-use disclosures are met. Relevant maintainer requests are addressed. Judge only requirements established by the package or, in live mode, the repo and course instructions. | required |
| Easy to follow | PR description and supporting evidence; see Standards and comms. | A reviewer can find the problem, change, results and limitations without sorting through repetition or unrelated material. No fixed length or extra heading format is required. | preferred |

## Verdict rule

Accept when every required check passes. A required fail or unclear means
reject. The preferred check gives feedback but does not change the verdict.
Give a specific fact or quote for every grade. For unclear, name the
missing evidence instead of guessing.

## Judgment calls

- A failed check command does not automatically mean rejection. An
  explained failure can pass the checks-accounted-for rule when its
  outcome is visible and the claims stay within the evidence. It does
  not replace proof of the fix: grade Evidence tests the issue separately.
- Read deviations as part of the plan. An openly reduced scope can pass
  when the description matches what was delivered. A deviation note does
  not excuse unrelated edits or a claim that all planned work is complete.
- Use the checks and policies actually supplied. If an eval package names
  no additional required suite, do not invent one. Useful evidence can
  come from a command or a focused test; a new test file is not mandatory.
- For the live course PR, AI-use disclosure is required in Notes for
  Reviewers. In eval mode, use the package's stated disclosure policy;
  do not apply the course requirement to every practice repository.
- Evaluate the PR before submission. An unticked CI box is expected for
  the live course draft; it does not replace running the local checks.
