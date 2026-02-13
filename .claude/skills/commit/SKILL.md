---
description: Create a properly formatted commit following project conventions
disable-model-invocation: true
allowed-tools: Bash(git *)
---

# Commit with conventions

Help the user create a properly formatted commit following this project's commit conventions.

## Steps

1. Run `git status` and `git diff --staged` to see what's being committed. If nothing is staged, run `git diff` to see unstaged changes and ask the user what to stage.
2. Analyze the changes and determine:
   - The appropriate **category** (one of: `feature`, `fix`, `refactor`, `docs`, `tests`, `chore`)
   - A concise **purpose** stated as a *new capability*, not what was done
3. Propose a commit message following the pattern: `<category>: <does something>`
4. Rules:
   - All lowercase
   - One thing per commit
   - If two highly related things, separate with semicolon: `<category>: <does something>; <related thing>`
   - Purpose describes the new capability, not the action taken
5. Ask the user to confirm or adjust the message before committing.
6. Stage the relevant files (prefer specific files over `git add -A`) and run the commit.

## Category reference

- `feature`: adding a new feature
- `fix`: fixing a bug
- `refactor`: changing code without changing its behavior
- `docs`: fix documentation or metadata (e.g., bump version numbers)
- `tests`: write necessary tests
- `chore`: everything else (formatting, cleaning useless code, etc.)

## Examples

- `feature: new survey chart`
- `fix: generates survey from spreadsheet`
- `refactor: survey chart uses new data structure`
- `docs: updated README for feature usage details`
- `tests: failing test for bug`
- `chore: upgraded to python 3.8`

## Important

- Do NOT add a `Co-Authored-By` line or reference AI in the commit message.
- Do NOT push after committing unless the user explicitly asks.
