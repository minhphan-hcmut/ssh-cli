# CLI Reference

Detailed guide for `ssh-cli` commands.

## Session Management

### `add`
Add a new SSH session.
```bash
ssh-cli add <name> [options]
```
**Options:**
- `--host, -h`: Remote hostname or IP.
- `--user, -u`: SSH username.
- `--port, -p`: SSH port (default: 22).
- `--key, -i`: Path to private key.
- `--group, -g`: Group name for organization.

### `list`
List all saved sessions.
```bash
ssh-cli list [--group <name>] [--json]
```

### `edit`
Modify an existing session.
```bash
ssh-cli edit <name>
```

### `delete` / `rm`
Remove a session.
```bash
ssh-cli rm <name>
```

## Connection

### `connect`
Connect to a saved session.
```bash
ssh-cli connect <name>
```

### `ui`
Open the interactive session browser (default if no command is provided).
```bash
ssh-cli ui
```

## Configuration

### `config`
Manage global settings.
```bash
ssh-cli config set default-user <name>
ssh-cli config set tmux-integration true
```
