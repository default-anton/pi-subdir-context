# pi-subdir-context

Automatically load `AGENTS` context (`AGENTS.override.md` or `AGENTS.md`) from subdirectories in [pi](https://github.com/badlogic/pi-mono) coding agent.

## What it does

When you read a file in a subdirectory (e.g., `src/components/Button.tsx`), this extension automatically discovers and injects AGENTS context files in the path hierarchy. `AGENTS.override.md` is treated as `AGENTS.md` and wins when both exist in the same directory, so you get relevant local context without manual loading.

## Installation

```bash
pi install npm:pi-subdir-context
```

Or try it temporarily:

```bash
pi -e npm:pi-subdir-context
```

## How it works

1. When you use the `read` tool, the extension checks the file's directory path
2. It walks up the tree looking for AGENTS context files (`AGENTS.override.md` first, then `AGENTS.md`)
3. Found files are loaded in order (closest to root first)
4. Content is injected into the tool result as additional context
5. Already-loaded files are deduplicated per session

## Example

Project structure:
```
my-project/
├── AGENTS.md                    # project-wide rules
├── src/
│   ├── AGENTS.override.md       # src-specific override
│   └── components/
│       ├── AGENTS.md            # component-specific rules
│       └── Button.tsx
```

When you `read src/components/Button.tsx`, the extension automatically loads subdirectory context (the root AGENTS context is already loaded by pi):
1. `src/AGENTS.override.md` (override beats `src/AGENTS.md`)
2. `src/components/AGENTS.md` (component-specific — closest to file)

## Scope

- Context loading stops at the project root (current working directory)
- Files outside the project or home directory are ignored
- Files are loaded once per session and deduplicated

## License

MIT
