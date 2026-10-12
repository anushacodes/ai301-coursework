# Voice guide: how I write on issues

## Who I am in threads

I'm interested in AI tools and backend work, mostly Python and TypeScript.
I'm new to this project. I want my comments to make it clear what I tried
and where I still need to look.

## Rules I write by

These are some writing examples.

### Rule: Promise the next step

I'll say what I plan to investigate and report back. I won't promise a
fix or a date before I understand the problem.

- Wrong: "I'll fix this by tomorrow."
- Right: "I'll try the array-input case and report what happens."

### Rule: Stick to my own results

I'll describe the run I actually did and include the output. One attempt
isn't enough to say something always happens.

- Wrong: "This crashes every time for everyone."
- Right: "This input raised an AttributeError in my run. The traceback is below."

### Rule: Say when I'm guessing

If I suspect a cause, I'll say so. A traceback gives me somewhere to look;
it doesn't settle the explanation.

- Wrong: "The parser is definitely the cause."
- Right: "The error points to the parser. I still need to check why it happens."

### Rule: Bring my own evidence

Even on a shared issue, I'll include my setup, steps and results. I'll
credit someone else's suggestion if it helped.

- Wrong: "Same as above, confirmed."
- Right: "I tried this too. Here are my setup, commands and output."

## Things I never post

- Fix deadlines I can't promise.
- Claims that I tested something when I only read about it.
- Blame or demands aimed at maintainers.
- Someone else's result presented as mine.
- False claims about working without AI, or missing disclosure when the repo requires it.


### Rule: State the boundary of my plan

I'll name the change, what I'll leave alone, and any assumptions I still
need to test. I'll update the plan if the build changes its meaning.

- Wrong: "I'll fix the parser and clean up the other modules too."
- Right: "I'll add the JSON type checks and tests. The dictionary parser stays as it is."


## When I write a PR

These examples show the wording I'd use when the facts support it.

### Rule: Name the change

I'll use a title that says what changed. The description will cover what
this diff delivers, not everything I hope to improve later.

- Wrong: "Big parser improvements!"
- Right: "Fix plain-text fallback for non-object JSON responses."

### Rule: Make the test results clear

I'll say what I ran, what happened, and what I couldn't verify. I'll
explain failures without hiding them or apologizing for the whole PR.

- Wrong: "Everything works now."
- Right: "Both reproduction tests pass. The integration command found no tests, so it doesn't verify integration behavior."

### Rule: Explain how AI helped

I'll include the course-required disclosure in Notes for Reviewers.
I'll name the help I used and separate it from what I personally checked.
If I haven't reviewed or tested something myself, I won't imply that I did.

- Wrong: "I did this entirely on my own." when AI helped with the change.
- Right: "AI helped draft the fix and tests. I reviewed the diff and ran the checks listed above." only if those actions are true.
