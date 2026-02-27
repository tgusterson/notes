# Notes

A flat collection of markdown notes, organised by filename prefix.

## Prefixes

| Prefix | Purpose | Examples |
|--------|---------|---------|
| `cs-` | Programming concepts, algorithms, language-specific behaviour | `cs-recursion.md`, `cs-js-hoisting.md`, `cs-go-goroutines.md` |
| `ref-` | Tool and command cheat sheets | `ref-docker.md`, `ref-git.md`, `ref-tmux.md` |
| `env-` | Personal environment — tools installed, config, setup reminders | `env-tools.md`, `env-terminal.md` |
| `pwf-` | Work notes (gitignored, local only) | `pwf-project-x.md` |

## Conventions

- **Filenames are lowercase kebab-case.** e.g. `cs-js-hoisting.md`, not `CS-JS-Hoisting.md`.
- **One concept per file.** A note about hoisting is `cs-js-hoisting.md`, not a section in a large `lang-javascript.md`.
- **Language-specific `cs-` notes** include the language in the filename: `cs-js-`, `cs-python-`, `cs-go-` etc.
- **`env-`** is for your own setup — things you might forget you have installed, or how something in your environment works. Not a general tool reference (that's `ref-`).
- **`pwf-`** files are listed in `.gitignore` and never leave this machine.
