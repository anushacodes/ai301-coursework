# Procedure: how this tool grades a PR package

## Read order

1. Establish the mode using SKILL.md. In live mode, read scope.md first
   and apply its refusal rules, then read voice-guide.md. In eval mode,
   ignore both and use only the supplied package as evidence.
2. Read rubric.md and references/evidence-guide.md. Note the checks,
   their weights and the verdict rule. Stop if the rubric or this
   procedure is unfinished, as SKILL.md requires.
3. Read the issue and thread. Note the reported behavior, reproduction
   and relevant maintainer instructions. Read the repository requirements:
   the bundle's repo facts in eval mode, or the PR template and contribution
   guide in live mode. Include the course requirements for a live course PR.
4. Read the plan before the diff. List the promised work, named files,
   excluded work, test plan and recorded deviations. Use the supplied
   house plan and repro pack when reviewing the house chain.
5. Read the full diff and commit list. In live mode, use the committed
   changes from git diff main...HEAD in the fork's top folder. Note what
   each changed part does; do not count uncommitted edits as delivered work.
6. Read the test evidence, then the PR title and description. Record the
   actual outcomes before considering what the description claims.

This order keeps the plan and observed results as the basis for review,
so the description does not become proof of its own claims.

## Evidence gathering

1. Matches the plan: pair each promised change with the diff that delivers
   it. Check in both directions for omitted work and added behavior.
   For a mismatch, find the plan's deviation note and record its reason.
2. Description matches the code: collect the title and description's
   claims about behavior, scope, completion and testing. Match each to
   the diff or recorded result. Note contradictions and unsupported claims.
3. Evidence tests the issue: compare the original reproduction and planned
   test with the supplied before/after inputs, commands and outputs.
   Record what changed observably and whether the check exercises the
   relevant code. Look for tests that bypass the fix or would pass without it.
4. Repository checks are accounted for: list the applicable repo checks
   and planned verification steps. Pair each with its recorded attempt
   and outcome. For failures, blockers or empty suites, find the explanation
   and the limitation stated in the description. Do not invent extra checks
   when none are required by the supplied facts.
5. Changes stay focused: inspect every diff hunk, not just filenames or
   commit messages. Note how each change supports the issue. Identify
   debug leftovers, dead code, unrelated edits or unnecessary formatting.
   A deviation note alone does not make unrelated work appropriate.
6. Follows submission requirements: pair each template, policy or relevant
   maintainer requirement with where the PR meets it. Check the issue
   reference and required disclosures. Use the course's AI-use disclosure
   requirement for the live course PR; use only the supplied policy in eval.
7. Easy to follow: locate the problem, change, results and limitations in
   the description and evidence. Note repetition or unrelated material that
   makes those details hard to find. In live mode, also collect any voice
   rule violations for the summary.

Keep a short quote or a precise source location with each finding. These
are checks of supplied evidence; do not claim to have executed its commands.

## Check execution

1. Grade every check in rubric order, even after finding a reason to reject.
2. Use the gathered evidence and the pass condition as written. Re-read the
   relevant source if the notes are insufficient or appear to conflict;
   there is no need to repeat the whole read for every check.
3. Assign pass when the evidence meets the condition and fail when it
   contradicts it. For missing evidence, use unclear and name what cannot
   be verified, unless the rubric explicitly makes that omission a failure.
4. Apply the rubric's judgment calls. An explained command failure is
   separate from whether the evidence supports the fix. A disclosed scope
   reduction is separate from whether the diff contains unrelated work.
5. Give one deciding fact or quote per grade. Do not invent requirements,
   evidence or procedure steps. Report any procedure gap in the summary;
   mark checks it leaves unverifiable as unclear.

## Verdict assembly

1. Apply the rubric's verdict rule: accept only when every required check
   passes. Any required fail or unclear means reject. The preferred check
   never changes that result.
2. For a rejection, lead the summary with the first required check in
   rubric order graded fail or unclear. Quote its deciding evidence, or
   name the missing evidence. Include the other checks and their reasons.
3. Include any procedure gaps and live-mode voice notes. Voice feedback
   changes the verdict only when it is part of a rubric check.
4. End with the exact JSON structure required by SKILL.md. Include all
   check names in rubric order, their grades and one-line evidence, then
   the verdict. Validate the JSON and put nothing after its closing fence.
