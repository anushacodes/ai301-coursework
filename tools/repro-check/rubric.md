# Rubric: is this ready to post?

A reader should be able to repeat the attempt and see why the conclusion
follows. These checks apply to the claim and report together.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Issue-specific claim | Claim wording compared with the issue's behavior and trigger; see Comms. | Name the problem, give a concrete investigation step, and plan to report back. Support any claim of completed work with evidence in the package. | required |
| Relevant environment | Report's setup details compared with the issue's target; see Environment. | Give the OS, relevant software versions, and tested release or commit. Include settings that affect the bug. Explain important differences from the original setup and limit the conclusion accordingly. A release version can identify the code without a separate commit. | required |
| Repeatable steps | Report's setup, input, commands or UI actions; see Steps. | A reader can follow the attempt through the issue's trigger without guessing an essential step. Include needed data or code, or link to a specific accessible source. | required |
| Evidence matches the issue | Output, logs, screenshots or test results compared with the issue; see Behavior shown. | Show what happened when testing this issue's trigger and state the expected result. Evidence of a successful attempt where the bug did not appear also counts. A different crash, a setup blocker or “same here” is insufficient. | required |
| Honest conclusion | Report's conclusion compared with its setup, steps and evidence; see Honesty. | Say whether the bug reproduced, did not reproduce, or could not be tested. Keep conclusions within what the attempt shows. Label guesses about the cause. An evidenced cannot-reproduce result passes; an honest setup blocker can pass this check while failing other checks. | required |
| Repository conventions | Both comments compared with the supplied repo facts or live contribution and reporting rules; see Comms. | Meet the applicable requirements, including AI disclosure when required. Avoid blame, demands for fixes or deadlines, and unsupported accusations. Don't invent a disclosure rule. Checked sources with no such rule are different from sources you couldn't access. | required |
| Easy to follow | Claim's plan and report's expected result, actual result and supporting evidence; see Comms. | The main point and its evidence are easy to find, without unrelated material or repeated claims. No fixed length or heading order is needed. | preferred |

## Verdict rule

Accept when every required check passes. A required fail or unclear means
reject and revise. The preferred check does not change the verdict.
Give a fact or quote for each grade.

For a live claim-only draft, grade Issue-specific claim, Repository
conventions and Easy to follow. Mark the other four checks unclear with
`not yet applicable: claim-only draft` and exclude them from the verdict.
Reproduction evidence isn't due yet.

Eval mode uses only the supplied package and grades all checks. Live mode
also follows scope.md and voice-guide.md. Voice notes alone do not change
the verdict.

## Judgment calls

- Ask for details that affect the attempt. Explain why a missing detail matters.
- Any evidence format can work if it shows the relevant result.
- Read the whole package. Don't borrow proof from unquoted local files.
- “Works for me” needs a real attempt and evidence. Success on a different
  setup doesn't establish that the original bug is gone.
- Required information can appear anywhere in the comments. Follow a fixed
  template only when the repo explicitly requires that format.
