# Fair PR Review Checklist

A free, vendor-neutral **AI code review prompt and pull request review checklist** for engineers who want evidence-backed findings instead of style-review churn.

Works with Claude Code, Codex, GitHub Copilot, Cursor, and other assistants that can inspect a pull request or repository context.

## Good fit for

- AI-assisted pull request review before merge;
- reviewing code written by Claude Code, Codex, Copilot, Cursor, or another coding agent;
- test-gap and regression review;
- ship/readiness checks for small teams;
- teams that want fewer low-value review comments and clearer blocking evidence.

## What's included

- `PR_REVIEW_PROMPT.md` - a reusable AI-assisted review prompt.
- `SHIP_CHECKLIST.md` - a compact pre-merge / pre-release checklist.
- `EXAMPLE_REVIEW.md` - a fictional worked review showing evidence, impact, minimal fix, test assessment, and confidence.
- `SKILL.md` - an Agent Skill version for compatible coding-agent skill systems.

## Review principles

A blocking finding should be tied to concrete evidence: changed behavior, code, tests, logs, data semantics, authorization, deployment risk, or documented requirements.

The workflow deliberately avoids:
- invented requirements;
- stylistic churn when conventions are already consistent;
- blocking on speculative maintainability concerns;
- approving solely because CI is green.

## Agent Skill

The repository also includes a root `SKILL.md` so compatible agent-skill systems can use the same evidence-first workflow directly.

The skill is vendor-neutral: it does not require a specific model provider and does not call external services by itself.

## Quick start

1. Open `PR_REVIEW_PROMPT.md`.
2. Give the reviewer the PR intent, diff/repository context, and relevant test commands.
3. Run the review.
4. Use `SHIP_CHECKLIST.md` before merge/deploy.

## What a useful finding looks like

Instead of:

> Retry handling looks risky.

Prefer:

> **High - retry/idempotency.** The first attempt and retry create separate provider requests without reusing a stable idempotency key. A client-side timeout does not prove the first request failed, so the retry can duplicate the side effect. Smallest safe fix: create one operation key before the first attempt, reuse it for every retry, and add a test for "provider accepts, client times out, retry occurs."

A good blocker states **severity, evidence, impact, and the smallest safe fix**.

See a full fictional report:
https://incomelab-six.vercel.app/sample-pr-audit.html?utm_source=github&utm_medium=organic&utm_campaign=fair_pr_review_checklist&utm_content=readme_sample

## Want the expanded pack?

The **AI PR Audit Kit** adds release and bug-triage prompts plus repository-health tooling.

- AI PR Audit Kit ($19): https://buy.stripe.com/00w3cw3KW90y1fib26aVa00?client_reference_id=github_free_repo_kit&utm_source=github&utm_medium=organic&utm_campaign=fair_pr_review_checklist&utm_content=readme_kit
- Fixed-scope audits and workflow setup: https://incomelab-six.vercel.app/?utm_source=github&utm_medium=organic&utm_campaign=fair_pr_review_checklist&utm_content=readme_services
- Evidence-first review guide: https://incomelab-six.vercel.app/ai-code-review-prompt.html?utm_source=github&utm_medium=organic&utm_campaign=fair_pr_review_checklist&utm_content=readme_guide

## License

MIT. Use it, adapt it, and improve it.
