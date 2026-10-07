# Fair PR Review Checklist

A practical, low-noise pull request review starter pack for engineers who want **evidence-backed findings instead of style-review churn**.

## What's included

- `PR_REVIEW_PROMPT.md` — a reusable AI-assisted review prompt.
- `SHIP_CHECKLIST.md` — a compact pre-merge / pre-release checklist.

## Review principles

A blocking finding should be tied to concrete evidence: changed behavior, code, tests, logs, data semantics, authorization, deployment risk, or documented requirements.

The workflow deliberately avoids:
- invented requirements;
- stylistic churn when conventions are already consistent;
- blocking on speculative maintainability concerns;
- approving solely because CI is green.

## Quick start

1. Open `PR_REVIEW_PROMPT.md`.
2. Give the reviewer the PR intent, diff/repository context, and relevant test commands.
3. Run the review.
4. Use `SHIP_CHECKLIST.md` before merge/deploy.

## Want the expanded pack?

The **AI PR Audit Kit** adds release and bug-triage prompts plus repository-health tooling.

- Expanded kit: https://incomelab-six.vercel.app/#start
- Fixed-scope PR / repository audits: https://incomelab-six.vercel.app/

## License

MIT. Use it, adapt it, and improve it.
