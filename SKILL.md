---
name: git-style-commits
description: Apply the user's preferred git workflow for inspecting uncommitted changes, grouping work into clean commits, partially staging mixed files, and writing commit messages in their preferred style. Use when Codex needs to review git status, propose or enforce commit boundaries, preserve user-owned wording, or create and rework local commits before push.
---

# Git Style Commits

Follow this workflow whenever preparing, staging, or rewriting local commits for the user.

## Inspect First

- Run `git status --short` before any staging or commit work.
- Read diffs before deciding commit boundaries.
- Prefer targeted diffs over blind full-tree commits.
- Do not stage or commit the whole tree by default.

## Split By Theme

- Group changes by intent, not by file.
- Follow any explicit commit order the user gives.
- Default to separate commits for independent themes such as API fixes, behavior changes, performance work, docs, or version bumps.
- Stage only the hunks that belong to the current commit when a file mixes multiple themes.
- Summarize the proposed commit groups before committing when the boundary is not obvious.

## Preserve User Edits

- Treat user-called-out copy, labels, and naming as user-owned.
- Keep explicitly protected wording unchanged unless the user asks for a change.
- Do not silently normalize or revert user wording.

## Commit Messages

- Write commit messages in English.
- Use concise phrases joined by ` + `.
- End every commit message with `.`.
- Prefer messages like `Fix API Validation + Add API Logs.` or `Optimize Performance + Update Docs.`.
- Do not switch to conventional-commit prefixes unless the user explicitly asks.

## Rework Local History Carefully

- Rewrite a just-created local commit if its scope or message is wrong and it has not been pushed.
- Do not rewrite pushed history unless the user explicitly asks.
- Re-check `git status` after each commit so the remaining work is clear.

## Report Clearly

- Tell the user whether the current tree should be committed in one commit or split.
- Explain the grouping in the order you plan to commit it.
- List the final commit messages in order when the commit work is done.
