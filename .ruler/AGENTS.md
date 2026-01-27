# agent-shared-rules

This repository contains shared AI agent rules and skills for use across projects via [Ruler](https://github.com/intellectronica/ruler).

## About This Repository

This is a **self-hosting** setup: this repository uses itself as its own skills source via a git submodule. The rules and skills defined here are applied to this repository for development and serve as examples.

## Structure

- **Rules** (`_rules/*.md`): Always-on guidelines loaded into every prompt
- **Skills** (`*/SKILL.md`): On-demand knowledge invoked by agents when relevant

## Development

When contributing to this repository, the same rules and skills apply. Run `ruler apply` after making changes to regenerate agent configurations.
