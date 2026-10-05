# Plan for issue #69: output parser crashes on a JSON array

## Diagnosis

`parse_review_output` in `rag/generator/output_parser.py` passes whatever
`json.loads` returns straight to `_parse_json_output`, which assumes a dict
and calls `data.items()`. A valid JSON array is not a dict, so it crashes.

Repro evidence I rely on (commit `2f4e82f`, Python 3.11.14, pytest 9.1.1):

```text
rag/generator/output_parser.py:48: in parse_review_output
    return _parse_json_output(data)
rag/generator/output_parser.py:68: in _parse_json_output
    for key, value in data.items():
E   AttributeError: 'list' object has no attribute 'items'
1 failed, 1 passed in 0.23s
```

The object-input test (`test_raw_json_without_fence`) passes in the same
run, so this object-input control works; the run does not establish that
every dict input works. The raw-JSON branch (line 48) is where the array
arrives. At planning time, I inferred the same risk in the fenced branch
from its call to `_parse_json_output`; the added raw/fenced tests now
confirm the fallback behavior after the fix.

## Scope

In scope:
- Make `parse_review_output` treat parsed JSON that is not an object (an
  array, and by the same reasoning a bare string, number or `null`) as
  unstructured output and fall back to the existing plain-text parser, so
  the raw text is preserved as one section.
- Remove the `xfail` marker on `test_json_array_fallback` so it runs as a
  normal test.

Not in scope:
- The unused `sections = []` accumulator in `parse_review_output` (a
  separate, deliberately seeded defect).
- Any change to how dict output is parsed, to `FeedbackSection`, or to the
  plain-text parser.
- Interpreting array items as separate sections. That would be a new
  feature the issue does not ask for.

## Files I'll touch

- `rag/generator/output_parser.py`
- `tests/unit/test_output_parser.py`

## Approach

1. In `parse_review_output`, at both places that call `_parse_json_output(data)`
   (fenced JSON and raw JSON), only call it when `isinstance(data, dict)`.
   Otherwise log a warning and fall through to `_parse_plaintext_output(raw)`.
2. In the test file, remove the `@pytest.mark.xfail(strict=True, ...)`
   decorator from `test_json_array_fallback`. With `strict=True`, leaving it
   would turn the fixed test into a failure.
3. Strengthen the existing array test to check that it returns exactly one
   `general_feedback` section preserving the complete raw text. Add tests
   for empty arrays and scalar JSON (string, number, boolean and null),
   each raw and fenced, with the same preservation assertions.

## Test plan

Re-run my Unit 2 command from the repo root:

```bash
.venv/bin/python -m pytest \
  tests/unit/test_output_parser.py::TestOutputParser::test_raw_json_without_fence \
  tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback \
  --runxfail -v --tb=short
```

- Before the fix: `1 failed, 1 passed`, with the `AttributeError` above.
- After the fix: `2 passed`, exit code 0, no `AttributeError`.
- Run `.venv/bin/python -m pytest tests/unit/test_output_parser.py -v`:
  expect every parser test to pass with no xfail or xpass left, including
  the raw/fenced non-object cases and existing object controls.
- Run `make lint`, Black in check mode, `make typecheck`, and `make test-unit`.
  Record their output; do not change unrelated seeded bugs to make checks pass.

## Thread, repository rules, and callers

On October 4, I read the issue and all 41 comments returned by the GitHub
API. My reproduction is
https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69#issuecomment-5862241610.
The issue asks for array fallback handling and removal of the H-02 xfail.
No owner/member/collaborator reply supplies a different required approach;
classmates' plans do not block my own plan under the course rules.

I read `docs/CONTRIBUTING.md` and `.github/PULL_REQUEST_TEMPLATE.md`.
They require a typed issue-number branch, conventional commits, relevant
tests, and removal of the fixed seeded bug's xfail. They warn against
bulk-fixing deliberately seeded bugs. Neither file states an AI-use
disclosure requirement. This local plan records the AI assistance used.

The production caller in `rag/generator/review_generator.py` consumes
the first returned `FeedbackSection`. The fallback already returns that
type, so the proposed change keeps the existing interface.

## Risks and unknowns

- My posted reproduction covers a raw array and one object control. A
  fenced array and scalars were unverified by that reproduction. The
  same guard followed from code inspection; the added tests now pass
  for raw and fenced arrays and scalars.
- Plain-text fallback preserves array syntax as text rather than
  interpreting array items. That follows the existing fallback behavior;
  a maintainer may prefer a different array representation later.
- The unit tests call the real parser directly and make no model API
  calls. They do not verify end-to-end model behavior.
- Codex helped review and draft this plan and prepare the implementation.
  I have since committed and pushed the two-file fix to my fork.

## Local build verification evidence

These commands and output were saved while testing the local fix before
commit. The tested implementation is now committed and pushed as
`27fa926` on `fix/69-json-array-fallback`.

```text
$ .venv/bin/python -m pytest tests/unit/test_output_parser.py::TestOutputParser::test_raw_json_without_fence tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback --runxfail -v --tb=short
tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback PASSED [100%]

============================== 2 passed in 0.24s ===============================

Exit code: 0

$ .venv/bin/python -m pytest tests/unit/test_output_parser.py -v
tests/unit/test_output_parser.py::TestOutputParser::test_no_suggestions_key PASSED [100%]

============================== 31 passed in 0.23s ==============================

Exit code: 0

$ make lint
.venv/bin/ruff check .
All checks passed!

Exit code: 0

$ .venv/bin/black --check .
All done! ✨ 🍰 ✨
110 files would be left unchanged.

Exit code: 0

$ make typecheck
.venv/bin/mypy api/ core/ ingestion/ rag/ agent/ safety/
Success: no issues found in 76 source files

Exit code: 0

$ make test-unit

-- Docs: https://docs.pytest.org/en/stable/how-to/capture-warnings.html
================= 388 passed, 52 xfailed, 5 warnings in 18.50s =================

Exit code: 0

```

## Deviations

The committed fix follows the planned implementation: guards at both JSON
call sites, the H-02 xfail removed, and tests for raw/fenced arrays and
scalars that preserve the complete input. No implementation scope changed.

There is an order deviation: Codex prepared and tested the local draft
before my plan comment was posted because GitHub CLI was not signed in.
The assignment asks for the plan to be posted before building; this
local preparation happened out of order. I subsequently posted my plan:
https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69#issuecomment-5986337476

The two-file fix is now committed as `27fa9264a8426c7675887ce3503e860835c19b61` and pushed to
my fork on `fix/69-json-array-fallback`:
https://github.com/anushacodes/pathreview-ai301-fa26-s3/tree/fix/69-json-array-fallback

`plan.md` and `comment.md` were kept out of the fix commit. No pull
request has been opened yet; that is the Unit 4 step.

The original two-test reproduction now reports 2 passed in 0.24s.
The parser file has 31 passing tests. The complete unit suite reports
388 passed, 52 xfailed, and 5 warnings. Lint, Black check, and mypy pass.
Black initially requested formatting in the new parametrized test; that
file was formatted and the parser tests, lint, and format check rerun.
Integration and frontend checks were not run; these remain PR-stage checks.
