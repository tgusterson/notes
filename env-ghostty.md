# Ghostty Terminal

Config file: `~/.config/ghostty/config`

---

## Current Config

```
font-family = FuraMono Nerd Font
font-size = 14
theme = TokyoNight Night
macos-option-as-alt = true

# Alt+left/right unbound (so tmux/shell can use them)
keybind = alt+left=unbind
keybind = alt+right=unbind

# Shift+Enter sends escape sequence (useful in some terminal apps)
keybind = shift+enter=text:\x1b\r
```

---

## Default Keybindings (macOS)

| Binding | Action |
|---------|--------|
| `cmd+t` | New tab |
| `cmd+n` | New window |
| `cmd+w` | Close tab |
| `cmd+d` | New pane (vertical split) |
| `cmd+shift+d` | New pane (horizontal split) |
| `cmd+[` / `cmd+]` | Navigate panes |
| `cmd+1-9` | Switch to tab by number |
| `cmd+,` | Open config file |
| `cmd+shift+,` | Reload config |

---

## Useful Config Options

```
# Fonts
font-family = <name>        # use 'ghostty +list-fonts' to see available
font-size = <number>

# Themes
theme = <name>              # use 'ghostty +list-themes' to see available

# macOS
macos-option-as-alt = true  # makes opt key send Alt (needed for many terminal shortcuts)

# Keybinds
keybind = <key>=<action>    # e.g. keybind = ctrl+shift+t=new_tab
keybind = <key>=unbind      # remove a default binding
keybind = <key>=text:\x1b\r # send raw escape sequence
```

## CLI Commands

```sh
ghostty +list-themes    # list available themes
ghostty +list-fonts     # list available fonts
ghostty +list-keybinds  # list all active keybindings
```
