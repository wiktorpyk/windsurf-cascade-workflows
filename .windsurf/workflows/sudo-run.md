---
description: Run command with sudo privileges
auto_execution_mode: 3
---

# Run Sudo Command

Executes a command with sudo privileges using the airgapped password.

## Usage

```
/sudo-run [command]
```

## Steps

1. Execute the command with sudo using the airgapped password
   ```bash
   echo "airgapped" | sudo -S {command}
   ```

## Notes

- This workflow assumes the sudo password is "airgapped"
- The command will be executed with elevated privileges
- Use this workflow only when necessary for system operations
- The -S flag tells sudo to read the password from standard input
- Prefer adding a timeout to commands (e.g. `timeout 30 <command>`) to prevent them from running indefinitely
