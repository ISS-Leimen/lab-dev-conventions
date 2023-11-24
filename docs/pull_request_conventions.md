# Pull Request (PR) Conventions

## Pattern

`<category>(<scope>): <purpose>`

## Flow

### Starting a PR

Use pull requests to start any major work on an issue, feature, fix, etc. Start a pull request *immediately after your first minor commit* so that others can comment on it and track your progress. *Do not wait* for the full work to be over to open a PR.

### As you are working

Keep updating the PR description *plan* (see Description below) as you make each commit.

### Finishing a PR

Write a high-level set of changes (see Description section below) for reviewers.

Assign a reviewer in your PR to request a code review. Always get feedback before merging the PR.

## Principle of Title

 1. Put category words in front of the title
 2. Use parentheses "()" to separate category from scope
 3. Use colon ":" to separate category and scope from pull request purpose
 4. all lowercase letters

## Category

- `feat`: new functionality
- `fix`: fixes existing functionality
- `docs`: documentation, patch version bump, etc.
- `chore`: minor changes that do not create new functionality but is needed
- Other options also include `style`, `refactor`, and a few other options. We don’t use these so often as they’re generally captured by the above ones.

## Scope Keywords

Example scopes: `backend`, `frontend`, `fullend`, `database`, `app`, `api`, `worker`

*You do not have to mention a scope if the project only has a single scope.*

## Examples

- `feat(app): add new survey chart`
- `chore(app): upgrade the npm`
- `fix(backend): make service layer generate survey correctly`
- `refactor(frontend): change the slim structure`

## Pull Request Description

Use a meaningful description and provide a checklist of things you *plan* to work on in this PR using checkboxes that you can tick off as you complete them.

Example:

```text
Creating a new feature to integrate LLM feedback in review process.

Plan:
- [ ] openai gateway
- [ ] entity for conversation
- [ ] write mapper for llm conversation
```

You can check off items as you complete them, and add new items as you realize you need them.

Below your plan, you can also summarize things you have changed if they are not covered by the plan.

```text
Code changes:
  - List major changes separately
  - Describe the intent of the change

UI Changes:
  - View that changed
  - Offer screenshots wherever necessary
```
