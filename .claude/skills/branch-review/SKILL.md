---
name: branch-review
description: Review a branch's implementation against its branch plan
allowed-tools: Bash(git *), Bash(gh pr *)
---

# Branch Review Skill

Review the current branch assuming code was AI-authored from a branch plan. Focus on what a second AI pass uniquely catches: plan fidelity, fresh-context bugs, cross-cutting impact, unnecessary complexity, and security.

## Usage

```text
/branch-review [<base-branch>]
```

- `/branch-review` — review current branch (base auto-detected)
- `/branch-review develop` — review against `develop`

## Instructions for Claude

### Step 1: Determine the base branch

If the user provides a base branch, use it. Otherwise, auto-detect:

1. Check if a `develop` branch exists (`git rev-parse --verify develop`)
2. If `develop` exists and the current branch is not a release branch, use `develop`
3. Otherwise, use `main` — or `master` if `main` does not exist

### Step 2: Gather context

Run in parallel:

- `git log <base>..HEAD --oneline` — all commits on this branch
- `git diff <base>...HEAD --stat` — files changed
- `git diff <base>...HEAD` — the full diff
- Read the branch plan document (`CLAUDE.<branch-name>.md` referenced in `CLAUDE.local.md`)

If no branch plan exists, skip to step 4 and review the diff on its own merits.

### Step 3: Plan fidelity check

Compare the branch plan against what was implemented:

- **Completed tasks**: for each task marked done in the plan, verify the diff contains corresponding changes
- **Skipped tasks**: flag any plan tasks not reflected in the diff
- **Scope drift**: flag changes in the diff that don't correspond to any plan task
- **Out-of-scope changes**: check the plan's "out of scope" section (if any) — flag violations

### Step 4: Code review

Review the full diff with fresh context. Do not assume the author-AI made correct decisions. Check for:

- **Bugs with fresh eyes** — hallucinated APIs/methods, wrong assumptions about existing code, subtle logic errors, incorrect error handling
- **Cross-cutting impact** — broken imports, changed interfaces or signatures that affect callers, unintended side effects on existing behavior
- **Unnecessary complexity** — abstractions not justified by the task, premature generalization, over-engineering, dead code introduced
- **Security** — injection vectors, auth boundary issues, data leakage, unsafe defaults
- **Test gaps** — new or changed code paths without corresponding tests (note: some repos may not have tests — adapt accordingly)

### Step 5: Produce the review

Output a structured review called `CLAUDE.<branch name>-review.md` using these sections. Omit any section that has no findings.

```markdown
## Plan Fidelity

[Only if a branch plan exists]

- **Completed**: [N of M] plan tasks verified in diff
- **Skipped**: [list any plan tasks not implemented]
- **Scope drift**: [changes not in the plan]

## Issues

[Ordered by severity. Use review comment conventions.]

### blocking

- [file:line] — [description of issue and why it blocks]

### suggestion

- [file:line] — [description and suggested alternative]

### nit

- [file:line] — [cosmetic or minor observation]

### question

- [file:line] — [something unclear that the author should clarify]

## Summary

[2-3 sentence overall assessment. Is this ready for human review? Are there blocking issues?]
```

### Principles

- **Assume nothing from the author session** — review as if seeing this code for the first time
- **Flag, don't fix** — the reviewer's job is to identify issues, not rewrite code
- **Be specific** — reference file paths and line numbers; vague feedback is not actionable
- **Calibrate severity honestly** — only use `blocking` for things that would cause bugs, security issues, or significant maintenance problems
- **Acknowledge what's good** — if the implementation is clean, say so briefly in the summary

## Important

- Do NOT modify any files. This skill is read-only.
- Do NOT push, commit, or create PRs. Only produce the review output.
- If the diff is too large to review in one pass, review file-by-file and consolidate findings.
