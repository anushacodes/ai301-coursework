# Procedure: how this skill grades a plan package

## Read order

1. Read `rubric.md` and `references/evidence-guide.md`. List the checks and the verdict rule.
2. Read the issue context and thread highlights. Note what the reporter asks for and any explicit direction a maintainer gave.
3. Read the repo-facts block. Note the bug-report or PR template asks, contribution rules, and any AI-use disclosure requirement (or that none is stated).
4. Read the repro evidence before the plan. Note the steps, the exact outputs or tracebacks, any control runs, and what each result rules in or out.
5. Read the candidate plan: its cause, in-scope and not-in-scope lines, files, approach, test plan, risks and unknowns.
6. Read the candidate plan comment last, with the notes from steps 2 and 3 in hand.

Reading the repro first matters because the diagnosis and test checks are judged against it.

## Evidence gathering

1. Diagnosis: quote the plan's stated cause. Quote the repro lines that confirm it, and any that contradict it or rule out the named component.
2. Scope: quote the in-scope and not-in-scope statements and list every file or area the plan says it will change. Compare with what the issue asks for.
3. Executability: list the file or function names, the action at each place, and the order of work. Record whether any step lacks a location or an action.
4. Test plan: quote the test plan. Record the repro step it re-runs and the outcome it expects. Decide whether that outcome would differ with and without the fix.
5. Honesty: collect every sentence in the plan and comment that states a cause, a result or a confidence level. For each, find the supporting repro line or note that none exists. Collect the stated risks and unknowns.
6. Comms: list each maintainer direction from the thread and each repo requirement (template, contribution rule, AI disclosure). For each, find where the comment satisfies it or note it is missing. Note any blame, deadline or demand in the comment.

In eval mode use only the bundle text. Never fetch anything.

## Check execution

1. Run the checks in table order.
2. Grade each check from the evidence gathered for it; re-read the package only when the gathered notes are insufficient.
3. If the evidence a check needs is absent from the package, grade `unclear` and say what is missing. Do not guess or borrow from outside the package.
4. If the evidence contradicts the pass condition, grade `fail`.
5. Apply the pass condition as written, even if the plan feels wrong or right. Note any tension in the summary only.
6. Write one line of evidence per check: the quote or fact that decided it.
7. If this procedure is silent on something you needed, note the gap in the summary.

## Verdict assembly

1. Collect the grades. Apply the rubric's verdict rule.
2. Any required `fail` or `unclear` gives `reject`. Only when every required check passes is the verdict `accept`.
3. The preferred check never changes the verdict.
4. In the output, put the deciding fact or quote for each required grade, and for a reject name the first failing required check in the summary.
5. Emit the JSON block last.
