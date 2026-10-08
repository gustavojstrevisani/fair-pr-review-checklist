# CLAUDE.md / AGENTS.md Quality Checklist

A free checklist for instruction files that keep coding agents on-scope, testable, and predictable.

## Checklist

- [ ] Project map is short and concrete
- [ ] Build/test commands are exact
- [ ] Protected paths and forbidden changes are explicit
- [ ] Done criteria are observable
- [ ] Unknowns trigger questions instead of guesses
- [ ] Repo-specific gotchas are documented
- [ ] Instructions avoid vague style advice
- [ ] Review/ship gate is stated

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

https://incomelab-six.vercel.app/products.html?utm_source=free_download&utm_medium=organic&utm_campaign=agent_workflows&utm_content=claude-agents-instruction-file-checklist
