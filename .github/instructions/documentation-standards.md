# Documentation Standards

These standards define how documentation should be written and maintained across this repository. Good documentation reduces onboarding time, prevents misuse of APIs, and makes the codebase more maintainable.

## Scope

Documentation is required for:

- All public functions, classes, methods, and modules.
- All REST API endpoints and message queue payloads.
- All environment variables and configuration options.
- All significant architectural decisions (captured as ADRs).
- The repository itself (README.md at the root).

## Inline Code Documentation

### TypeScript / JavaScript (JSDoc)

```typescript
/**
 * Calculates the total price including tax for a given order.
 *
 * @param subtotal - The pre-tax order total in the smallest currency unit (e.g., cents).
 * @param taxRatePercent - The tax rate as a percentage (e.g., 8.5 for 8.5%).
 * @returns The total price including tax, rounded to the nearest whole unit.
 * @throws {RangeError} If `subtotal` is negative or `taxRatePercent` is not between 0 and 100.
 *
 * @example
 * ```typescript
 * const total = calculateTotal(1000, 8.5); // returns 1085
 * ```
 */
export function calculateTotal(subtotal: number, taxRatePercent: number): number { … }
```

### Python (Google-style docstrings)

```python
def calculate_total(subtotal: int, tax_rate_percent: float) -> int:
    """Calculates the total price including tax for a given order.

    Args:
        subtotal: The pre-tax order total in the smallest currency unit (e.g., cents).
        tax_rate_percent: The tax rate as a percentage (e.g., 8.5 for 8.5%).

    Returns:
        The total price including tax, rounded to the nearest whole unit.

    Raises:
        ValueError: If subtotal is negative or tax_rate_percent is outside [0, 100].

    Example:
        >>> calculate_total(1000, 8.5)
        1085
    """
```

## README Structure

Every module or service repository must have a README.md with the following sections in order:

1. **Title and one-line description**
2. **Badges** (build status, coverage, licence)
3. **Overview** – What does this project do, and why does it exist?
4. **Quick Start** – Minimal steps to get a working instance running locally.
5. **Installation** – Detailed installation instructions.
6. **Configuration** – All environment variables and configuration options, in a table.
7. **Usage** – Common usage examples with code snippets.
8. **API Reference** – Link to or embed the API docs.
9. **Contributing** – Link to `CONTRIBUTING.md`.
10. **Licence**

## Architecture Decision Records (ADRs)

Store ADRs in `docs/adr/`. Use the following format:

```markdown
# ADR-<number>: <Title>

**Date:** YYYY-MM-DD  
**Status:** Proposed | Accepted | Deprecated | Superseded by ADR-<number>

## Context
What is the situation that motivated this decision?

## Decision
What was decided?

## Consequences
What are the positive and negative outcomes of this decision?
```

## Writing Style

- **Active voice:** Write "The function validates the token" not "The token is validated by the function".
- **Present tense:** Write "Returns the user object" not "Will return the user object".
- **Second person:** Address the reader as "you" – "You can configure the timeout by setting…".
- **Sentence length:** Keep sentences under 25 words where possible.
- **Paragraphs:** One idea per paragraph; blank line between paragraphs.
- **Headings:** Use title case for top-level headings (`## Overview`), sentence case for lower levels (`### Configuration options`).

## Keeping Documentation Current

- Documentation updates must be included in the same PR as the code change that necessitates them.
- Outdated documentation is treated with the same severity as a bug – file an issue and fix it promptly.
- Run a link checker in CI to catch broken hyperlinks in Markdown files.
