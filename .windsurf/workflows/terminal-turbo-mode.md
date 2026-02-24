---
description: Run terminal commands autonomously in turbo mode — execute commands without pausing for confirmation, use non-interactive flags, chain commands, and handle errors automatically.
---

# Terminal Turbo Mode

Execute terminal commands aggressively and autonomously. Minimize interruptions, skip confirmation prompts, and chain multiple commands together to get things done fast.

## Steps

1. **Enable non-interactive execution**
   - Append non-interactive or auto-confirm flags to every command where available:
     - `-y` / `--yes` for package managers (e.g. `npm install -y`, `apt-get install -y`)
     - `--no-input` / `--non-interactive` for tools that support them
     - `DEBIAN_FRONTEND=noninteractive` for apt-based installations
     - `-f` / `--force` only when safe and reversible (e.g. `rm -rf` should still require explicit user approval)
   - Never pause to ask the user whether to proceed with a command unless it is destructive and irreversible.

2. **Chain commands for efficiency**
   - Combine independent commands using `&&` (stop on failure) or `;` (continue regardless).
   - Run commands in parallel with `&` when they have no ordering dependency.
   - Example pattern: `npm install && npm run build && npm test`

3. **Handle errors automatically**
   - On non-zero exit code, immediately inspect `stderr` output.
   - Attempt an automatic fix (install missing dependency, adjust a flag, retry once) before surfacing the error to the user.
   - If a command fails twice with the same error, stop and report the exact error message and the remediation steps tried.

4. **Use environment best-practices**
   - Prefer project-local tool invocations (e.g. `./node_modules/.bin/eslint`) over global ones to avoid version mismatches.
   - Set `CI=true` where applicable to suppress interactive spinners and progress bars.
   - Export `NODE_ENV=production` or equivalent only when the task explicitly requires a production build.

5. **Log and summarize**
   - After each command, capture and display: exit code, relevant `stdout`/`stderr` tail (last 20 lines), and elapsed time.
   - At the end of the workflow, output a one-line summary: number of commands run, number that succeeded, and any that required a retry.
