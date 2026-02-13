# Code Review Practices

Code review has two passes: an AI review for mechanical and structural checks, and a human review for judgment, intent, and design. The human reviewer is always the final authority.

## Workflow

1. **Run `/branch-review`** — produces `CLAUDE.<branch-name>-review.md` with structured findings categorized by severity
2. **Human reviewer reads the AI review, then reviews the code** — uses the AI findings as a starting point, not a substitute

## AI Review

The `/branch-review` skill (`.claude/skills/branch-review/SKILL.md`) performs a fresh-context review of the branch diff. It auto-detects whether a branch plan exists and adjusts accordingly:

- **Plan fidelity** — completed tasks, skipped tasks, scope drift
- **Fresh-context bugs** — hallucinated APIs, wrong assumptions, logic errors
- **Cross-cutting impact** — broken imports, changed interfaces, side effects
- **Unnecessary complexity** — unjustified abstractions, over-engineering
- **Security** — injection, auth boundaries, data leakage
- **Test gaps** — new or changed code paths without tests

Findings use the same comment conventions as human reviews (nit, question, suggestion, blocking).

## Human Review

Read the AI review first, then review the code. Focus on what only a person can judge:

- **Does this match intent?** — The implementation may be technically correct but miss the point.
- **Does this belong here?** — Is the change in the right place architecturally?
- **Is it the simplest thing that works?** — Flag unnecessary abstraction, premature generalization, over-engineering.
- **Will I understand this in 6 months?** — If not, it needs restructuring (not just comments).
- **Are the trade-offs acceptable?** — Not just "is it correct" but "is this what we want?"
- **Did the AI review get it right?** — Were its findings accurate? Did it miss anything? Were severity levels appropriate?

## Review Comment Conventions

- `nit:` — cosmetic, not blocking
- `question:` — seeking understanding, not requesting a change
- `suggestion:` — take it or leave it
- `blocking:` — must be resolved before merge

## Principles

- Review the code, not the author
- Small PRs get better reviews — if a PR is too large to review in one sitting, ask the author to split it
- Every comment should be actionable or a genuine question
- Approve when good enough — don't block on perfection
- The human is responsible for all committed code, including AI-authored code
