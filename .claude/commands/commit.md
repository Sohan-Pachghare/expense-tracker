---
description: Stage all changes and commit with a given or generated message
argument-hint: [commit message]
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git diff:*), Bash(git commit:*)
---

Commit the current changes.

User-provided commit message: `$ARGUMENTS`

Steps:

1. Run `git add .` to stage all changes.

2. Decide the commit message:
   - If `$ARGUMENTS` is non-empty, use it verbatim as the commit message.
   - If `$ARGUMENTS` is empty:
     1. Run `git status` to see which files changed.
     2. Read the changes (`git diff --staged`, and read the changed/new files if needed).
     3. Generate a concise, descriptive commit message summarizing what changed and why
        (imperative mood, short subject line under ~72 chars, optional body for detail).

3. Run `git commit -m "<message>"` with the chosen message.

4. Report the resulting commit (hash and message) to the user. If the commit fails, show the error and do not retry blindly.
