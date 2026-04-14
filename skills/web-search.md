# Skill: Web Search

## Overview

The **Web Search** skill allows an agent to query the web for up-to-date information, documentation, or research and incorporate the results into its response.

## Capabilities

| Capability | Description |
|-----------|-------------|
| General search | Searches the web for a given query and returns summarised results |
| Documentation lookup | Finds official documentation pages for libraries, frameworks, or APIs |
| Error lookup | Searches for solutions to a specific error message or stack trace |
| CVE / security advisory lookup | Retrieves known vulnerabilities for a package and version |
| Changelog lookup | Finds release notes and changelogs for a dependency |

## Inputs

- **Query** (required) – the search query in natural language.
- **Mode** (optional) – one of `general` (default), `docs`, `error`, `security`, or `changelog`.
- **Max results** (optional) – maximum number of results to return (default: 5).

## Outputs

A list of search results, each containing:

```json
{
  "results": [
    {
      "title": "Express.js – Error Handling",
      "url": "https://expressjs.com/en/guide/error-handling.html",
      "snippet": "Error handling refers to how Express catches and processes errors that occur both synchronously and asynchronously…",
      "relevance_score": 0.94
    }
  ],
  "summary": "Express error handling relies on middleware with four arguments (err, req, res, next)…"
}
```

## Example Usage

```
@agent search for the latest breaking changes in React 19
@agent look up the CVE for lodash 4.17.20
@agent find the official Python docs for asyncio.gather
```

## Configuration

```yaml
skills:
  - name: web-search
    description: Queries the web for information and returns summarised results
    parameters:
      maxResults: 5
      safeSearch: true
      preferredLanguage: en
```
