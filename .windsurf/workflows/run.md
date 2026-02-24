---
description: Run command without sudo privileges
auto_execution_mode: 3
---

# Run Command

Executes a command as the current non-root user.

## Usage

```
/run [command]
```

## Steps

1. Execute the command as the current user
   ```bash
   {command}
   ```

## Notes

- This workflow runs the command without elevated privileges
- Use this workflow for standard operations that do not require root access
