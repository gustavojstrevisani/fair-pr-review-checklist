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

- AI PR Audit Kit ($19): https://buy.stripe.com/00w3cw3KW90y1fib26aVa00?client_reference_id=github_free_repo_kit&utm_source=github&utm_medium=organic&utm_campaign=fair_pr_review_checklist&utm_content=readme_kit
- Fixed-scope audits and workflow setup: https://incomelab-six.vercel.app/?utm_source=github&utm_medium=organic&utm_campaign=fair_pr_review_checklist&utm_content=readme_services
- Evidence-first review guide: https://incomelab-six.vercel.app/ai-code-review-prompt.html?utm_source=github&utm_medium=organic&utm_campaign=fair_pr_review_checklist&utm_content=readme_guide

## License

MIT. Use it, adapt it, and improve it.
