# Debug Issue Prompt

Help me investigate and resolve the bug or unexpected behaviour described below. Walk through the analysis step-by-step.

## Issue Description

<!-- Replace this section with the actual bug description or paste the error message/stack trace -->

```
<paste error message or describe the unexpected behaviour here>
```

## Debugging Steps

Work through the following process:

1. **Reproduce** – Identify the minimal inputs or steps needed to trigger the issue.
2. **Isolate** – Narrow down which file, function, or line is the root cause.
3. **Hypothesise** – List the most likely causes ranked by probability.
4. **Verify** – For each hypothesis, suggest a targeted test or log statement to confirm it.
5. **Fix** – Provide the corrected code with an explanation of why the original code was wrong.
6. **Prevent** – Recommend a unit test that would have caught this bug, and suggest any defensive coding changes.

## Constraints

- Do not change unrelated code.
- Prefer the smallest possible fix that resolves the root cause.
- If multiple approaches exist, explain the trade-offs before recommending one.

## Output

- Corrected code snippet(s) with inline comments explaining the changes.
- A short summary of the root cause.
- A suggested regression test.
