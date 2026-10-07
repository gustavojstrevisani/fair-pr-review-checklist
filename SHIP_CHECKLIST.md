# Ship Checklist

## Scope
- [ ] Requirement and acceptance criteria are explicit.
- [ ] Diff contains no unrelated changes.

## Correctness
- [ ] Happy path works.
- [ ] Relevant edge/error paths are handled.
- [ ] Authorization and data ownership are preserved.
- [ ] Timezone/currency/localization semantics are intentional when applicable.

## Data
- [ ] Schema changes are backward compatible or rollout is sequenced.
- [ ] Migration is safe for existing rows.
- [ ] Destructive changes have rollback/recovery consideration.

## Tests
- [ ] Changed behavior has meaningful automated coverage.
- [ ] Tests assert outcomes, not implementation trivia.
- [ ] Existing relevant suites pass.

## Operations
- [ ] Logs/errors are actionable.
- [ ] Secrets are not committed.
- [ ] External calls have timeout/failure behavior.
- [ ] Rollback path is understood.

## Review
- [ ] Blocking findings are evidence-backed.
- [ ] Non-blocking comments are clearly labeled.
- [ ] Reviewer did not invent requirements.
