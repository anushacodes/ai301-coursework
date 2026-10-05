# Rubric: is this plan ready to post and build from?

A plan is ready when a maintainer could trust its diagnosis, see its
limits, and a stranger could build and verify it. Judge the plan itself
against the repro evidence, never its formatting or length.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis follows the evidence | The plan's stated cause read against the repro evidence's steps, outputs, tracebacks and any control runs; see Diagnosis and grounding. | The stated cause explains the observed behavior and is consistent with every result in the repro evidence, including controls. It targets the cause the evidence points at, not a symptom or a component the evidence rules out. A cause the evidence cannot support, or one it contradicts, fails. | required |
| Bounded scope | The plan's in-scope statement, not-in-scope line and named files, read against the issue's ask; see Scope. | The plan is one change that fixes the reported problem and says what it will not touch. Refactors, migrations, renames, new features or redesigns beyond what the issue and evidence need fail, even if described as small. | required |
| Stranger could start | The plan's files or areas, approach and order of work; see Executability. | A developer new to the repo could open the named place and begin the change without asking the author. The plan names where the change goes and what it does there. Vague intent ("improve handling", "clean up") fails. | required |
| Decisive test plan | The plan's test plan read against the repro evidence's steps and observed results; see Test plan. | The test plan re-runs the repro (or a check through the real code) and names an observable outcome that differs between the broken and fixed states, so a pass proves the fix and a fail would show it did not work. "Verify it works" or tests that would pass without the fix fail. | required |
| Honest about unknowns | The plan's risks and unknowns, and the plan comment's claims, read against the repro evidence; see Honesty. | Guesses are labeled as guesses. Claims of completed work, tested results or confidence are supported by the quoted repro evidence. Nothing is stated as fact that the package does not show. | required |
| Comment fits thread and repo | The plan comment read against the thread highlights and the repo-facts block's contribution policy, templates and AI-disclosure rules; see Comms. | The comment follows any explicit direction a maintainer gave in the thread and any stated repo requirement, including AI-use disclosure when the repo-facts state one. Do not invent a rule that the facts do not state. A comment that ignores an explicit ask or a stated requirement fails. | required |
| Plan comment is a plan | The plan comment compared with the plan; see Comms. | The comment states the cause, scope and test in the author's own words, consistent with the plan, without blame, deadlines or demands. | required |
| Easy to follow | The plan and comment together; see Comms. | The main point can be found quickly, with no repeated or unrelated material. | preferred |

## Verdict rule

Accept when every required check passes. A required fail means reject.
A required `unclear` also means reject: a plan whose evidence cannot be
verified from the package is not ready to build from. The preferred check
never changes the verdict. Give a fact or quote for every grade.

## Judgment calls

- Terse can be ready; long can be unready. Grade the substance.
- A plan may be grounded in the repro evidence even if the repro does not
  name the fix. The plan must not contradict or ignore what it shows.
- Unknowns stated honestly do not fail a plan; false certainty does.
- Check the comment against the thread and repo-facts block only; do not
  invent policy.
