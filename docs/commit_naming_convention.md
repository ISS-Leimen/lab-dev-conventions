# Commit Naming Convention

## Pattern

`git commit -m category: now does something; does some other things`

## Principle

 1. Do only one thing in one commit
 2. Use colon ":" to separate category from purpose
 3. Purpose should be stated as a *new capability* rather than what you did
 4. Use lowercase letters only

## Category

- feat: adding a new feature
- fix: fixing a bug
- refactor: changing code without changing its behavior (tests remain same)
- docs: fix documentation or metadata (e.g., bump version numbers)
- tests: write necessary tests (e.g., to catch an issue)
- chore: everything else (formatting, cleaning useless code etc.)

## Examples

- `feat: new survey chart`
- `fix: can now generate survey from spreadsheet`
- `refactor: survey chart uses new data structure`
- `chore: upgrade to python 3.8`
