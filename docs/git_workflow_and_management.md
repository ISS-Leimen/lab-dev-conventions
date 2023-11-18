# Dev Workflow Management

## Branches

### `main` branch

- Any code in the `main` branch should be deployable.
- Only use Pull Requests to merge into `main` branch.
- Only ever base merges from the `develop` branch into `main` branch.

### `develop` branch

- Maintain a `develop` For *anything larger than a WIP/experimental* project.
- All new work should branch out of `develop` – never out of `main` except for `hotfix-*`

### Feature branches

- Create new descriptively-named branches off the `develop` branch (only!) for new work, such as `taylor/feature-add-new-payment-types` (see full naming convention in Branch Conventions).
- Always add new tests to confirm the major behavior of your features (Use HAPPY/BAD/SAD tests).
- Make sure to test and refactor your feature branches before merging into `develop`

## Git/Github Flow Practices

- When starting a new feature/fix/docs/etc. branch, make a small initial commit and push it to Github;
open a Pull Request immediately so others can track your progress (see what to write in the PR description in Pull Request Conventions).
- Commit new work to your local branches and regularly push work to the remote; the Pull Request should reflect these changes immediately.
- To request feedback or help, or when you think your work is ready to merge into the `develop` branch, assign a 'reviewer' to do a **Code Review** (see Code Review Practices).
- After your work or feature has been *reviewed and approved*, it can be merged into the `develop` branch.

## Reference

[GitHub](https://docs.github.com/en/get-started/quickstart/github-flow)
[Gitkraken](https://www.gitkraken.com/learn/git/best-practices/git-branch-strategy)
