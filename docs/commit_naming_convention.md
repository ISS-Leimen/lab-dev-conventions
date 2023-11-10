# Commit Naming Convention

## Principle

 1. Use Separators “:” to separate `category_words:commit_purpose`
 2. Use lowercase letters only
 3. Do only one thing in one commit

## Category

- feat: is for adding a new feature
- fix: is for fixing a bug
- refactor: is for changing code for performance or convenience purpose (e.g. readability)
- chore: is for everything else (writing documentation, formatting, adding tests, cleaning useless code etc.)

## Example

`git commit -m <category: do something; do some other things>`
Ex :

- `feat: add new survey chart`
- `chore: upgrade to python 3.8`
- `fix: unable to generate survey`
- `refactor: change survey chart to use new data structure`
