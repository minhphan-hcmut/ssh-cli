# ssh-cli (Working Name)

A powerful, MobaXterm-inspired SSH session manager for the terminal. Built with Node.js, `ssh-cli` brings structured session management, encrypted credential storage, and a multi-tab experience (via `tmux` integration) to your CLI.

## 🚀 Features

-   **Session Management**: Create, edit, and organize SSH connections into groups/folders.
-   **Multi-Tab Support**: Seamless integration with `tmux` to manage multiple active sessions in a single terminal window.
-   **Secure Credentials**: Encrypted local storage for passwords and SSH keys.
-   **Quick Connect**: Fuzzy-search through your sessions to connect in seconds.
-   **Import/Export**: Easily move your session configurations between machines.

## 🛠 Installation

```bash
npm install -g @your-username/ssh-cli
```

## 📖 Quick Start

```bash
# Add a new session
ssh-cli add "Production DB" --host 192.168.1.10 --user admin --group DBs

# List all sessions
ssh-cli list

# Connect to a session
ssh-cli connect "Production DB"

# Search and connect (Interactive)
ssh-cli
```

## 🔒 Security

Sessions and credentials are encrypted using AES-256-GCM. You will be prompted for a master password upon the first run, which will be used to derive the encryption key.
