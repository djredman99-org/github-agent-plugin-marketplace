# Code Review Prompt

Perform a thorough code review of the selected code or the files listed below. Focus on the following areas and provide structured, actionable feedback.

## Review Checklist

### Correctness
- Are there any logic errors, off-by-one issues, or edge cases not handled?
- Do all functions behave as their names and documentation suggest?
- Are error conditions caught and handled appropriately?

### Readability and Maintainability
- Is the code easy to understand for someone unfamiliar with the context?
- Are variable and function names descriptive and consistent?
- Are there any long functions or classes that should be broken up?

### Performance
- Are there any obvious performance bottlenecks (e.g., N+1 queries, unnecessary loops)?
- Are expensive operations cached where appropriate?

### Security
- Is user input validated and sanitised before use?
- Are secrets and credentials kept out of the code?
- Are there any known vulnerable patterns (e.g., SQL injection, XSS)?

### Test Coverage
- Are there tests for the main code paths, including edge cases and error conditions?
- Do the existing tests actually validate the expected behaviour?

## Output Format

For each finding, respond with:

```
**[Severity: Critical | High | Medium | Low | Info]**
File: `<filename>`, Line(s): <line numbers>
Issue: <description of the problem>
Suggestion: <concrete recommendation or code snippet>
```

End with a brief summary of overall code quality and the top 3 most important items to address.
