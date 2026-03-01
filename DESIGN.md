# Design Document: ssh-cli

This document outlines the technical architecture for `ssh-cli`, focusing on terminal multiplexing and secure storage.

## 1. Terminal Multiplexing (The "MobaXterm" Experience)

To achieve a "multi-tab" feel within the CLI, `ssh-cli` will leverage `tmux` as its backend engine.

### Workflow:
-   **Session Launching**: When a user connects to a session, `ssh-cli` checks if a `tmux` session named `ssh-cli` exists.
-   **Window Management**: Each new SSH connection is opened as a new **window** or **pane** within the `ssh-cli` tmux session.
-   **UI Wrapper**: The tool can provide a status bar or a sidebar (using `blessed` or `ink`) to navigate between these "tabs" if not using native tmux shortcuts.

## 2. Credential Storage

Security is paramount for a session manager.

### Implementation:
-   **Storage Path**: `~/.config/ssh-cli/sessions.json` (or encrypted binary).
-   **Encryption**: `crypto` module (AES-256-GCM).
-   **Key Derivation**: `scrypt` or `pbkdf2` from a user-provided master password.
-   **Keyring Integration (Optional)**: Support for `keytar` to use system keychains (macOS Keychain, Windows Credential Vault, Secret Service).

## 3. Tech Stack

-   **Runtime**: Node.js
-   **CLI Framework**: `commander` or `yargs`.
-   **Interactive UI**: `inquirer` or `enquirer` for forms; `fzf-lite` for searching.
-   **Terminal UI**: `ink` (React-based CLI) for the dashboard.
-   **SSH Client**: Native `ssh` command (spawned as a process) for best compatibility and agent support.
