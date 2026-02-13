---
name: pr-create
description: Push branch and create a GitHub PR with a structured description derived from the branch plan
allowed-tools: Bash(git *), Bash(gh pr *)
---

# PR Create Skill

Push the current branch and create a GitHub pull request with a structured description derived from the branch plan document.

## Usage

```text
/pr-create [<base-branch>]
```

- `/pr-create` — create PR targeting `main`
- `/pr-create develop` — create PR targeting `develop`

## What This Skill Does

1. **Locate the branch plan** for the current branch
2. **Read the plan** to extract goal, changes, and decisions
3. **Push the branch** to the remote (with `-u` flag)
4. **Create a PR** using `gh pr create` with the structured description below

## Instructions for Claude

### Step 1: Gather context

Run these in parallel:

- `git log <base>..HEAD --oneline` (default base: `main`) to see all commits
- `git diff <base>...HEAD --stat` to see files changed
- Read the branch plan document (`CLAUDE.<branch-name>.md` referenced in `CLAUDE.local.md`)

### Step 2: Derive PR content from the branch plan

Extract from the branch plan:

- **Summary**: from the plan's Goal section — 1-3 sentences on what this PR achieves.
- **Plan**: from the plan's Tasks section — a checklist of work items. Completed items are checked off; remaining items are unchecked. This lets reviewers see both what's done and what's planned.
- **Changes**: from commits and the plan's completed tasks — what was actually implemented, organized by concern. Only include this section if the plan checklist alone doesn't convey the changes clearly enough.
- **Design notes**: from the plan's Architecture Decisions or Questions sections — only non-obvious decisions a reviewer needs to understand. Omit if straightforward.

### Step 3: Write the PR title

Follow the pattern: `<category>(<scope>): <purpose>`

- All lowercase
- Under 70 characters
- Categories: `feat`, `fix`, `docs`, `chore` (also `style`, `refactor`)
- Scope in parentheses (e.g., `backend`, `frontend`, `api`) — omit if the project has a single scope
- Purpose describes the outcome, not the mechanism

Examples:

- `feat(app): add new survey chart`
- `fix(backend): make service layer generate survey correctly`
- `docs: split workflow docs into semver and trunk-based`

### Step 4: Push and create PR

```bash
git push -u origin <branch>
gh pr create --title "..." --body "..." --base <base>
```

## PR Structure

```markdown
## Summary

[1-3 sentences from the plan's Goal. What does this PR achieve?]

## Plan

- [x] [completed item]
- [x] [completed item]
- [ ] [remaining item]

## Changes

[Group by concern — use whatever groupings suit the project. Skip if the plan checklist is sufficient.]

**[Concern]** — [one-line summary]:
- [specific change]
- [specific change]

### Design note

[Only if there's a non-obvious decision reviewers need. Otherwise omit this section.]
```

### Principles

- **Orient the reviewer**: the PR description's job is to help someone review the diff. Keep it concise.
- **Plan is a living checklist**: the plan section reflects the branch plan document — check off items as they're completed, add new ones as discovered.
- **Changes, not plans**: the Changes section describes what was done, not what was considered.
- **No duplication**: each section has a distinct purpose. Don't repeat information across Summary, Plan, and Changes.

## Important

- Do NOT add a `Co-Authored-By` line or reference AI in the PR title or description.
- Do NOT push to `main` or `master` directly — always create the PR against the base branch.
- Return the PR URL when done so the user can review it.
