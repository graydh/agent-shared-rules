# agent-shared-rules

Shared AI agent skills and rules for use across repositories via [Ruler](https://github.com/intellectronica/ruler).

## Branches

| Branch | Purpose |
|--------|---------|
| `main` | Stable library branch - use this as a submodule in other projects |
| `dev` | Self-hosting branch - uses `main` as its own skills source |

## Structure (dev branch)

```
agent-shared-rules/
├── .devcontainer/            # Dev container with uv + Node.js + ruler
│   └── devcontainer.json
├── .ruler/                   # Self-hosting: uses itself via submodule
│   ├── AGENTS.md             # Project-specific intro
│   ├── ruler.toml            # Ruler configuration
│   ├── *.md                  # Symlinks to skills/_rules/*.md
│   └── skills/               # Git submodule → this repo
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

## Usage in Other Projects

Add as a git submodule at `.ruler/skills/`:

```bash
cd your-project
git submodule add https://github.com/graydh/agent-shared-rules.git .ruler/skills
```

Ruler discovers skills at `.ruler/skills/*/SKILL.md` — this just works.

For the always-on rules, symlink `_rules/` contents into `.ruler/`:

```bash
# From project root (inside .ruler/)
cd .ruler
ln -s skills/_rules/00-response-style.md 00-response-style.md
ln -s skills/_rules/10-plan-before-act.md 10-plan-before-act.md
ln -s skills/_rules/20-tool-preferences.md 20-tool-preferences.md
ln -s skills/_rules/30-code-style.md 30-code-style.md
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

## Dev Container

This repository includes a dev container configuration using:
- **Base image**: `ghcr.io/astral-sh/uv:python3.12-bookworm` (Python/uv)
- **Node.js 22**: Added via dev container features (required for ruler)
- **Ruler**: Installed globally via npm

Open in VS Code with the Dev Containers extension, or use GitHub Codespaces.

### Dev Container for Your Projects

```json
{
  "name": "your-project",
  "image": "ghcr.io/astral-sh/uv:python3.12-bookworm",
  "features": {
    "ghcr.io/devcontainers/features/node:1": { "version": "22" },
    "ghcr.io/devcontainers/features/git:1": {}
  },
  "postCreateCommand": "npm install -g @intellectronica/ruler && git submodule update --init --recursive"
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
