# Neovim Setup

Config: `~/.config/nvim/` (managed via `~/.dotfiles/nvim/`).
Plugin manager: **Lazy.nvim**
Leader key: `<space>`

---

## Core Keymaps

| Keymap | Mode | Action |
|--------|------|--------|
| `<leader>y` | n/v | Copy to system clipboard |
| `<leader>cp` | n | Copy current file path to clipboard |
| `<leader>;` | n | Enter command mode (like `:`) |
| `<C-j>` | insert | Leave insert mode and move right (jump past autopaired char) |
| `<Esc>` | n | Clear search highlights |
| `<C-h/j/k/l>` | n | Navigate windows (works with tmux panes too) |
| `\` | n | Toggle Neotree (file tree) |
| `<leader>\` | n | Oil floating file explorer |
| `<leader>vv` | n | Re-source config (`$MYVIMRC`) |
| `<leader>z` | n | Close quickfix list |
| `<M-j>` / `<M-k>` | n | Next / previous quickfix item |

---

## Telescope (Fuzzy Finder)

| Keymap | Action |
|--------|--------|
| `<leader>sf` | Find files |
| `<leader>sg` | Live grep |
| `<leader>sw` | Grep word under cursor |
| `<leader>sb` | Search open buffers |
| `<leader>sr` | Resume last search |
| `<leader>s.` | Recent files |
| `<leader>sh` | Search help tags |
| `<leader>sk` | Search keymaps |
| `<leader>/` | Fuzzy search current buffer |
| `<leader>t` | Open telescope picker |

### Notes-specific
| Keymap | Action |
|--------|--------|
| `<leader>sn` | Live grep in `~/notes` |
| `<leader>en` | Find and open a note by filename |
| `<leader>ni` | Open `inbox.md` directly |

---

## Git (Gitsigns + Lazygit)

| Keymap | Action |
|--------|--------|
| `<leader>gg` | Open Lazygit |
| `<leader>gs` | Stage hunk |
| `<leader>gS` | Stage entire buffer |
| `<leader>gr` | Reset hunk |
| `<leader>gR` | Reset entire buffer |
| `<leader>gp` | Preview hunk |
| `<leader>gb` | Blame current line |
| `<leader>gd` | Diff against index (toggle) |
| `<leader>gD` | Diff against last commit |
| `<leader>gcn` / `<leader>gcp` | Next / previous hunk |
| `<leader>gtb` | Toggle inline blame |
| `<leader>gtd` | Toggle deleted lines preview |

vim-fugitive is also installed for `:Git` commands.

### vim-fugitive essentials

**Git blame**
| Command | Action |
|---------|--------|
| `:Git blame` | Open blame panel (split) |
| `q` | Close blame panel |
| `o` / `O` | Open commit in split / new tab |
| `<CR>` | Jump to commit |

**Diffing**
| Command | Action |
|---------|--------|
| `:Gdiffsplit` | Diff current file against index (side by side) |
| `:Gdiffsplit HEAD` | Diff against last commit |
| `:Gdiffsplit HEAD~1` | Diff against N commits ago |
| `]c` / `[c` | Next / previous diff hunk |
| `do` | Diff obtain — pull change from other side |
| `dp` | Diff put — push change to other side |
| `:diffoff` | Close diff mode |

**General**
| Command | Action |
|---------|--------|
| `:Git` | Interactive status window (stage, commit, push, etc.) |
| `:Git log` | Git log |
| `s` / `u` | Stage / unstage file (in `:Git` status) |
| `cc` | Commit (opens commit message buffer) |

---

## Copilot

| Keymap | Mode | Action |
|--------|------|--------|
| `<C-a>` | insert | Accept full suggestion |
| `<C-l>` | insert | Accept current line only |

Tab is intentionally unbound for copilot — use `<C-a>`.

---

## Reloading Config

| Action | Command |
|--------|---------|
| Re-source `init.lua` | `<leader>sv` or `:source $MYVIMRC` |
| Reload a plugin (re-runs setup) | `:Lazy reload <plugin-name>` e.g. `:Lazy reload render-markdown.nvim` |

> Re-sourcing only re-runs `init.lua` — it won't re-execute plugin `config`/`opts` functions. For plugin changes, use `:Lazy reload`.

---

## Plugins Reference

| Plugin | Purpose |
|--------|---------|
| Telescope | Fuzzy finder for files, grep, buffers, help |
| Neotree | File tree sidebar (`\`) |
| Oil | Edit filesystem like a buffer (`<leader>\`) |
| Gitsigns | Inline git diff, blame, hunk staging |
| Snacks (Lazygit) | TUI git client (`<leader>gg`) |
| vim-fugitive | Git commands via `:Git` |
| Copilot | AI code completion |
| blink.cmp | Completion engine |
| conform | Code formatter |
| nvim-lint | Linting |
| Treesitter | Syntax highlighting |
| which-key | Shows available keymaps after leader |
| undotree | Visual undo history |
| autopairs / autotag | Auto-close brackets and HTML tags |
| render-markdown | Rendered markdown in buffer |
