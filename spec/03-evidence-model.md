# Evidence Model

Status: Draft  
Version: 0.2  
Scope: Observations, claims, evidence, sufficiency, freshness, and conflict

The Evidence Model defines how Outcome-Oriented Engineering reasons about whether an outcome has become true.

Evidence is not proof of effort.

Evidence is support for a claim about reality.

## Core distinction

OOE distinguishes between four related ideas:

```text
Activity → Observation → Evidence → Validation
```

### Activity

Activity is work performed by a worker.

Examples:

- Writing code
- Updating documentation
- Running tests
- Deploying a change
- Reviewing a pull request

Activity may produce observations.

Activity is not evidence by itself.

### Observation

An Observation is an event, measurement, or reviewable fact that reveals something about engineering reality.

Examples:

- The integration test suite passed.
- The deployment completed.
- Error rates increased after release.
- A reviewer noted that audit logging is missing.
- A customer failed to complete checkout.

Observations are raw inputs into evidence.

### Evidence

Evidence is interpreted information derived from observations that supports or weakens a claim.

Evidence should be connected to what it supports or weakens.

A passing test is not universally meaningful.

It becomes meaningful when tied to a claim such as:

```text
Existing username/password sign-in still works under tested conditions.
```

### Validation

Validation is the conclusion that sufficient evidence demonstrates an outcome has become true under its stated constraints.

Validation depends on evidence.

It is not the same as worker completion, merged code, passing tests, or deployment success.

## Claims

A Claim is a statement about engineering reality that evidence may support or weaken.

Outcomes often require multiple claims to be supported.

Example outcome:

```text
Users can sign in using the approved external identity provider while existing sign-in continues to work and authentication events are audit logged.
```

Possible claims:

- Users can sign in using the external identity provider.
- Existing username/password sign-in continues to work.
- Authentication events are audit logged.
- Tokens are not stored in plaintext.
- Production authentication reliability is not degraded.

Claims make evidence precise.

Without claims, evidence becomes vague.

## Sufficiency

Evidence is **sufficient** when it is enough to support validation of a claim or outcome.

Evidence may be supportive but insufficient.

Examples:

- Unit tests may support correctness but be insufficient for production readiness.
- A successful deployment may support operational readiness but be insufficient to prove user success.
- Documentation updates may support usability but be insufficient to validate that the workflow works.

Sufficiency depends on the outcome, constraints, risk, and context.

OOE does not require all outcomes to have the same evidence threshold.

It requires the threshold to be explicit enough to reason about.

## Freshness

Evidence is **fresh** when it remains relevant to the current engineering reality.

Evidence may become stale when:

- Code changes
- Dependencies change
- Configuration changes
- Production behavior changes
- Requirements change
- Constraints change
- Time-sensitive assumptions expire

Stale evidence may still be historically useful.

It should not be treated as current validation without reevaluation.

## Conflict

Evidence may conflict.

Examples:

- Tests pass, but production telemetry shows failures.
- A reviewer approves architecture but flags security concerns.
- Synthetic monitoring succeeds, but customer behavior shows drop-off.
- Documentation exists, but support tickets indicate users remain confused.

Conflicting evidence should be preserved rather than hidden.

Conflicting evidence may prevent validation, reopen a validated outcome, or require a narrower claim.

## Evidence direction

Evidence may be:

### Supporting

Evidence supports a claim when it increases the justification for treating the claim as true.

### Weakening

Evidence weakens a claim when it decreases the justification for treating the claim as true.

### Neutral

Evidence is neutral when it is relevant to the outcome but does not materially support or weaken a claim.

### Inconclusive

Evidence is inconclusive when it cannot be interpreted clearly enough to affect validation.

## Minimal evidence structure

A minimal evidence entry should be able to express:

```yaml
evidence:
  claim: Existing username/password sign-in continues to work.
  observation: Integration tests for username/password sign-in passed.
  direction: supporting
  freshness: current
  sufficiency: partial
  notes: Supports preservation of existing behavior under tested conditions.
```

This representation is illustrative rather than normative.

A future specification may define a formal schema.

## Evidence and constraints

Evidence must be evaluated against constraints.

A behavior may work while violating a constraint.

Example:

```text
Users can sign in successfully, but tokens are stored in plaintext.
```

This provides evidence for the sign-in behavior claim, but evidence against the security constraint.

The outcome should not validate unless both the desired behavior and required constraints are satisfied.

## Evidence and reopening

A validated outcome may be reopened when new observations weaken or invalidate the evidence that supported validation.

Examples:

- A later deployment breaks a previously validated behavior.
- A production incident reveals a hidden failure mode.
- A compliance interpretation changes.
- Evidence becomes stale after significant system changes.

Reopening preserves the principle that reality is observed, not assumed.

## Open questions

- Should future specifications define formal evidence levels?
- How should automated and human evidence be reconciled?
- Can evidence sufficiency be standardized by outcome category?
- How should evidence history be queried over time?
- Should evidence be signed, attributed, or traceable to specific workers?
