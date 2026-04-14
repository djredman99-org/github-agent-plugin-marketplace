# Skill: File Operations

## Overview

The **File Operations** skill enables an agent to read, write, move, rename, and delete files within the workspace. All operations are scoped to the current workspace and respect `.gitignore` rules.

## Capabilities

| Capability | Description |
|-----------|-------------|
| Read file | Returns the full or partial content of a file |
| Write file | Creates or overwrites a file with new content |
| Append to file | Appends content to an existing file without overwriting it |
| Move / rename file | Moves or renames a file within the workspace |
| Delete file | Permanently removes a file (prompts for confirmation by default) |
| List directory | Lists the files and subdirectories within a given path |
| Search in files | Performs a full-text or regex search across workspace files |

## Inputs

- **Operation** (required) – one of `read`, `write`, `append`, `move`, `delete`, `list`, `search`.
- **Path** (required) – relative path within the workspace.
- **Content** (required for `write`/`append`) – the text to write or append.
- **Destination** (required for `move`) – the target path.
- **Pattern** (required for `search`) – a string or regex pattern.

## Outputs

Varies by operation:

```json
// read
{ "path": "src/utils.ts", "content": "export function add(a: number, b: number) {…}" }

// list
{ "path": "src/", "entries": ["index.ts", "utils.ts", "services/"] }

// search
{ "pattern": "TODO", "matches": [{ "file": "src/utils.ts", "line": 12, "text": "// TODO: add validation" }] }
```

## Safety Rules

- The agent will **never** delete files outside the workspace root.
- Write and delete operations on files tracked by Git will display a confirmation prompt before proceeding.
- Binary files (images, compiled artefacts) are read-protected by default.

## Example Usage

```
@agent read the contents of src/config.ts
@agent search all TypeScript files for the string "deprecated"
@agent move src/helpers/utils.ts to src/shared/utils.ts
```

## Configuration

```yaml
skills:
  - name: file-operations
    description: Reads, writes, moves, and searches files within the workspace
    parameters:
      confirmBeforeDelete: true
      confirmBeforeOverwrite: true
      respectGitignore: true
```
