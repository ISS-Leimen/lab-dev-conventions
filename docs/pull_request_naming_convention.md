# Pull Request Naming Convention

## Principle of Title

 1. Put category_words in front of the title
 2. Use() to separate `category_words(scope)`
 3. Use : to separate `category_words(scope):pull_request_purpose`
 4. all lowercase letters

## Category

- feat: is for new functionality
- fix: for a fix to existing functionality
- chore: for a change that does not create new functionality but is needed (e.g. documentation, patch version bump)
- Other options also include docs:, style:, refactor: , and a few other options. We don’t use these so often as they’re generally captured by the above three.

## Domain Keywords

possible scope : `backend, frontend, fullend, database, app, worker`

## Example of Title

`<category_words(domain):pull_request_purpose>`
Ex :

- `feat(app): add new survey chart`
- `chore(app): upgrade the npm`
- `fix(backend): service layer unable to generate survey`
- `refactor(frontend): change the slim structure`

## Pull Request Description

Description :

- Code change :
  - What is the change
  - list each item separately
- UI change (offer screenshot)
