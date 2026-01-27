# pi-subdir-context

Automatically load `AGENTS.md` context from subdirectories in [pi](https://github.com/badlogic/pi-mono) coding agent.

## What it does

When you read a file in a subdirectory (e.g., `src/components/Button.tsx`), this extension automatically discovers and injects any `AGENTS.md` files found in the path hierarchy (`src/components/AGENTS.md`, `src/AGENTS.md`), giving pi the relevant local context without manual loading.

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
2. It walks up the tree looking for `AGENTS.md` files
3. Found files are loaded in order (closest to root first)
4. Content is injected into the tool result as additional context
5. Already-loaded files are deduplicated per session

## Example

Project structure:
```
my-project/
├── AGENTS.md           # project-wide rules
├── src/
│   ├── AGENTS.md       # src-specific conventions
│   └── components/
│       ├── AGENTS.md   # component-specific rules
│       └── Button.tsx
```

When you `read src/components/Button.tsx`, the extension automatically loads subdirectory context (the root `AGENTS.md` is already loaded by pi):
1. `src/AGENTS.md` (src-specific)
2. `src/components/AGENTS.md` (component-specific — closest to file)

## Scope

- Context loading stops at the project root (current working directory)
- Files outside the project or home directory are ignored
- Files are loaded once per session and deduplicated

## License

MIT
