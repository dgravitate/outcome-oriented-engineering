# Example: Engineering State Snapshot

Status: Draft  
Version: 0.3  
Related specs:

- `spec/02-outcome-lifecycle.md`
- `spec/03-evidence-model.md`
- `spec/04-engineering-state.md`

This example shows how Engineering State captures what is currently known about reality after evidence has been collected.

It builds on the external identity provider sign-in example.

## Outcome

```text
Users can sign in using the approved external identity provider while existing username/password sign-in continues to work, authentication events are audit logged, and credentials or tokens are never stored in plaintext.
```

## Lifecycle status

```yaml
outcome_lifecycle:
  status: validated
  validation_summary: >
    The outcome was validated based on passing integration tests,
    passing regression tests, audit log verification, static analysis,
    successful deployment, and 24 hours of production telemetry.
```

The lifecycle status says where the outcome stands.

It does not, by itself, preserve everything currently known about the outcome.

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

  - claim: Authentication reliability is not degraded in production.
    observation: Production telemetry showed no material increase in authentication failures for 24 hours after release.
    direction: supporting
    sufficiency: strong
    freshness: current
```

Evidence explains why claims are supported or weakened.

Engineering State records the current understanding built from that evidence.

## State snapshot

```yaml
state_snapshot:
  subject: External identity provider sign-in
  captured_at: 2026-07-01
  lifecycle_status: validated

  state_claims:
    - claim: Users can sign in using the external identity provider.
      status: supported
      evidence:
        - External sign-in integration tests passed.
        - Production telemetry showed successful external sign-in events.

    - claim: Existing username/password sign-in continues to work.
      status: supported
      evidence:
        - Username/password sign-in regression tests passed.
        - Production telemetry showed no material increase in authentication failures for 24 hours.

    - claim: Authentication events are audit logged.
      status: supported
      evidence:
        - Audit log tests verified success events.
        - Audit log tests verified failure events.

    - claim: Credentials and tokens are not stored in plaintext.
      status: supported
      evidence:
        - Static analysis found no plaintext token storage.

  unknowns:
    - Whether legacy account configurations were fully represented in test data.

  assumptions:
    - Test accounts represent the most common production account configurations.
    - The first 24 hours of authentication telemetry are representative of normal usage.

  risks:
    - Legacy account users may experience sign-in failures not covered by current tests.

  decisions:
    - Production telemetry must be observed for 24 hours before validation.
    - Existing username/password sign-in must remain enabled for the first release.
```

## Why this is useful

The lifecycle status says:

```text
Validated
```

The evidence says:

```text
Here is what supports validation.
```

Engineering State says:

```text
Here is what we currently know, what remains unknown, what assumptions we are using, what risks remain, and what decisions shaped the current understanding.
```

These are related but distinct.

## State transition

Suppose that three days later, support tickets show that users with legacy account configurations cannot sign in using the external identity provider.

That new observation may create a State Transition:

```yaml
state_transition:
  subject: External identity provider sign-in
  trigger: Support tickets from legacy account users
  changed_claims:
    - claim: Users can sign in using the external identity provider.
      from: supported
      to: disputed
      reason: >
        Production support tickets indicate that a subset of users with
        legacy account configurations cannot complete sign-in.
  new_evidence:
    - Support tickets from legacy account users describe failed sign-in attempts.
  new_unknowns:
    - How many legacy account configurations are affected?
    - Did test data omit legacy account coverage?
  lifecycle_effect: Outcome may need to move from Validated to Reopened.
```

The transition preserves what changed and why.

## Lesson

Engineering State helps future workers understand reality without reconstructing it from scattered artifacts.

It preserves:

- Current claims
- Supporting and weakening evidence
- Unknowns
- Assumptions
- Risks
- Decisions
- Changes over time

The goal is not to make every project bureaucratic.

The goal is to prevent engineering knowledge from disappearing when a ticket closes, a conversation ends, or a worker moves on.
