# Rubric: is this a good first issue?

For a first contribution, I want a project where someone is still
maintaining the code and a task I can reasonably finish. A friendly label
helps, but I want the decision to come from the issue and its history.

## How to read the evidence

- In eval mode, use only the snapshot bundle. Measure dates against its
  capture date, not today. In live mode, use today's date and the sources
  in `references/evidence-guide.md`.
- Apply the house rules in `scope.md` in live mode only. In Path Review,
  classmates' claim comments do not block an issue. Do not carry that
  exception into the eval snapshots.
- Read the issue body and comments together. A later maintainer decision
  can settle an earlier disagreement. Check PRs mentioned in comments as
  well as formally linked PRs; an empty sidebar alone does not prove that
  nobody is working on the issue.
- Use dates, quoted statements, and recorded states as evidence. Do not
  guess activity dates from an undated response-time average or treat
  stars and labels as proof that a project is healthy.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Active maintenance | Snapshot: the last five default-branch commits, maintainer first-response sample, and issue comments with author associations. Live: the same commit history, recent issue replies, and Owner, Member, or Collaborator comments. | At least one human default-branch commit, merged human contribution, or dated maintainer reply is within the last 90 days, including day 90. A bot merging a human's PR counts; automated bot updates by themselves do not. | required |
| Project still maintained | Snapshot: archived flag, latest release, and last five default-branch commits in Repo facts. Live: archive banner, Releases page, and default-branch history. | The repository is not archived, and it has either a release within the last 12 months or human development on the default branch within the last 90 days. A bot merging a human's PR counts as human development. A missing release is fine when the commit evidence meets the other condition. | required |
| Bounded scope | Issue body and comment thread, especially the requested outcome, required versus optional work, and maintainer statements settling design or product decisions. | The task has one clear outcome, which may require several related files, edits, or steps. Judge the required work; do not turn optional suggestions into requirements. Reject an umbrella of independent tasks, an unresolved design decision, or work a maintainer explicitly says needs major changes to core internals. If the request depends on a product decision, such as adding company branding to shared UI, require evidence that maintainers have accepted that direction; without it, mark this check unclear. A requester's success checklist alone does not settle a product decision. Ordinary implementation details do not need separate approval. A short description, "etc.", or missing reproduction steps alone does not fail this check. If the actual outcome cannot be identified, mark it unclear. | required |
| Contribution still needed | Issue body, current issue state, latest comments, and linked or mentioned PR outcomes. | There is a code, test, or documentation change still being requested. A usage question alone fails. An issue already resolved by a merged fix, withdrawn by its author without a remaining request, or closed as no longer needed fails. | required |
| Work available | Snapshot: assignees and linked PR states in Repo facts, plus claim, progress, and reservation comments. Live: Assignees and Development sections, the comment thread, and PRs mentioned there. | No current assignee or open PR is addressing the same work, no unwithdrawn claim or progress update was posted within the last 30 days, including day 30, and no still-applicable maintainer statement reserves the work for someone. Claims older than 30 days are inactive when those conditions hold; they do not need an explicit withdrawal. A closed, unmerged PR is a past attempt, not active ownership. Apply the live Path Review exception described above. | required |
| AI workflow allowed | Snapshot: contribution policy in Repo facts. Live: CONTRIBUTING.md, linked contributor rules, dedicated AI policy files, and PR template requirements. | No stated rule bans the AI-assisted work we intend to submit. Disclosure, personal understanding, testing, and human-review requirements are conditions to follow, not reasons to reject; record any such conditions. If the checked sources state no AI restriction, pass. If the policy evidence cannot be accessed, mark it unclear rather than assuming permission. | required |
| Clear verification | Issue body and comments for reproduction steps, an expected result, acceptance criteria, or a relevant test. | At least one concrete way to check the change is provided. For a bug, this might be reproduction steps with an expected outcome or a failing test. For documentation, it might be a specific correction to verify. Missing reproduction steps do not change the final verdict. | preferred |
| Clear starting point | Issue body and comments from any author, including named files, functions, examples, and proposed approaches; read later comments for corrections or disagreement. | The issue gives at least one concrete starting point that has not been contradicted: a relevant file or function, a worked example, or an implementation approach. The author's role does not decide whether that guidance is useful. A label alone is not a starting point, and a contributor's suggestion does not count as maintainer approval of an unresolved product decision. | preferred |

## A few judgment calls

Judge scope by the outcome, not the number of files or bullet points.
Writing documentation for one workflow and updating related pages or
links to agree with it is one bounded task when the requested content
and destinations are specified. Likewise, a fix plus its tests and docs
is not three independent tasks. An umbrella issue instead collects
separate outcomes that need their own decisions or work plans. To fail
bounded scope for an umbrella, name those independent outcomes and
explain why they do not serve one specified change; file count or the
amount of text alone is not enough. Other scope failures, such as an
unresolved product decision or explicitly required major changes to
core internals, still apply.

An old issue is not automatically a bad issue. If several attempts were
abandoned, read why. Reject it under bounded scope when that history
reveals unresolved design or major changes to core internals, not simply
because it has been open a long time.

A good-first-issue label can support a maintainer's description of the
work, but it cannot override a failed required check. I would rather
accept a clearly bounded task with a rough write-up than a polished
tracking issue that hides several projects.

The 90-day window is deliberately cautious: I want recent human
involvement for my first contribution. It may exclude some healthy,
slow-moving projects. The release window is longer because projects do
not all publish on the same schedule.

## Verdict rule

Accept only when every required check passes. If any required check fails
or is unclear, reject and explain which evidence caused that result or
what information is missing. Still report every check.

Preferred checks never change accept to reject or rescue a rejected
issue. Use them to help rank accepted issues, together with the fit
profile in live mode. An unclear preference gives no ranking advantage.

Missing evidence is different from an explicit absence: "assignees:
none" establishes that there is no assignee; an omitted assignee field
does not. Similarly, a checked policy with no AI restriction passes,
while an unreadable policy leaves that check unclear. Do not turn a
missing preference into a required failure.
