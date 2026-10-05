# Evidence guide: where evidence lives in a plan package

Quote the fact behind each grade. Use unclear when needed proof is
missing and fail when the evidence contradicts the rule.

In evals, use only the bundle: repo facts, issue, thread highlights,
repro evidence, candidate plan and candidate plan comment. Live, read the
issue thread and the drafts; other local files are not part of the plan.

## Diagnosis and grounding

**Where it lives:** The plan's `Cause:` statement (or its opening
diagnosis). The behavior it must explain is in the `## Repro evidence`
block: the steps, output or traceback, and any control run.

**What good looks like:** The cause explains the failing output and
agrees with everything the repro shows, controls included. A cause that
names a component the repro rules out, or never mentions a decisive
result, is not grounded. Treat a plan that fixes only the visible symptom
as ungrounded when the evidence points deeper.

## Scope

**Where it lives:** The plan's `Change:` text, its in/out lines, and the
files it names, compared with the issue body.

**What good looks like:** One change that fixes the reported problem, with
an explicit not-in-scope line. A drive-by refactor, rename, migration or
redesign beside the fix is scope creep.

## Executability

**Where it lives:** The plan's file and function names, approach, and
order of work.

**What good looks like:** A newcomer can open the named place and know what
to do there. Locations and actions are specific, not "improve" or "handle
better".

## Test plan

**Where it lives:** The plan's `Test:` section, read against the repro
evidence's steps and expected/actual results.

**What good looks like:** It re-runs the repro (or a check through the real
code) and names an observable outcome that differs before and after the
fix, such as an exit code, an output line or a value. A check that passes
without the fix proves nothing.

## Honesty

**Where it lives:** The plan's risks and unknowns, and each claim of cause,
result or confidence in the plan and the comment. Live, also the
`## Deviations` section after the build.

**What good looks like:** Guesses are labeled, claims point at quoted
evidence, and open questions are named. Certainty the repro does not
support, or "tested" claims with nothing quoted, is false confidence.

## Comms

**Where it lives:** The candidate plan comment, read against `## Thread
highlights` and the `## Repo facts` block (bug-report template,
contribution policy, AI-use policy).

**What good looks like:** The comment follows any explicit maintainer
direction in the thread and any stated repo rule, including AI disclosure
when the repo-facts require it; a silent comment does not satisfy a stated
requirement. It states cause, scope and test in the author's words, without
blame, deadlines or demands. If the repo facts state no policy, do not
invent one.
