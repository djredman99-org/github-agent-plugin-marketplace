# Coding Standards

These standards apply to all code in this repository regardless of language or feature area. They complement the language-specific guidelines in adjacent instruction files.

## Naming Conventions

- Use **descriptive**, intention-revealing names. A name should tell you *what* and *why*, not *how*.
- Avoid abbreviations except for universally accepted ones (`id`, `url`, `api`, `html`, `dto`).
- Boolean variables and functions that return booleans should be named with an `is`, `has`, `can`, or `should` prefix (e.g., `isActive`, `hasPermission`).
- Constants should be `SCREAMING_SNAKE_CASE` in JavaScript/TypeScript and Python.
- Avoid generic names like `data`, `info`, `result`, `temp`, `obj`, `val`, or `flag`.

## Functions and Methods

- A function should do **one thing** and do it well (Single Responsibility Principle).
- Keep function bodies short. If a function exceeds 30 lines, consider splitting it.
- Limit the number of parameters to 3. If more are needed, accept an options object/dataclass.
- Functions must not have side effects that are not obvious from their name and signature.
- Return early when possible to reduce nesting depth (guard clauses).
- Prefer pure functions where practical – they are easier to test and reason about.

## Error Handling

- Never swallow exceptions silently. Always log, re-throw, or handle an error meaningfully.
- Distinguish between expected errors (e.g., validation failures) and unexpected errors (e.g., null pointer).
- Use custom error classes/exceptions to carry structured context (error code, message, original cause).
- Always handle the unhappy path explicitly; do not rely on "it won't happen in practice".

## Code Formatting

- Indentation: 2 spaces for TypeScript/JavaScript, 4 spaces for Python.
- Maximum line length: 100 characters.
- No trailing whitespace.
- Files must end with a single newline character.
- Run the project linter before committing – CI will reject un-linted code.

## Imports and Dependencies

- Order imports: standard library → third-party → internal modules.
- Remove unused imports before committing.
- Do not introduce a new dependency unless it is justified and approved in a PR comment.
- Prefer tree-shakeable libraries to keep bundle sizes small.

## Version Control Hygiene

- Commit messages must follow the Conventional Commits format: `<type>(<scope>): <short description>`.  
  Valid types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`.
- Keep commits small and focused. One logical change per commit.
- Do not commit commented-out code, debug `console.log` / `print` statements, or TODO items without a linked issue.
- Branches must be named `<type>/<short-description>` (e.g., `feat/add-payment-retry`, `fix/null-check-in-auth`).
