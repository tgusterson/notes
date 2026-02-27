# Installed CLI Tools

Managed via Homebrew. To reinstall everything: run `~/.dotfiles/install.sh`.

| Tool | Purpose |
|------|---------|
| `bat` | `cat` replacement with syntax highlighting. Use instead of `cat`. Theme: `tokyonight_night`. |
| `glow` | Terminal markdown renderer. Used by `sn` to render `.md` files in the fzf preview window. |
| `fzf` | Fuzzy finder. Integrated into zsh (replaces `**` tab completion) and nvim. Use instead of `find`. |
| `ripgrep` (`rg`) | Fast grep. Used by telescope and the `ns` note search function. |
| `tldr` | Simplified man pages with examples. Try this before writing a ref- note. |
| `lazygit` | TUI git client. Launch from nvim with `<leader>gg` or run `lazygit` in terminal. |
| `neovim` | Editor. Config at `~/.config/nvim/` (see `env-nvim.md`). |
| `tmux` | Terminal multiplexer. Config at `~/.tmux.conf` (see `env-tmux.md`). |
| `stow` | Dotfile symlink manager. Used by install.sh to link `~/.dotfiles` into `$HOME`. |
| `powerlevel10k` | Zsh prompt theme. Reconfigure with `p10k configure`. |
| `tree-sitter` | Parser generator used by neovim for syntax highlighting. |
| `pyenv` | Python version manager. |
| `nvm` | Node version manager. |
| `pnpm` | Fast Node package manager. |

## Zsh Functions & Aliases

Defined in `~/.dotfiles/zsh/.zshrc`.

```zsh
note [filename]        # open ~/notes/<filename>.md in nvim (defaults to inbox.md)
sn [query]             # search notes with rg+fzf, open result in nvim at matching line
inv                    # pick a file with fzf (bat preview) and open in nvim
vim                    # aliased to nvim
start_my_day           # runs ~/start_my_day.sh
```

## FZF

fzf is wired into the shell automatically. Key behaviours:
- `<ctrl-r>` — fuzzy search shell history
- `<ctrl-t>` — fuzzy find files in current dir
- `**<tab>` — trigger fuzzy completion in any command (e.g. `cd **<tab>`)
- File preview uses `bat` (syntax highlighted, first 500 lines)
