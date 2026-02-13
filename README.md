# ISS-Leimen Code Management Conventions

## About This Repo

This repo documents our lab's code management conventions. Please follow these conventions to code and work with others.

## Git Workflows

This lab uses two git workflow strategies depending on the project type:

- **[Semver Versioned Software](docs/git_workflow_semver.md)** — for R/Python packages and libraries with semantic versioning. Uses Gitflow with `main`, `develop`, feature, release, and hotfix branches.
- **[End-User Services](docs/git_workflow_trunk.md)** — for web apps, mobile apps, and deployed services. Uses trunk-based development off `main` with feature and hotfix branches.

## Conventions Directory

1. [Git Workflow: Semver Versioned Software](docs/git_workflow_semver.md)
2. [Git Workflow: End-User Services](docs/git_workflow_trunk.md)
3. [Pull Request Conventions](docs/pull_request_conventions.md)
4. [Branching Conventions](docs/branching_conventions.md)
5. [Commit Naming Convention](docs/commit_conventions.md)
6. [Code Review Practices](docs/code_review_practices.md)

## Suggestions and Editing

Feel free to submit suggestions as issues or PRs.

- Images
  - Figures should always be in `.draw.svg` format.
  - Figures require using draw.io or (preferred) the "Draw.io integration" for VSCode.

Please see if your suggestion is in the todo list, or consider adding it to that list if you don't have an implementation yet.

[Todo List](todo.md)
