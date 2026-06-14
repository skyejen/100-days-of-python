# Git learning notes

Personal reference for git commands and situations encountered while learning.

---

## Amending the most recent commit message

When the last commit message has a typo or needs changing:

```
git commit --amend -m "your corrected message here"
git push --force-with-lease
```

`--force-with-lease` is safer than `--force` -- it refuses to push if someone else has pushed to the same branch in the meantime.

---

## Changing older commit messages (interactive rebase)

When you need to fix a message that is NOT the most recent commit:

```
git rebase -i HEAD~N
```

Replace `N` with how many commits back you want to go. For example, `HEAD~2` covers the last 2 commits.

This opens vim showing the commits. Change `pick` to `r` (reword) on any commit you want to rename, then save and quit.

### Vim quick reference

- You are in NORMAL mode by default
- Press `i` to enter INSERT mode (for editing text)
- Press `Escape` to go back to NORMAL mode
- Type `:wq` in NORMAL mode to save and quit
- If `:wq` is typing into the file instead of the command bar, you are still in INSERT mode -- press `Escape` first

Git will pause on each `r` commit and open another editor for you to type the new message. Save and quit each one the same way.

When the rebase is done, force push:

```
git push --force-with-lease
```

### Classic mistake

Typing `:wq` while still in INSERT mode saves the literal text `:wq` into the commit message. Fix it with:

```
git commit --amend -m "your actual message"
git push --force-with-lease
```

---

## Commit message convention (this repo)

Format: `type: short description`

- Lowercase everything, including names and exercise titles
- Imperative mood -- "add" not "added"
- No emojis (have to copy-paste them, not worth it)
- Keep it under 72 characters

Types used in this repo: `exercise`, `docs`, `fix`, `notes`, `chore`, `refactor`

Examples:
- `exercise: add tip calculator`
- `exercise: add treasure island`
- `docs: add README`
