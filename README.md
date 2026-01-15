# agent-shared-rules

Shared AI agent skills and rules for use across repositories via [Ruler](https://github.com/intellectronica/ruler).

## Structure

```
agent-shared-rules/           # Add as submodule at .ruler/skills/
├── _rules/                   # Always-on rules (symlink to .ruler/)
│   ├── 00-response-style.md
│   ├── 10-plan-before-act.md
│   ├── 20-tool-preferences.md
│   └── 30-code-style.md
├── commit-message/           # Skill: conventional commits + co-authors
│   └── SKILL.md
├── git-workflow/             # Skill: branching, MRs, operations
│   └── SKILL.md
└── documentation/            # Skill: README, API docs, changelogs
    └── SKILL.md
```

## Usage

Add as a git submodule at `.ruler/skills/`:

```bash
cd your-project
git submodule add https://github.com/dgmullen/agent-shared-rules.git .ruler/skills
```

Ruler discovers skills at `.ruler/skills/*/SKILL.md` — this just works.

For the always-on rules, symlink `_rules/` contents into `.ruler/`:

```bash
# From project root
ln -s skills/_rules/00-response-style.md .ruler/00-response-style.md
ln -s skills/_rules/10-plan-before-act.md .ruler/10-plan-before-act.md
ln -s skills/_rules/20-tool-preferences.md .ruler/20-tool-preferences.md
ln -s skills/_rules/30-code-style.md .ruler/30-code-style.md
```

Or copy them if symlinks are problematic (devcontainers):

```bash
cp .ruler/skills/_rules/*.md .ruler/
```

Then run `ruler apply` to regenerate agent configs.

## Updating

```bash
git submodule update --remote .ruler/skills
git add .ruler/skills
git commit -m "chore: update shared agent skills"
```

## Devcontainer Setup

```json
{
  "postCreateCommand": "git submodule update --init --recursive && cp .ruler/skills/_rules/*.md .ruler/"
}
```

## Rules vs Skills

| Aspect | Rules (`_rules/*.md`) | Skills (`*/SKILL.md`) |
|--------|----------------------|----------------------|
| **Location** | Copied/linked to `.ruler/` | `.ruler/skills/*/` |
| **When used** | Always in prompt | On-demand by agent |
| **Best for** | Conventions, constraints | Workflows, procedures |

## Available Skills

| Skill | Purpose |
|-------|---------|
| `commit-message` | Conventional commits format, AI co-author attribution |
| `git-workflow` | Branch naming, MR guidelines, common git operations |
| `documentation` | README structure, API docs, changelog format |

## Customization

Projects should have their own `.ruler/AGENTS.md` with project-specific context. Shared content supplements but doesn't replace project-specific instructions.
