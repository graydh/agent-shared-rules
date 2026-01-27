---
name: git-workflow
description: Use this skill for branching strategies, merge requests, and git operations.
---
# Git Workflow Skill

Use this skill for branching strategies, merge requests, and git operations.

## Branch Naming

```
<type>/<short-description>
```

### Types

- `feature/` - New functionality
- `fix/` - Bug fixes
- `hotfix/` - Urgent production fixes
- `docs/` - Documentation updates
- `refactor/` - Code restructuring
- `test/` - Test additions/modifications
- `chore/` - Maintenance tasks

### Examples

```
feature/oauth-integration
fix/login-redirect-loop
hotfix/security-patch-auth
docs/api-reference-update
```

## Merge/Pull Request Guidelines

### Title

Follow conventional commit format:
```
feat(scope): description
```

### Description Template

```markdown
## Summary
Brief description of changes.

## Changes
- Change 1
- Change 2

## Testing
How to verify the changes work.

## Related Issues
Closes #123
```

### Before Merging

- [ ] All CI checks pass
- [ ] Code reviewed
- [ ] Documentation updated if needed
- [ ] No merge conflicts

## Common Git Operations

### Sync with Upstream

```bash
git fetch upstream
git rebase upstream/main
# or
git merge upstream/main
```

### Interactive Rebase (Clean History)

```bash
# Squash last 3 commits
git rebase -i HEAD~3
```

### Undo Last Commit (Keep Changes)

```bash
git reset --soft HEAD~1
```

### Stash Work in Progress

```bash
git stash push -m "WIP: description"
git stash pop
```

### Cherry-Pick Specific Commit

```bash
git cherry-pick <commit-sha>
```

## Protected Branches

- `main` / `master` - Production-ready code
- `release/*` - Release stabilization branches
- Never force-push to protected branches
- All changes via merge/pull request

## Worktree-Based Development

For repositories with separate development and library branches (e.g., `dev` for tooling, `main` for consumable content), use git worktrees to work on both simultaneously.

### Setup

```bash
# From the dev branch checkout, create a worktree for main
git worktree add ../project-main main
```

This creates a sibling directory with `main` checked out:

```
project/           # dev branch (dev container, tooling)
project-main/      # main branch (library code)
```

### Creating Feature Branches

When making changes to the library (main branch):

```bash
# Work in the main worktree
cd ../project-main

# Create feature branch from main
git switch -c feature/my-feature

# Make changes, commit, push
git push -u origin feature/my-feature
```

### Keeping Worktrees in Sync

```bash
# In the main worktree
cd ../project-main
git fetch origin
git rebase origin/main  # or merge
```

### Cleanup

```bash
# Remove a worktree when done
git worktree remove ../project-main

# List all worktrees
git worktree list
```

### Key Rules

- Feature branches for `main` must be created in the main worktree
- Never merge `dev` into `main` (they have different purposes)
- Only merge `main` into `dev` to get library updates
- PRs for library changes target `main`, not `dev`