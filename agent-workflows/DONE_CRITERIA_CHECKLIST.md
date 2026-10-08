# AI Coding Agent Done Criteria Checklist

A compact done-definition for AI coding tasks so agents stop with evidence instead of confidence theater.

## Checklist

- [ ] Requested behavior implemented
- [ ] Relevant tests executed
- [ ] Skipped checks disclosed
- [ ] No unrelated changes
- [ ] Risky data/auth/deploy changes called out
- [ ] Diff reviewed
- [ ] Rollback/recovery considered
- [ ] Final report cites commands and evidence

## Evidence rule

Every instruction should be testable by a reviewer. Replace vague language like "be careful" or "follow best practices" with a concrete command, path, constraint, or observable output.

## Minimal instruction-file skeleton

```md
# Project map
- App: <path + stack>
- API: <path + stack>
- Tests: <commands>

# Change rules
- Do not touch <protected paths> unless the task explicitly names them.
- Follow nearby code before introducing an abstraction.
- Keep unrelated formatting/refactors out of the diff.

# Verification
- Run: <exact commands>
- Report: changed files, commands, results, skipped checks.

# Stop conditions
- Ask before destructive data changes, secrets, billing/auth changes, or unclear requirements.
```

## Quick prompt

Before changing code, restate the task, list in-scope files/areas, name required checks, and call out any ambiguity that could change behavior. Do not infer missing requirements. When done, report exact files changed, commands run, results, and remaining uncertainty.

## Go deeper

The paid agent-workflow packs add production-ready guardrails, task/handoff templates, and review gates:

https://incomelab-six.vercel.app/products.html?utm_source=free_download&utm_medium=organic&utm_campaign=agent_workflows&utm_content=ai-agent-done-criteria-checklist
