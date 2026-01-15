# Commit Message Skill

Use this skill when creating git commits to ensure proper formatting and attribution.

## Conventional Commits Format

All commits must follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types

| Type | Purpose | Version Bump |
|------|---------|--------------|
| `feat` | New feature | MINOR |
| `fix` | Bug fix | PATCH |
| `docs` | Documentation only | - |
| `style` | Formatting, whitespace | - |
| `refactor` | Code restructuring | - |
| `perf` | Performance improvement | - |
| `test` | Adding/modifying tests | - |
| `build` | Build system, dependencies | - |
| `ci` | CI configuration | - |
| `chore` | Maintenance tasks | - |

### Breaking Changes

- Add `!` after type: `feat!: remove deprecated API`
- Or add `BREAKING CHANGE:` in footer
- Triggers MAJOR version bump

### Scope Guidelines

- Use lowercase, keep consistent within project
- Common: `api`, `ui`, `ci`, `docs`, `deps`, `auth`, `db`

## AI Co-Author Attribution

When AI substantially contributes, add trailer after blank line:

```
feat(auth): add OAuth2 support

Implements OAuth2 flow with refresh token handling.

Co-authored-by: Claude <noreply@anthropic.com>
```

### Known AI Emails

| Assistant | Trailer |
|-----------|---------|
| Claude | `Co-authored-by: Claude <noreply@anthropic.com>` |
| Gemini | `Co-authored-by: Gemini <gemini@google.com>` |
| GitHub Copilot | `Co-authored-by: GitHub Copilot <copilot@github.com>` |
| Cursor | `Co-authored-by: Cursor <hi@cursor.com>` |

### Multiple Assistants

Include all that contributed:

```
fix: resolve auth bug

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Gemini <gemini@google.com>
```

### When to Include

✅ AI generated substantial code or provided architectural guidance
❌ Minor autocomplete, typo fixes, or informational answers only

## Examples

```bash
# Feature with scope
feat(api): add rate limiting middleware

# Bug fix
fix: resolve race condition in queue processor

# Breaking change
feat!: require Node 18+

BREAKING CHANGE: Drop support for Node 16

# With AI attribution
docs: update API reference

Co-authored-by: Claude <noreply@anthropic.com>
```
