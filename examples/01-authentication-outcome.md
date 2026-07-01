# Example: External Identity Provider Sign-In

Status: Draft  
Version: 0.2  
Related specs:

- `spec/02-outcome-lifecycle.md`
- `spec/03-evidence-model.md`

This example demonstrates how an ordinary engineering request can be expressed as an Outcome-Oriented Engineering outcome.

## Initial request

A typical engineering request might begin as:

```text
Add external identity provider sign-in.
```

This is a useful intention, but it is not yet a complete OOE outcome.

It does not define the desired state precisely.

It does not identify constraints.

It does not define what evidence would demonstrate success.

At this point, the outcome is **Proposed**.

## Defined outcome

A more complete outcome might be:

```text
Users can sign in using the approved external identity provider while existing username/password sign-in continues to work, authentication events are audit logged, and credentials or tokens are never stored in plaintext.
```

At this point, the outcome may become **Defined**.

## Desired state

```yaml
outcome:
  name: External identity provider sign-in
  desired_state: >
    Users can sign in using the approved external identity provider while
    existing username/password sign-in continues to work.
```

## Constraints

```yaml
constraints:
  - Existing username/password sign-in must continue to work.
  - Authentication success and failure events must be audit logged.
  - Credentials and tokens must not be stored in plaintext.
  - Existing active sessions must not be invalidated unexpectedly.
  - Authentication failure rates must not materially increase after release.
```

These constraints define what counts as an acceptable outcome.

A solution that enables external sign-in while violating one of these constraints does not satisfy the outcome.

## Claims

The outcome can be decomposed into claims that evidence may support or weaken.

```yaml
claims:
  - Users can sign in using the external identity provider.
  - Existing username/password sign-in continues to work.
  - Authentication success events are audit logged.
  - Authentication failure events are audit logged.
  - Credentials and tokens are not stored in plaintext.
  - Existing active sessions are preserved as expected.
  - Authentication reliability is not degraded in production.
```

Claims make evidence evaluable.

## Observations

Observations are events or measurements.

```yaml
observations:
  - External sign-in integration tests passed.
  - Username/password sign-in regression tests passed.
  - Audit log tests verified success events.
  - Audit log tests verified failure events.
  - Static analysis found no plaintext token storage.
  - Deployment completed successfully.
  - Production telemetry showed no material increase in authentication failures for 24 hours after release.
```

Observations are not automatically sufficient.

They must be interpreted as evidence for or against claims.

## Evidence

```yaml
evidence:
  - claim: Users can sign in using the external identity provider.
    observation: External sign-in integration tests passed.
    direction: supporting
    sufficiency: partial
    freshness: current

  - claim: Existing username/password sign-in continues to work.
    observation: Username/password sign-in regression tests passed.
    direction: supporting
    sufficiency: partial
    freshness: current

  - claim: Authentication success events are audit logged.
    observation: Audit log tests verified success events.
    direction: supporting
    sufficiency: partial
    freshness: current

  - claim: Authentication failure events are audit logged.
    observation: Audit log tests verified failure events.
    direction: supporting
    sufficiency: partial
    freshness: current

  - claim: Credentials and tokens are not stored in plaintext.
    observation: Static analysis found no plaintext token storage.
    direction: supporting
    sufficiency: partial
    freshness: current

  - claim: Authentication reliability is not degraded in production.
    observation: Production telemetry showed no material increase in authentication failures for 24 hours after release.
    direction: supporting
    sufficiency: strong
    freshness: current
```

## Lifecycle progression

The outcome might move through the lifecycle as follows:

```text
Proposed
  Initial request is created.

Defined
  Desired state, constraints, and expected evidence are documented.

In Progress
  Workers implement, test, review, and deploy changes.

Observed
  Test results, static analysis, deployment status, and telemetry are collected.

Validated
  Evidence is judged sufficient to demonstrate that the desired state is true under the stated constraints.
```

## Example validation statement

A validation statement might read:

```text
The External identity provider sign-in outcome is validated based on passing integration and regression tests, audit log verification, static analysis, successful deployment, and 24 hours of production telemetry showing no material degradation in authentication reliability.
```

This statement is stronger than:

```text
The PR was merged.
```

It explains why the outcome is believed to be true.

## Reopening scenario

Suppose that three days later, support tickets show that users with an older account configuration cannot sign in using the external identity provider.

That observation may weaken the claim:

```text
Users can sign in using the external identity provider.
```

The outcome may move from **Validated** to **Reopened**.

Reopening does not erase the earlier evidence.

It adds new evidence that changes what is known about engineering reality.

## Lesson

This example illustrates several OOE principles:

- The initial request is not the outcome.
- The desired state must be explicit.
- Constraints define acceptability.
- Observations become evidence only when interpreted against claims.
- Validation requires sufficient evidence.
- Outcomes may be reopened when reality changes or new evidence appears.

The goal is not to add ceremony.

The goal is to make engineering truth visible.
