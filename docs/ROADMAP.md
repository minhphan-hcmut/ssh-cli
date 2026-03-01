# Project Roadmap: ssh-cli

This roadmap outlines the phased development of `ssh-cli`, a Node.js-based SSH session manager with `tmux` integration and secure credential storage.

---

## 🏗 Phase 1: Foundation (The "Kernel")
*Goal: Establish the CLI structure and basic session management.*

- [ ] **1.1 Project Scaffolding**: Setup `commander.js` or `yargs` for command-line argument parsing.
- [ ] **1.2 Session Storage**: Implement a simple JSON-based storage manager in `~/.config/ssh-cli/sessions.json`.
- [ ] **1.3 Basic Commands**:
    - `ssh-cli add <name> --host <ip> --user <user>`: Save a new session.
    - `ssh-cli list`: Display all saved sessions in a table.
    - `ssh-cli rm <name>`: Delete a session.
- [ ] **1.4 Direct Connection**: Implement the `connect <name>` command that spawns a native `ssh` child process.

## 🔐 Phase 2: Security (The "Vault")
*Goal: Protect sensitive credentials using encryption.*

- [ ] **2.1 Master Password**: Implement a one-time setup to prompt for a master password.
- [ ] **2.2 Encryption Engine**: Use Node's `crypto` module (AES-256-GCM) to encrypt/decrypt the `sessions.json` file.
- [ ] **2.3 Key Derivation**: Use `scrypt` or `pbkdf2` to derive a secure encryption key from the user's master password.
- [ ] **2.4 Password Handling**: Securely prompt for the master password when the CLI is invoked (similar to `sudo`).

## 🪟 Phase 3: Multi-Tab Experience (The "Multiplexer")
*Goal: Integrate with `tmux` to provide a "tabbed" interface like MobaXterm.*

- [ ] **3.1 Environment Check**: Detect if `tmux` is installed on the host system.
- [ ] **3.2 Session Persistence**: Logic to create or attach to a dedicated `tmux` session (e.g., `ssh-cli-hub`).
- [ ] **3.3 Intelligent Connect**: Modify `connect` to open new SSH sessions as `tmux` windows or panes rather than replacing the current process.
- [ ] **3.4 Window Naming**: Automatically name `tmux` windows based on the session name (e.g., "Prod-DB", "Web-01").

## 🖥 Phase 4: Interactive UI (The "Dashboard")
*Goal: Provide a visual, searchable interface for managing sessions.*

- [ ] **4.1 Fuzzy Search**: Integrate `inquirer` or `enquirer` with a fuzzy-search plugin for quick session selection.
- [ ] **4.2 Grouping Logic**: Support hierarchical grouping (e.g., `Production/Database`) and allow filtering by group.
- [ ] **4.3 Interactive Dashboard**: (Optional) Use `ink` (React-based CLI) to build a persistent dashboard showing active connections and server status.

## 🚀 Phase 5: Advanced Features (The "Power User")
*Goal: Professional-grade utilities for efficiency.*

- [ ] **5.1 Multi-Exec**: Send a single command to multiple sessions simultaneously (utilizing `tmux set-window-option synchronize-panes`).
- [ ] **5.2 Import/Export**: Tools to import from `~/.ssh/config` or export to CSV/JSON.
- [ ] **5.3 Key Management**: Automated SSH key generation and `ssh-copy-id` integration.
- [ ] **5.4 Custom Styling**: Support for themes and custom terminal colors per session/group.
