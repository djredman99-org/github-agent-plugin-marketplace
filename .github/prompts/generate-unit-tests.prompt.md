# Generate Unit Tests Prompt

Generate comprehensive unit tests for the selected code. The tests should be production-quality and ready to commit.

## Requirements

- Use the testing framework already present in the project (Jest for TypeScript/JavaScript, pytest for Python).
- Create one test file per source file, following the existing naming convention (e.g., `*.test.ts`, `*_test.py`).
- Cover all exported/public functions and classes.

## Test Coverage Goals

For each function or method, write tests that cover:

1. **Happy path** – the expected, normal usage.
2. **Boundary conditions** – empty inputs, zero values, maximum values, etc.
3. **Error conditions** – invalid inputs, missing required arguments, thrown exceptions.
4. **Side effects** – verify that mocks/stubs are called with the correct arguments.

## Conventions

- Each test must have a clear, descriptive name using the format:
  - `should <do something> when <condition>` (Jest)
  - `test_<function>_<scenario>` (pytest)
- Group related tests using `describe` blocks (Jest) or test classes (pytest).
- Mock all external dependencies (database, HTTP, file system) to keep tests isolated.
- Do not test implementation details; test observable behaviour.

## Output

Provide the complete test file(s) ready to be saved. Include import statements and any required setup/teardown code.
