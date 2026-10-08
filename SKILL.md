---
name: fair-pr-review
description: Review pull requests and code changes for correctness, regressions, security/privacy exposure, data and migration risk, meaningful test gaps, deploy/rollback concerns, and ship readiness while suppressing unsupported or style-only findings.
version: 1.0.0
---

# Fair PR Review

Use this skill when reviewing a pull request, branch diff, commit, or AI-generated code change before merge or release.

The goal is high-signal engineering review: identify risks worth fixing, require evidence for blockers, and avoid manufacturing comments just to appear thorough.

## Review priorities

Review in this order:

1. correctness and behavioral regressions;
2. security/privacy issues with a concrete exposure path;
3. authorization, ownership, and trust-boundary changes;
4. data loss, schema/migration, concurrency, retry, and idempotency risks;
5. missing tests for materially changed behavior;
6. deploy, rollout, monitoring, and rollback risk;
7. maintainability only when it creates credible defect or operational burden.

Do not prioritize style, naming, or speculative refactors above the items above.

## Required context

Before issuing a verdict, gather as much of the following as is available:

- stated intent or acceptance criteria;
- relevant diff or changed files;
- repository conventions or project instructions;
- build, test, lint, and type-check commands;
- migration/deploy context when applicable.

If required context is missing, say what evidence is missing rather than inventing requirements.

## Evidence rules

A blocking finding must include:

- severity;
- exact evidence from code, tests, configuration, documented intent, or observed behavior;
- concrete impact;
- smallest safe fix;
- relevant test or verification step.

Reject a candidate finding when:

- it is style-only;
- it relies on an invented requirement;
- the repository context already mitigates it;
- it cannot explain a credible failure mode;
- it is only a future-maintainability preference with no concrete risk.

Green CI is evidence, not automatic approval.

## Review process

### 1. Establish intent

Summarize what the change is supposed to accomplish and any explicit non-goals.

### 2. Inspect changed behavior

Trace affected inputs, outputs, state changes, permissions, side effects, and error paths.

### 3. Inspect boundaries

Pay extra attention to:

- null/empty/boundary values;
- retries and idempotency;
- timeouts and partial success;
- authorization and resource ownership;
- schema compatibility and rollout order;
- timezones, currency, localization, and units when relevant;
- external API contracts.

### 4. Assess tests

For every materially changed behavior, ask:

- what outcome proves this works?
- what failure path matters?
- are tests asserting behavior or implementation details?
- does the important regression scenario have coverage?

### 5. Assess delivery risk

Check:

- migration compatibility;
- deploy ordering;
- feature flag behavior;
- observability;
- rollback path;
- operational blast radius.

### 6. Produce a verdict

Use exactly one:

- **APPROVE** - no blocking issue found with available evidence;
- **REQUEST CHANGES** - at least one verified blocking issue exists;
- **NEEDS EVIDENCE** - a material risk cannot be resolved without additional context.

## Output format

### Verdict

APPROVE / REQUEST CHANGES / NEEDS EVIDENCE

### Blocking findings

For each blocker:

- **Severity**
- **Area**
- **Evidence**
- **Impact**
- **Smallest safe fix**
- **Verification**

If there are no blockers, say so explicitly.

### Non-blocking improvements

Only include high-value improvements. Do not fill this section with cosmetic comments.

### Test assessment

State:

- changed behavior;
- what is covered;
- meaningful gaps;
- recommended tests, if any.

### Delivery notes

Include deploy, migration, rollback, monitoring, or operational considerations only when relevant.

### Limitations

List missing context or checks you could not execute.

### Confidence

High / Medium / Low, with a short reason.

## Example quality bar

Weak:

> Retry handling looks risky.

Strong:

> **High - retry/idempotency.** The first attempt and retry create separate provider requests without reusing a stable idempotency key. A client-side timeout does not prove the first request failed, so the retry can duplicate the side effect. Smallest safe fix: create one operation key before the first attempt, reuse it for every retry, and add a test for "provider accepts, client times out, retry occurs."

The strong finding is preferable because it provides evidence, impact, a minimal fix, and a verification path.
