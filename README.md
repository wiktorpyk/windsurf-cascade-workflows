# windsurf-cascade-workflows

A collection of reusable [Windsurf Cascade](https://codeium.com/windsurf) workflows.

## Workflows

### `/terminal-turbo-mode`

**File:** [`.windsurf/workflows/terminal-turbo-mode.md`](.windsurf/workflows/terminal-turbo-mode.md)

Runs terminal commands autonomously with minimal interruptions. Enables non-interactive flags, chains commands for efficiency, handles errors automatically, and outputs a summary at the end.

**Usage:** Open the Cascade panel in Windsurf and type `/terminal-turbo-mode`.

## Adding Workflows

Place a Markdown file inside `.windsurf/workflows/` with a YAML front-matter block containing at least a `description` field. Cascade will automatically pick it up as a slash command.