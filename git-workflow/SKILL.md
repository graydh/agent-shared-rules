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