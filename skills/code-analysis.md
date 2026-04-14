# Skill: Code Analysis

## Overview

The **Code Analysis** skill gives an agent the ability to statically examine source code and report on quality, complexity, potential bugs, and style violations.

## Capabilities

| Capability | Description |
|-----------|-------------|
| Complexity analysis | Calculates cyclomatic complexity for functions and flags those that exceed the threshold |
| Dependency audit | Lists third-party dependencies and highlights outdated or vulnerable packages |
| Dead code detection | Identifies unused imports, variables, and functions |
| Style checking | Validates code against the project's linter rules (ESLint, pylint, etc.) |
| Duplication detection | Finds copy-pasted code blocks that should be extracted into shared utilities |

## Inputs

- **Source file(s) or directory path** – the code to be analysed.
- **Analysis scope** (optional) – one of `quick`, `standard` (default), or `deep`.
- **Severity threshold** (optional) – minimum severity to report: `info`, `warning`, `error`.

## Outputs

A structured report containing:

```json
{
  "summary": {
    "total_issues": 12,
    "critical": 1,
    "high": 3,
    "medium": 6,
    "low": 2
  },
  "issues": [
    {
      "file": "src/utils.ts",
      "line": 42,
      "severity": "high",
      "rule": "complexity",
      "message": "Function 'processOrder' has a cyclomatic complexity of 18 (threshold: 10).",
      "suggestion": "Extract the discount and tax calculation into separate functions."
    }
  ]
}
```

## Example Usage

```
@agent analyse the code in src/services/ and report any high-severity issues
```

## Configuration

Add the following to your agent manifest to enable this skill:

```yaml
skills:
  - name: code-analysis
    description: Statically analyses source code for quality, complexity, and style issues
    parameters:
      scope: standard
      severityThreshold: warning
```
