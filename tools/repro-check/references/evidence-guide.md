# Evidence guide: where to look

Quote the fact behind each grade. Use unclear when proof is missing and
fail when the evidence contradicts the rule.

For evals, use only the supplied issue, repo facts, claim and report.
For live checks, read the issue and repo instructions, then the drafts
and their explicit references. Other local files aren't part of a comment.

## Environment

**Where it lives:** Compare the report's setup with the issue and repo
facts. Live, also check maintainer clarifications and setup docs.

**What good looks like:** The OS, relevant versions and tested release
or commit identify the setup. Important differences from the issue are
explained. Extra dependency or configuration details are needed only
when they affect the attempt.

## Steps

**Where it lives:** Read the report's setup, inputs and commands or UI
actions against the issue's trigger. Live, follow specific links that
supply needed code, data or instructions.

**What good looks like:** A reader can repeat the attempt without filling
in a critical gap. “See the docs” is too vague when an essential setup
step is missing. The steps should describe the run shown in the evidence.

## Behavior shown

**Where it lives:** Compare the report's output, logs, screenshots or test
results with the issue's described behavior. Live, inspect linked evidence;
mark essential proof unclear if it cannot be accessed.

**What good looks like:** The evidence connects the relevant action to
its result. A cannot-reproduce report shows the attempt and what happened
instead. A failure before reaching the trigger only establishes a blocker.

## Honesty

**Where it lives:** Read conclusions and explanations alongside the
setup, steps and evidence. Check claims of completed work in both comments.

**What good looks like:** The author says what this attempt established
and what remains uncertain. A guessed cause stays a guess. One successful
run doesn't prove the bug is fixed everywhere.

## Comms

**Where it lives:** Compare the claim with the issue. For evals, read both
comments against the repo-facts reporting and contribution rules. Live,
check CONTRIBUTING, reporting templates, linked policies, scope.md and
voice-guide.md. Name the policy sources checked.

**What good looks like:** The claim names the problem, a concrete next
step and a plan to report back. The comments meet applicable rules and
make the result easy to follow, without blame or demands.

Required information can appear across the two comments. Reproduction
fields aren't due in a claim-only draft. If policy requires AI disclosure,
a silent comment doesn't satisfy it. If the supplied facts state no AI
policy, don't invent one; inaccessible live policies remain an evidence gap.

Live checks also apply the class house rules: other students' claims don't
block yours, and each student supplies their own proof. Quote any broken
voice-guide rule in the summary. The voice guide is ignored during evals.
