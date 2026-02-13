# Code Review Practices

Code review has two passes: an AI-assisted pass for mechanical and structural checks, and a human pass for judgment, intent, and design. The human reviewer is always the final authority.

When code is AI-authored from a branch plan, the AI pass shifts from surface-level checks toward verifying plan-to-code fidelity and catching what the author-AI missed.

## AI-Assisted Pass

### When code is AI-authored from a branch plan

The author-AI already handled style, naming, and basic correctness. The reviewer-AI adds value by checking with fresh context:

- **Plan fidelity** — does the implementation match the branch plan? Did it drift, skip tasks, or add out-of-scope work?
- **Fresh-context bugs** — a second pass without author context catches hallucinated APIs, wrong assumptions about existing code, subtle logic errors
- **Cross-cutting impact** — how do changes interact with the rest of the codebase? Broken imports, changed interfaces, unintended side effects
- **Unnecessary complexity** — AI tends to over-engineer; flag abstractions or patterns not justified by the current task
- **Security** — adversarial thinking the "helpful author" mode doesn't naturally apply: injection, auth boundaries, data leakage

### When code is human-authored

Standard mechanical checks:

- Style, formatting, and linting compliance
- Naming clarity and consistency
- Test coverage — are new or changed code paths tested?
- Obvious bugs: off-by-ones, unclosed resources, missing error handling
- Documentation gaps — public APIs without docstrings, missing README updates

## Human Reviewer Pass

What only a person can judge — regardless of who authored the code:

- **Was the plan itself correct?** — Garbage plan in, perfect garbage out. Verify the plan matches actual requirements.
- **Does this match intent?** — The AI's interpretation of requirements may be technically correct but miss the point.
- **Does this belong here?** — Is the change in the right place architecturally?
- **Is it the simplest thing that works?** — Flag unnecessary abstraction, premature generalization, over-engineering.
- **Will I understand this in 6 months?** — If not, it needs restructuring (not just comments).
- **Are the trade-offs acceptable?** — Not just "is it correct" but "is this what we want?"

## Review Comment Conventions

- `nit:` — cosmetic, not blocking
- `question:` — seeking understanding, not requesting a change
- `suggestion:` — take it or leave it
- `blocking:` — must be resolved before merge

## Principles

- Review the PR, not the person (or agent)
- Small PRs get better reviews — if a PR is too large to review in one sitting, ask the author to split it
- Every comment should be actionable or a genuine question
- Approve when "good enough" — don't block on perfection
- The human is ultimately responsible for all committed code, including AI-authored code
