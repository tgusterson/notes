# Git Reference

Config: `~/.gitconfig`

---

## Aliases

```sh
git recent    # graph of all branches from the last week, with author and relative time
```

---

## Identity: Work vs Personal

Git uses conditional includes to switch identity based on repo location.

| Directory | Identity |
|-----------|----------|
| Everything (default) | `thom@proworkflow.com` — work identity |
| `~/.dotfiles/`, `~/other-repos/`, `~/notes/` | `thomgusterson@gmail.com` — personal identity |

Personal config is at `~/.gitconfig-personal` (overrides user name, email, and disables commit template).

---

## Commit Template

Work repos use a commit template at `~/.git-commit-template.txt`.
Personal repos (see above) override this with `/dev/null` — no template.

---

## Repo-local Gitignore (notes)

The notes repo has its own `.gitignore` at `~/notes/.gitignore`.

Current patterns:
```
pwf-*
```
Files prefixed with `pwf-` are kept local — never pushed to the remote.

---

## Commands & Examples

### Push safely (force-with-lease)

Safer than `--force` — refuses to overwrite if the remote has commits you haven't fetched yet.

```sh
git push --force-with-lease
```

### Interactive add (stage hunks, not whole files)

```sh
git add -i       # full interactive menu
git add -p       # jump straight to hunk-by-hunk patching (most useful)
```

In patch mode: `y` accept, `n` skip, `s` split hunk, `e` edit manually, `q` quit.

### Rebase

```sh
git rebase main                   # replay current branch on top of main
git rebase -i HEAD~3              # interactive: reorder/squash/edit last 3 commits
git rebase --abort                # bail out entirely
git rebase --continue             # after resolving a conflict mid-rebase
```

Interactive rebase verbs: `pick`, `squash` (meld into previous), `fixup` (squash, discard message), `reword`, `drop`.

### Merge conflicts

```sh
git status                        # see which files are conflicted
git diff                          # show conflict markers inline
```

After editing the conflicted files:

```sh
git add <file>                    # mark as resolved
git commit                        # complete the merge
# or, if rebasing:
git rebase --continue
```

To just take one side wholesale:

```sh
git checkout --ours <file>        # keep your version
git checkout --theirs <file>      # take the incoming version
```

Abort and start over:

```sh
git merge --abort
git rebase --abort
```

### switch vs checkout (branches)

`git switch` is the modern, focused replacement for branch operations. Prefer it.

```sh
git switch my-branch              # switch to existing branch
git switch -c new-branch          # create and switch
git switch -                      # switch back to previous branch
```

`git checkout` still owns file/path operations (no `switch` equivalent):

```sh
git checkout -- <file>            # discard unstaged changes to a file
git checkout --ours <file>        # (conflict resolution — see above)
```

### Fetch

```sh
git fetch --all --prune           # fetch all remotes, delete local refs to deleted remote branches
git fetch origin main             # fetch a specific branch without switching to it
```

`--prune` is worth making a habit — keeps your remote-tracking branches clean.

### Log

```sh
git log --oneline                 # compact, one line per commit
git log --oneline --graph         # ASCII branch graph
git log --oneline --graph --all   # include all branches, not just current
git log --stat                    # show files changed per commit
git log -p                        # show full diff per commit
git log --author="Thom"           # filter by author
git log --since="1 week ago"      # filter by date
git log --grep="fix"              # search commit messages
git log main..HEAD                # commits on current branch not yet in main
git log -- <file>                 # history for a specific file
```

Useful combo — compact graph of everything:

```sh
git log --oneline --graph --all --decorate
```

(This is roughly what `git recent` does, scoped to the last week.)

### Reflog

The reflog is a local safety net — a log of everywhere HEAD has pointed, even after resets, rebases, or deleted branches. It's how you undo things that seem permanent.

```sh
git reflog                        # show the full HEAD history
git reflog show my-branch         # reflog for a specific branch
```

Output looks like:

```
abc1234 HEAD@{0}: commit: add feature
def5678 HEAD@{1}: rebase: pick commit
789abcd HEAD@{2}: checkout: moving to main
```

To recover — find the entry you want, then:

```sh
git checkout HEAD@{2}             # inspect it (detached HEAD)
git switch -c recovered-branch HEAD@{4}   # recover as a new branch
git reset --hard HEAD@{1}         # reset current branch back to that point
```

Common scenarios:

- **Undid a reset you regret** — `git reflog` to find the commit before the reset, then `git reset --hard <hash>`
- **Deleted a branch by accident** — find the last commit on it in reflog, `git switch -c <name> <hash>`
- **Rebase went wrong** — find the pre-rebase entry (labelled `rebase: start`), reset back to it

Reflog entries expire after 90 days by default — it's local only, never pushed.
