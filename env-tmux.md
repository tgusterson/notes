# Tmux Setup

Config: `~/.tmux.conf` (managed via `~/.dotfiles/tmux/`).
Prefix: `C-s` (not the default `C-b`)

---

## Key Bindings

| Binding | Action |
|---------|--------|
| `prefix + r` | Reload tmux config |
| `prefix + h/j/k/l` | Navigate panes (vim-style) |
| `C-h/j/k/l` | Navigate panes **without prefix** (via vim-tmux-navigator — also works across nvim splits) |
| `C-M-l` | Clear terminal (no prefix needed) |
| `prefix + [` | Enter copy mode |

### Copy Mode (vi keys)
Mouse drag selection is automatically copied to clipboard via `pbcopy`. No extra step needed.

---

## Session / Window Management

These are standard tmux — prefix is `C-s`:

| Binding | Action |
|---------|--------|
| `prefix + c` | New window |
| `prefix + ,` | Rename window |
| `prefix + n` / `prefix + p` | Next / previous window |
| `prefix + 0-9` | Switch to window by number |
| `prefix + %` | Split pane vertically |
| `prefix + "` | Split pane horizontally |
| `prefix + x` | Kill current pane |
| `prefix + d` | Detach session |
| `prefix + $` | Rename session |
| `prefix + s` | List / switch sessions |

---

## Plugins (TPM)

| Plugin | Purpose |
|--------|---------|
| `tmux-plugins/tpm` | Plugin manager. Install plugins: `prefix + I`. Update: `prefix + U`. |
| `christoomey/vim-tmux-navigator` | Unified `C-h/j/k/l` navigation across tmux panes and nvim splits |
| `fabioluciano/tmux-tokyo-night` | Tokyo Night status bar theme (night variant) |

Status bar is at the **top**. Shows date/time (`dd-mm-yyyy HH:MM`).
