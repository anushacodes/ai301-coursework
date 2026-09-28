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
