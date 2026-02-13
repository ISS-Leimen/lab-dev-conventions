---
description: Create a properly formatted commit following project conventions
disable-model-invocation: true
allowed-tools: Bash(git *)
---

# Commit with conventions

Help the user create a properly formatted commit following this project's commit conventions.

## Steps

1. Run `git status` and `git diff --staged` to see what's being committed. If nothing is staged, run `git diff` to see unstaged changes.
2. Stage the relevant files (prefer specific files over `git add -A`), unless the user explicitly asks to commit all changes.
3. Analyze the changes and determine:
   - The appropriate **category** (one of: `feature`, `fix`, `refactor`, `docs`, `tests`, `chore`)
   - A concise **purpose** stated as a *new capability*, not what was done
4. Propose a commit message following the pattern: `<category>: <purpose>`
   - Feature purpose describes a new capability from pov of system, not the action taken by devs (e.g., `feature: generates survey from spreadsheet`, *not* `added survey generation`)
   - Fix purpose describes what is fixed, not what was broken (e.g., `fix: link for generated survey`, *not* `fixed broken link`)
   - Docs purpose describes what is changed, not what actions were done (e.g., `docs: README includes feature usage details`, *not* `changed README`)
   - Tests purpose describes purpose of changes, not what was done (e.g., `tests: failing test for bug` or `tests: no redundancy in DB happy cases`, *not* `added failing test`)
5. Rules:
   - All lowercase
   - One thing per commit
   - If two highly related things, only mention major one: `<category>: <does something>`
6. Do not list minor or related changes in subject line; use bullet points in message body for each change if needed.
7. Run the commit; do not ask the user to confirm or adjust the message before committing.
8. For multi-line commits, use a HEREDOC to preserve formatting:

   ```shell
   git commit -m "$(cat <<'EOF'
   docs: branching conventions updated

   - added release branch pattern
   - clarified per-workflow differences
   EOF
   )"
   ```

## Category reference

- `feature`: adding a new feature
- `fix`: fixing a bug
- `refactor`: changing code without changing its behavior
- `docs`: fix documentation or metadata (e.g., bump version numbers)
- `tests`: write necessary tests
- `chore`: everything else (formatting, cleaning useless code, etc.)

## Examples

- `feature: new survey chart`
- `fix: link for generated survey`
- `refactor: survey chart uses new data structure`
- `docs: README includes feature usage details`
- `tests: failing test for bug`
- `chore: upgrade to python 3.8`

## Important

- Do NOT add a `Co-Authored-By` line or reference AI in the commit message.
- Do NOT push after committing unless the user explicitly asks.
