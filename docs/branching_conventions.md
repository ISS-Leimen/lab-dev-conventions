# Branching Conventions

Branches serve to separate work in progress (WIP) from finished work. Generally, create a Pull Request (PR) on Gitub for a branch *right away* after the smallest possible initial commit. This allows others to comment on the work and track your progress. Do not wait until the full work is over to open a PR, even for relatively small changes.

Also see our Git Workflow conventions ([Semver Workflow](git_workflow_semver.md) | [Trunk-Based Workflow](git_workflow_trunk.md)) for when and why to branch.

## Branch Naming Pattern

`<author>/<category>-<branch_purpose>`

### Principle

 1. Branch names start with category and then purpose
 2. Use slash (/) to separate `branch_author/branch_purpose`
 3. Use dashes (-) to separate words in branch purpose
 4. Include author Name in front of the branch; omit for long-lived branches
 5. Use lowercase letters only

### Categories

- hotfix: changing code with a temporary solution
- bugfix: for fixing a bug
- feature: for adding, refactoring or removing a feature
- docs: for adding or changing documentation
- test: for writing tests outside of an issue
- wip: (rare) for a work in progress (only use for free experimentation)

### Examples

- taylor/hotfix-unable-to-generate-survey
- soumya/bugfix-creating-survey-crashes
- jerry/feature-add-new-survey-chart
- soumya/docs-installation
- tiffany/test-google-oauth-authenticate
- francis/wip-new-complexity-algorithm
- release/1.2.0 *(semver workflow only)*

## Release Branches (Semver Workflow Only)

Release branches are only used in the [Semver Workflow](git_workflow_semver.md). The [Trunk-Based Workflow](git_workflow_trunk.md) does not use release branches.

Release branches serve to stage final changes in documentation and external checks (e.g., CRAN) before a release; do not use them for development.

Release branches use a different naming pattern since they are shared and not owned by a single author:

`release/<version>` (e.g., `release/1.2.0`)
