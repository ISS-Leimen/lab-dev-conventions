# Code Review Practices

Code review has two passes: an AI-assisted pass for mechanical checks, and a human pass for judgment and design. The human reviewer is always the final authority.

## AI-Assisted Pass

What an AI agent can check before or during review:

- Style, formatting, and linting compliance
- Naming clarity and consistency
- Test coverage — are new or changed code paths tested?
- Obvious bugs: off-by-ones, unclosed resources, missing error handling
- Documentation gaps — public APIs without docstrings, missing README updates

## Human Reviewer Pass

What only a person can judge:

- **Does this belong here?** — Is the change in the right place architecturally?
- **Is it the simplest thing that works?** — Flag unnecessary abstraction, premature generalization, over-engineering
- **Will I understand this in 6 months?** — If not, it needs restructuring (not just comments)
- **Edge cases and failure modes** — What happens when things go wrong?
- **Security and data integrity** — Injection, auth boundaries, data leakage

## Review Comment Conventions

- `nit:` — cosmetic, not blocking
- `question:` — seeking understanding, not requesting a change
- `suggestion:` — take it or leave it
- `blocking:` — must be resolved before merge

## Principles

- Review the PR, not the person
- Small PRs get better reviews — if a PR is too large to review in one sitting, ask the author to split it
- Every comment should be actionable or a genuine question
- Approve when "good enough" — don't block on perfection
