# Testing Standards

These standards ensure that tests are meaningful, reliable, and maintainable. They apply to all automated tests in this repository.

## Test Frameworks

| Language | Unit / Integration | End-to-End |
|----------|--------------------|------------|
| TypeScript / JavaScript | Jest | Playwright |
| Python | pytest | Playwright / Selenium |

## Naming Conventions

- Test files must be colocated with the source file they test:
  - TypeScript: `src/utils.ts` → `src/utils.test.ts`
  - Python: `src/utils.py` → `tests/test_utils.py`
- Test names must describe the expected behaviour, not the implementation:
  - ✅ `should return 401 when the token is expired`
  - ❌ `test token check`
- Group related tests using `describe` blocks (Jest) or test classes (pytest).

## Coverage Requirements

| Code type | Minimum line coverage |
|-----------|-----------------------|
| Business logic (services, domain) | 90% |
| Utilities and helpers | 85% |
| API route handlers | 80% |
| Data access / repositories | 75% |

Coverage reports are generated in CI. Pull requests that lower overall coverage by more than 2% will require justification.

## Test Design Principles

### Isolation

- Each test must be fully independent and able to run in any order.
- Never share mutable state between tests (no module-level variables that tests mutate).
- Reset all mocks and stubs in `beforeEach` / `afterEach` blocks or pytest fixtures.

### Mocking External Dependencies

- Mock all external dependencies: HTTP calls, databases, file system access, clocks, and random number generators.
- Use dependency injection or module-level mocking to make substitution easy.
- Verify not only return values but also that mocks were called with the correct arguments.

### Assertions

- Every test must have at least one assertion. A test with no assertions is not a test.
- Be specific: prefer `expect(result.status).toBe(404)` over `expect(result).toBeTruthy()`.
- Test one concept per test case. If a test requires a long chain of assertions that test multiple behaviours, split it.

### Test Data

- Use realistic but obviously fake test data (e.g., `user@example.com`, `Test Corp Ltd`).
- Never use production data in tests.
- Use factory functions or builder patterns to create test fixtures to avoid duplication.

## Continuous Integration

- All tests run automatically on every pull request.
- Tests must pass before a PR can be merged.
- Flaky tests must be fixed or quarantined within one sprint of being identified. Quarantined tests must have a linked issue.

## Anti-patterns to Avoid

| Anti-pattern | Why it's bad |
|-------------|-------------|
| Testing implementation details | Makes tests brittle – they break on refactors that don't change behaviour |
| Overly large tests ("god tests") | Hard to understand failures; slow to run |
| Sleeping in tests (`setTimeout`, `time.sleep`) | Slow and flaky; use fake timers instead |
| Assertions in loops without clear failure context | Hard to diagnose which iteration failed |
| Ignoring test warnings | Warnings often become errors in the next version |
