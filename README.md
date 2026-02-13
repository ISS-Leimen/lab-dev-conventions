# ISS-Leimen Code Management Conventions

## About This Repo

This repo documents our lab's code management conventions and provides Claude Code skills that enforce them. The conventions describe *what* to do; the skills automate *how* to do it.

## Git Workflows

This lab uses two git workflow strategies depending on the project type:

- **[Semver Versioned Software](docs/git_workflow_semver.md)** — for R/Python packages and libraries with semantic versioning. Uses Gitflow with `main`, `develop`, feature, release, and hotfix branches.
- **[End-User Services](docs/git_workflow_trunk.md)** — for web apps, mobile apps, and deployed services. Uses trunk-based development off `main` with feature and hotfix branches.

Choose the workflow that matches your project and reference it in your project's `CLAUDE.md`.

## Conventions

1. [Branching Conventions](docs/branching_conventions.md) — branch naming patterns per workflow
2. [Commit Conventions](docs/commit_conventions.md) — message format and principles
3. [Pull Request Conventions](docs/pull_request_conventions.md) — PR titles, descriptions, and lifecycle
4. [Code Review Practices](docs/code_review_practices.md) — two-pass review: AI review then human review

## Claude Code Skills

Skills live in `.claude/skills/` and can be referenced from any project's `CLAUDE.md` to enforce these conventions automatically.

| Skill | Command | Applies |
| ----- | ------- | ------- |
| [Commit](.claude/skills/commit/SKILL.md) | `/commit` | [Commit Conventions](docs/commit_conventions.md) |
| [PR Create](.claude/skills/pr-create/SKILL.md) | `/pr-create` | [PR Conventions](docs/pull_request_conventions.md) |
| [Branch Review](.claude/skills/branch-review/SKILL.md) | `/branch-review` | [Code Review Practices](docs/code_review_practices.md) |

## Suggestions and Editing

Feel free to submit suggestions as issues or PRs.

- Images
  - Figures should always be in `.drawio.svg` format.
  - Figures require using draw.io or (preferred) the "Draw.io Integration" for VSCode.

Please see if your suggestion is in the todo list, or consider adding it to that list if you don't have an implementation yet.

[Todo List](todo.md)
