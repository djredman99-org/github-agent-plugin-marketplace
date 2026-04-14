# Refactor Code Prompt

Refactor the selected code to improve its design, readability, and maintainability without changing its external behaviour.

## Refactoring Goals

Select all that apply or add your own in the "Custom Goals" section below:

- [ ] Reduce duplication (DRY principle)
- [ ] Improve naming clarity
- [ ] Break up large functions or classes (Single Responsibility Principle)
- [ ] Replace magic numbers/strings with named constants
- [ ] Improve error handling
- [ ] Simplify complex conditional logic
- [ ] Improve performance (specify hotspot if known)
- [ ] Add or improve type annotations
- [ ] Migrate to a newer language feature or API

## Custom Goals

<!-- Describe any specific refactoring goals not listed above -->

## Constraints

- **Do not change observable behaviour.** All existing tests must still pass after the refactor.
- Keep the public API (exported function/class signatures) identical unless explicitly asked to change it.
- Preserve existing comments that remain accurate; remove comments that are no longer relevant.
- Make incremental changes so each step is reviewable.

## Output Format

For each change, provide:

1. **What** – A one-line description of the change.
2. **Why** – Why this improves the code.
3. **Before** – The original code snippet.
4. **After** – The refactored code snippet.

End with a diff-style summary or the complete refactored file(s).
