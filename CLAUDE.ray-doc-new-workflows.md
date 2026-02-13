# Split Workflow Documentation into Two Strategies

> **IMPORTANT**: This plan must be kept up-to-date at all times. Assume context can be cleared at any time — this file is the single source of truth for the current state of this work. Update this plan before and after task and subtask implementations.

## Branch

`ray/doc-new-workflows`

## Goal

Replace the single Gitflow-based workflow doc with two standalone workflow documents — one for semver-versioned software (Gitflow) and one for end-user services (trunk-based) — so each can be used independently as a skill file in project-specific Claude Code configurations.

## Strategy: Vertical Slice

Deliver complete, reviewable documentation end-to-end:

1. **Investigate** — Audit existing docs for workflow-specific content and implicit assumptions
2. **Write workflow docs** — Create the two standalone workflow files
3. **Update supporting docs** — Branch naming, diagrams, README, CLAUDE.md, todo.md
4. **Verify** — Review all cross-references and markdownlint compliance

> **Note**: This is a documentation-only repo. Test-first strategy does not apply — there is no application code or test framework.

## Current State

- [x] Plan created
- [x] Questions resolved with decisions
- [x] Core implementation complete (workflow docs, supporting docs, old files removed)
- [x] All diagrams complete (semver, trunk-based, rebase generalized)
- [x] Old `images/git-flow.drawio.svg` removed (replaced by new diagrams)
- [x] Additional improvements: code review practices, commit conventions, skills, repo hygiene
- [x] Branch ready for PR

## Key Findings

- The repo currently documents a single Gitflow workflow in `docs/git_workflow_and_management.md`
- Workflow-specific content is concentrated in `docs/git_workflow_and_management.md` and `docs/branching_conventions.md`; other docs (commits, PRs, code review) are workflow-agnostic
- Existing diagrams: `images/git-flow.drawio.svg` and `images/git-rebase.drawio.svg` — both assume Gitflow with `develop`
- `docs/pull_request_conventions.md` may contain implicit references to `develop` as merge target — needs review

## Questions

> Questions must be crossed off when resolved. Note the decision made.

- [x] Should release branches in Workflow A follow `release/<version>` naming? — **Yes**, `release/<version>` with no author prefix
- [x] Should Workflow B allow direct commits to main for trivial changes, or always require PRs? — **Always require PRs**
- [x] How to handle hotfixes in Workflow B? — **Keep `hotfix/*` naming** for urgency signaling, even though the flow is the same as feature branches
- [x] Should the two workflows live in a single file or two separate files? — **Two separate files** (`git_workflow_semver.md` and `git_workflow_trunk.md`) so they can be used as standalone skill files per project
- [x] For trunk-based workflow: staging/pre-production environment? — **Don't document deployment** — project-specific
- [x] For semver workflow: support release candidates? — **No** — simple version tags only (e.g., `v1.2.0`)
- [x] Should we document CI/CD expectations? — **No** — project-specific

## Scope

**In scope:**

- Create `docs/git_workflow_semver.md` — standalone Gitflow workflow for versioned packages
- Create `docs/git_workflow_trunk.md` — standalone trunk-based workflow for end-user services
- Update `docs/branching_conventions.md` — add `release/<version>` pattern, clarify per-workflow differences
- Create `images/git-flow-semver.drawio.svg` — Gitflow diagram with release branches
- Create `images/git-flow-trunk.drawio.svg` — trunk-based diagram (main + feature branches)
- Update or generalize `images/git-rebase.drawio.svg` — label target branch generically
- Update `README.md` — new links, brief intro about two workflows
- Update `CLAUDE.md` — reflect dual-workflow reality
- Update `todo.md` — adjust existing items
- Review `docs/pull_request_conventions.md` — generalize any `develop`-specific language
- Remove old `docs/git_workflow_and_management.md` after content is migrated
- Remove old `images/git-flow.drawio.svg` after replaced by new diagrams

**Out of scope:**

- CI/CD documentation
- Deployment strategy documentation
- Release candidate tagging conventions
- Changes to `docs/commit_conventions.md` (workflow-agnostic)
- Changes to `docs/code_review_practices.md` (workflow-agnostic)

## Tasks

> **Note**: Test-first does not apply — this is a documentation-only repo. Tasks are ordered by dependency.

- [x] 1 Audit `docs/pull_request_conventions.md` for implicit `develop` references — none found, no changes needed
- [x] 2 Create `docs/git_workflow_semver.md` — full Gitflow workflow with release branches, hotfix flow, rebase strategy
- [x] 3 Create `docs/git_workflow_trunk.md` — trunk-based workflow: main + feature/hotfix branches, rebase strategy
- [x] 4 Update `docs/branching_conventions.md` — add `release/<version>`, note per-workflow differences
- [x] 5 Create `images/git-flow-semver.drawio.svg` — Gitflow diagram (main, develop, feature, release, hotfix)
- [x] 6 Create `images/git-flow-trunk.drawio.svg` — trunk-based diagram (main, feature/hotfix)
- [x] 7 Update `images/git-rebase.drawio.svg` — generalize target branch label
- [x] 8 Update `README.md` — new links, two-workflow intro
- [x] 9 Update `CLAUDE.md` — describe both workflows
- [x] 10 Update `todo.md` — adjust items for dual-workflow context; added diagram tasks
- [x] 11 Generalize `docs/pull_request_conventions.md` if task 1 finds issues — no changes needed (already workflow-agnostic)
- [x] 12 Remove old `docs/git_workflow_and_management.md` and `images/git-flow.drawio.svg`
- [x] 13 Final review — cross-references verified, no broken links

## Additional Work (beyond original scope)

These changes were made during the branch but were not in the original plan:

- Updated `docs/code_review_practices.md` — AI-assisted and human review passes, branch-review skill reference
- Updated `docs/commit_conventions.md` — examples follow capability style
- Created `.claude/skills/commit/SKILL.md` — commit message skill
- Created `.claude/skills/pr-create/SKILL.md` — PR creation skill (drafts, updates, auto-detection)
- Created `.claude/skills/branch-review/SKILL.md` — branch review skill
- Created `.gitignore` — excludes local Claude files from version control
- Created `.markdownlint.json` — markdownlint configuration
- Renamed `docs/branch_naming_convention.md` → `docs/branching_conventions.md`

## Completed

All planned tasks complete. Branch ready for PR.

---

Last updated: 2026-02-14
