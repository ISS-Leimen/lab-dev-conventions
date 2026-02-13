# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a documentation-only repository containing ISS-Leimen lab's code management conventions. There is no application code, build system, or test framework. All content is Markdown documentation and SVG diagrams.

## Repository Structure

- `docs/` - Convention documents (git workflow, branch naming, commits, PRs, code review)
- `images/` - SVG diagrams created with draw.io (must use `.drawio.svg` format)
- `todo.md` - Planned documentation work
- `README.md` - Entry point with links to all convention docs

## Editing Conventions

When editing or adding documentation in this repo, follow the conventions it defines:

**Branches**: `<author>/<category>-<branch_purpose>` (all lowercase)

- Categories: hotfix, bugfix, feature, docs, test, wip
- Example: `soumya/docs-update-commit-conventions`

**Commits**: `<category>: <does something>; <related things>` (all lowercase)

- Categories: feature, fix, refactor, docs, tests, chore
- State purpose as a new capability, not what you did
- One thing per commit; use semicolon for two highly related things

**PR Titles**: `<category>(<scope>): <purpose>` (all lowercase)

- Categories: feat, fix, docs, chore (also style, refactor)
- Scope is optional for single-scope projects

**PR Descriptions**: Include a checklist plan with `- [ ]` items, updated as work progresses. Open PRs immediately after first commit, not after work is complete.

## Git Workflow

This repo documents two workflow strategies (see `docs/`):

- **Semver Versioned Software** (`docs/git_workflow_semver.md`): Gitflow with `main`, `develop`, feature, release, and hotfix branches. For R/Python packages and libraries.
- **End-User Services** (`docs/git_workflow_trunk.md`): Trunk-based development off `main` with feature and hotfix branches. For web apps and deployed services.

Common to both workflows:

- Rebase feature branches onto the target branch when it has new commits (don't merge)
- Force push feature branches after rebase: `git push --force origin <branch>`
- Open PRs immediately after first commit

## Figures

All diagrams must be `.drawio.svg` files created with draw.io or the "Draw.io Integration" VSCode extension. Store in the `images/` directory.

## IMPORTANT: First Message and AI-assisted authorship

At the START of every conversation, immediately inform the user: "[Reminder: You must review, understand, and be ultimately responsible for any code you commit — even when using AI assistance]"

Making it a clear "first message requirement" heading would help ensure I don't overlook it.

Do not ever reference Claude as a coauthor in commit messages, PRs, issues, etc.
