# 🧰 tmux Beginner’s Guide

> A complete guide for **beginners** to master `tmux` — starting from the most **practical use cases** to the most **advanced features**.

---

## 📌 What Is tmux?

**tmux** is a **terminal multiplexer** — it lets you manage multiple terminal sessions **from a single window**. This means you can:

- Keep processes running in the background
- Detach and reattach to sessions later
- Split your terminal into panes
- Manage multiple windows inside one terminal

---

## ⚙️ Installation

### Ubuntu/Debian:
```bash
sudo apt install tmux
```

### macOS (Homebrew):
```bash
brew install tmux
```

---

## 🥇 1. Start and Detach Sessions

### ✅ Start a new tmux session
```bash
tmux
```

### ✅ Start with a session name
```bash
tmux new -s mysession
```

### ✅ Detach (leave without killing the session)
- `Ctrl+b`, then `d`

### ✅ List all sessions
```bash
tmux ls
```

### ✅ Reattach to a session
```bash
tmux attach -t mysession
```

### ✅ Kill a session
```bash
tmux kill-session -t mysession
```

---

## 🥈 2. Window Management (like tabs)

### ✅ Create a new window
- `Ctrl+b`, then `c`

### ✅ Switch between windows
- `Ctrl+b`, then `n` → next window  
- `Ctrl+b`, then `p` → previous window  
- `Ctrl+b`, then number (e.g., `0`, `1`) → jump to window

### ✅ Rename a window
- `Ctrl+b`, then `,`

### ✅ List all windows
- `Ctrl+b`, then `w`

---

## 🥉 3. Pane Management (split-screen terminals)

### ✅ Split vertically
- `Ctrl+b`, then `%`

### ✅ Split horizontally
- `Ctrl+b`, then `"`

### ✅ Switch between panes
- `Ctrl+b`, then arrow keys

### ✅ Resize panes
- `Ctrl+b`, then `:`  
Then type:
```bash
resize-pane -L 10  # or -R, -U, -D
```

(Or hold `Alt` + arrow keys if supported)

### ✅ Close a pane
- `exit` or `Ctrl+d` inside the pane

---

## 🏗️ 4. Persistent Workflows (long-running tasks)

Perfect for:

- Remote SSH sessions
- Background scripts or servers
- Reconnecting later without losing state

```bash
tmux new -s myjob
# run your server
Ctrl+b d  # detach
# come back later
tmux attach -t myjob
```

---

## 🧪 5. Session Sharing (multi-user or multi-terminal)

Let two terminals or SSH users share a session:

```bash
tmux attach -t sharedsession
```

> Requires shared user login or shared socket setup.

---

## ⚡ 6. Copy Mode (scroll & copy terminal text)

### ✅ Enter copy mode
- `Ctrl+b`, then `[`  

### ✅ Move around
- Arrow keys or `vi` style (`h`, `j`, `k`, `l`)

### ✅ Start selecting
- Press `Space`, move, then `Enter` to copy

### ✅ Paste last copied text
- `Ctrl+b`, then `]`

---

## 🧭 7. Configuring tmux (`.tmux.conf`)

Create `~/.tmux.conf` for custom behavior:

```bash
# Use Ctrl+a instead of Ctrl+b
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix

# Enable mouse
set -g mouse on

# Scrollback buffer
set -g history-limit 10000
```

### ✅ Reload config
```bash
tmux source-file ~/.tmux.conf
```

---

## 🔧 8. Advanced Features (optional)

- **Named panes/windows** for automation
- **tmuxinator / teamocil**: project layouts
- **Hooks**: execute on events (e.g. `on-detach`)
- **Plugins** with TPM:

```bash
set -g @plugin 'tmux-plugins/tmux-resurrect'
run '~/.tmux/plugins/tpm/tpm'
```

---

## 🧵 9. Summary of Commands

| Action                    | Shortcut / Command         |
|--------------------------|----------------------------|
| Start session            | `tmux new -s name`         |
| Detach                   | `Ctrl+b d`                 |
| List sessions            | `tmux ls`                  |
| Attach to session        | `tmux attach -t name`      |
| New window               | `Ctrl+b c`                 |
| Split horizontally       | `Ctrl+b "`                 |
| Split vertically         | `Ctrl+b %`                 |
| Move between panes       | `Ctrl+b` then arrows       |
| Resize panes             | `Ctrl+b : resize-pane`     |
| Rename window            | `Ctrl+b ,`                 |
| Scroll/copy mode         | `Ctrl+b [`                 |

---

## 🧠 Pro Tips

- Combine tmux with `ssh` for remote workflow persistence
- Use mouse mode for easier interaction: `set -g mouse on`
- Set up plugins for backups, logging, and layout restoration

---

## 📎 License

MIT License

---

## ✍️ Author

This guide was generated with ❤️ by [ChatGPT](https://openai.com/chatgpt) for tmux beginners.