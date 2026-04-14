# Write Documentation Prompt

Generate clear, accurate documentation for the selected code, module, or feature. The documentation must be aimed at the appropriate audience (developer, end-user, or both) and follow project conventions.

## Scope

Based on the selected context, produce one or more of the following:

- **Inline doc-comments** – JSDoc for TypeScript/JavaScript, Google-style docstrings for Python.
- **Module / file header** – Brief description, author, and any important caveats.
- **README section** – Markdown prose explaining purpose, usage, and examples.
- **API reference** – Parameter names, types, return values, and thrown errors.

## Guidelines

- Use plain, precise language. Avoid jargon unless the audience is highly technical.
- Every public function and class must be documented.
- Include at least one concrete usage example per public API.
- Document expected input ranges, side effects, and any known limitations.
- Keep doc-comments in sync with the implementation – do not copy-paste stale descriptions.

## Output Format

### For code doc-comments
Embed the comments directly in the code snippet and show the full updated function/class.

### For README sections
Provide a Markdown block that can be pasted directly into the project README, with appropriate headings.

### For API references
Use a structured table or definition list:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name`    | `string` | Yes | ... |
