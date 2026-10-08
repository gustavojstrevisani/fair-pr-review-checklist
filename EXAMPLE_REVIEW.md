# Example PR Review

> Fictional example. No real client code, repository, or production data is used.

## Verdict

**REQUEST CHANGES**

One blocking correctness risk remains in the retry path.

## Blocking finding

### HIGH - Retry / idempotency

**Evidence**

The first send attempt and the retry construct separate provider requests without reusing a stable idempotency key.

A client-side timeout does not prove the provider rejected the first request. The provider may have accepted the first request even though the client did not receive the response.

**Impact**

The retry can duplicate the side effect, such as sending the same notification twice or charging the same logical operation twice.

**Smallest safe fix**

Generate one stable operation key before the first attempt and reuse it for every retry of the same logical operation.

Add a behavior-level test for this sequence:

1. provider accepts the first request;
2. client times out before receiving the response;
3. retry occurs;
4. the provider receives the same idempotency key;
5. only one logical side effect is produced.

## Non-blocking improvement

### MEDIUM - Retry observability

Emit structured fields for attempt number, terminal retry outcome, and provider response class.

This improves production diagnosis but does not need to block the PR after the duplicate-side-effect risk is fixed.

## Test assessment

Covered:
- immediate success;
- explicit provider failure.

Missing:
- ambiguous timeout after provider acceptance;
- retry reusing the same logical operation key.

The missing timeout test is material because it directly exercises the blocking risk.

## Delivery notes

- No schema migration is required in this fictional example.
- Rollout risk is concentrated in duplicate side effects.
- Monitor retry count and idempotency rejection/deduplication rate after deployment.
- Rollback is straightforward if no persistent state format changes are introduced.

## Confidence

**High** for the duplicate-side-effect risk given the stated fictional request behavior.

**Medium** for the operational recommendations because provider-specific contracts and production telemetry are not available.
