# GitHub Copilot – Workspace Custom Instructions

These instructions apply to all Copilot interactions within this repository. They guide code suggestions, chat responses, and agent behaviours across the workspace.

## General Principles

- Always prefer clarity and readability over cleverness.
- Follow the existing coding conventions and file structure of the project.
- When generating code, include relevant error handling unless told otherwise.
- Avoid hard-coded secrets, credentials, or environment-specific values.
- Favour composition over inheritance and small, focused functions/modules.

## Languages and Frameworks

- Use TypeScript (strict mode) for any JavaScript/Node.js code.
- Use Python 3.10+ with type annotations for all Python code.
- Follow PEP 8 for Python and the Airbnb style guide for TypeScript/JavaScript.
- Prefer async/await over callbacks or raw Promise chains.

## Testing

- All new functions and classes must have corresponding unit tests.
- Use Jest for TypeScript/JavaScript tests and pytest for Python tests.
- Test names must clearly describe the behaviour being verified.
- Aim for at least 80% code coverage on new code.

## Documentation

- Every public function, class, and module must have a doc-comment.
- Use JSDoc for TypeScript/JavaScript and Google-style docstrings for Python.
- Keep comments concise and focused on *why*, not *what*.

## Security

- Never generate code that stores plain-text passwords or secrets.
- Always validate and sanitise user input before use.
- Prefer established libraries for cryptography, authentication, and HTTP.
- Flag any potential security concerns with an inline `// SECURITY:` comment.

## Accessibility

- When generating HTML or UI components, include ARIA attributes and semantic elements.
- Ensure colour contrast meets WCAG 2.1 AA standards.
