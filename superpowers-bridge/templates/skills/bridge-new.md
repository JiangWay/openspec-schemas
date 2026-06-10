---
name: bridge-new
description: Scaffold a new superpowers-bridge change in an isolated git worktree — prevents untracked artifact pollution on the main working tree
---

# bridge-new

Scaffold a new OpenSpec change using the superpowers-bridge schema inside an
isolated git worktree.

## Why this skill exists

`/opsx:new <name> --schema superpowers-bridge` creates the change directory on
the main working tree. All subsequent artifacts (brainstorm.md, proposal.md,
design.md, specs/, tasks.md, plan.md) are written as **untracked files** on
main — git worktree creation during apply does NOT carry them over. This skill
reverses the order: create the worktree **first**, then run `openspec new
change` inside it. The change directory and all artifacts land directly in the
isolated branch, with zero main-tree pollution.

## When to use

Use this skill INSTEAD of `/opsx:new` when starting a superpowers-bridge
change. It is the canonical entry point for the schema.

## Usage

```
/bridge-new my-feature
```

Optionally pass `--schema superpowers-bridge` (the default).

## Procedure

### 1. Pre-flight

Confirm `superpowers:using-git-worktrees` is in the available skills list. If
missing, STOP — the user must install the Superpowers plugin.

### 2. Create the worktree

Invoke **superpowers:using-git-worktrees** to create an isolated git worktree
for `<change-name>`. The worktree branch should be named after the change
(e.g., `feat/<change-name>` or `<change-name>`).

### 3. Scaffold the change inside the worktree

Switch into the worktree, then run:

```bash
openspec new change <change-name> --schema superpowers-bridge
```

This creates `openspec/changes/<change-name>/.openspec.yaml` directly inside
the worktree (not on main).

### 4. Confirm and hand off

Run `git status` in the worktree to confirm the scaffolded directory exists.
Then tell the user:

> Worktree ready at `<path>`. Change scaffolded on branch `<branch>`.
> Run `/opsx:continue` to start brainstorming — all artifacts will land in
> the isolated worktree.

No files are written to the main working tree.
