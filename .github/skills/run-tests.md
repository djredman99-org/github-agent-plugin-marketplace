# Skill: Run Tests

## Overview

The **Run Tests** skill enables an agent to execute the project's test suite and report results, including pass/fail counts, coverage metrics, and failure details.

## Capabilities

| Capability | Description |
|-----------|-------------|
| Full test run | Executes all tests in the project |
| Targeted test run | Runs only the tests for a specific file, directory, or test name pattern |
| Coverage report | Generates a code-coverage report and highlights uncovered lines |
| Watch mode | Runs tests in watch mode and re-runs on file changes |
| Failure triage | Summarises failing tests and links them to the responsible source files |

## Inputs

- **Target** (optional) – file path, directory, or test name pattern to narrow the run.
- **Coverage** (optional, boolean) – whether to include coverage reporting (default: `false`).
- **Watch** (optional, boolean) – run in watch mode (default: `false`).

## Outputs

A structured result object:

```json
{
  "status": "failed",
  "summary": {
    "total": 120,
    "passed": 115,
    "failed": 5,
    "skipped": 0,
    "duration_ms": 4321
  },
  "failures": [
    {
      "test": "OrderService > should apply discount for premium users",
      "file": "src/services/order.service.test.ts",
      "line": 87,
      "error": "Expected 90 to equal 85",
      "stack": "..."
    }
  ],
  "coverage": {
    "lines": 82.4,
    "branches": 74.1,
    "functions": 88.0
  }
}
```

## Example Usage

```
@agent run the tests for src/services/order.service.ts and show me the coverage report
```

## Configuration

```yaml
skills:
  - name: run-tests
    description: Executes the project test suite and reports results and coverage
    parameters:
      coverageEnabled: true
      failFast: false
      testCommand: npm test
```
