# Engineering State

Status: Draft  
Version: 0.3  
Scope: Current known engineering reality

Engineering State is the current known, evidence-backed representation of engineering reality relevant to one or more outcomes.

It answers a practical question:

> What does the engineering system currently know about reality?

Engineering State is not the same as repository state, ticket state, deployment state, or worker memory.

Those may contribute to Engineering State.

They do not replace it.

## Purpose

Engineering State exists to preserve durable engineering knowledge.

Without Engineering State, knowledge is scattered across:

- Source code
- Tickets
- Pull requests
- Test results
- Dashboards
- Logs
- Documentation
- Chat conversations
- Human memory
- AI conversation context

OOE treats that scattered knowledge as insufficient.

Engineering knowledge must persist beyond any individual worker, artifact, tool, or conversation.

## Definition

Engineering State is a structured representation of what is currently known, unknown, assumed, decided, or at risk in engineering reality.

It may describe:

- Outcomes
- Constraints
- Claims
- Evidence
- Systems
- Workflows
- Deployments
- User-facing behavior
- Operational health
- Decisions
- Assumptions
- Risks
- Unknowns

Engineering State should be grounded in evidence where possible.

Where evidence is missing, Engineering State should make uncertainty visible.

## Core model

The initial Engineering State model includes:

```text
State Subject
State Claim
State Snapshot
State Transition
State History
Unknown
Decision
Assumption
Risk
```

## State Subject

A **State Subject** is the thing described by Engineering State.

Examples:

- An outcome
- A constraint
- A claim
- A workflow
- A system
- A deployment
- A user behavior
- A dependency

A subject gives state a target.

Without a subject, state becomes vague context.

## State Claim

A **State Claim** is a claim currently held about a State Subject.

Example:

```text
Existing username/password sign-in continues to work in production.
```

A State Claim may have one of the following provisional statuses:

```text
Supported
Weakened
Uncertain
Stale
Disputed
Invalidated
```

These statuses are descriptive, not final workflow requirements.

### Supported

A State Claim is **Supported** when current evidence supports treating the claim as true.

### Weakened

A State Claim is **Weakened** when evidence reduces confidence that the claim is true but does not fully invalidate it.

### Uncertain

A State Claim is **Uncertain** when there is not enough evidence to evaluate it.

### Stale

A State Claim is **Stale** when its supporting evidence may no longer apply to current engineering reality.

### Disputed

A State Claim is **Disputed** when available evidence conflicts.

### Invalidated

A State Claim is **Invalidated** when evidence shows the claim should no longer be treated as true.

## State Snapshot

A **State Snapshot** is a point-in-time representation of Engineering State.

A snapshot should be able to answer:

- What subjects are being described?
- What claims are currently held about those subjects?
- What evidence supports or weakens those claims?
- What constraints are relevant?
- What decisions shaped this state?
- What assumptions are currently being used?
- What unknowns remain visible?
- What risks are known?

A snapshot does not need to include everything known about a system.

It should include the information needed to reason about outcomes.

## State Transition

A **State Transition** is a change in Engineering State.

A transition may occur when:

- An observation is collected
- Evidence is interpreted
- A claim becomes supported, weakened, stale, disputed, or invalidated
- A constraint changes
- A decision is made
- A risk is discovered or reduced
- An unknown is answered
- A deployment changes reality
- An incident reveals reality was different than assumed

A transition should preserve what changed and why.

Example:

```text
Claim changed from Supported to Disputed because production telemetry showed failures for legacy account users.
```

## State History

**State History** is the record of snapshots and transitions that explain how the current Engineering State was reached.

State History matters because current reality often cannot be understood from current artifacts alone.

A worker should be able to ask:

```text
Why do we believe this outcome is validated?
```

or:

```text
Why was this outcome reopened?
```

and receive an answer grounded in prior observations, evidence, decisions, and transitions.

## Unknowns

An **Unknown** is a relevant question that has not yet been answered.

Unknowns are first-class state.

Examples:

- It is unknown whether legacy account users can complete sign-in.
- It is unknown whether the new workflow works under peak load.
- It is unknown whether support documentation is sufficient.
- It is unknown whether a dependency can meet the required availability target.

Making unknowns explicit prevents uncertainty from being mistaken for completion.

## Decisions

A **Decision** is a recorded choice that affects Engineering State.

Examples:

- Production telemetry must be observed for 24 hours before validation.
- The rollback plan must preserve existing sessions.
- Existing username/password sign-in must remain enabled for the first release.

Decisions explain why state changed or why evidence thresholds exist.

## Assumptions

An **Assumption** is a claim being used for reasoning without sufficient evidence.

Assumptions are allowed.

Hidden assumptions are dangerous.

OOE prefers visible assumptions that can later be validated, weakened, or removed.

## Risks

A **Risk** is a visible possibility that an outcome may not become true, may not remain true, or may violate a constraint.

Risks may be:

- Open
- Reduced
- Accepted
- Invalidated
- Realized

Risk status is intentionally provisional in this draft.

A future OOEP may define a more formal risk model.

## Minimal state entry

A minimal Engineering State entry might look like:

```yaml
state:
  subject: External identity provider sign-in
  claims:
    - claim: Existing username/password sign-in continues to work in production.
      status: supported
      evidence:
        - Username/password regression tests passed.
        - Production telemetry showed no material increase in authentication failures for 24 hours.
  unknowns:
    - Whether legacy account configurations have complete coverage in the test data.
  assumptions:
    - Test accounts represent the most common production account configurations.
  risks:
    - Legacy account users may experience sign-in failures not covered by current tests.
  decisions:
    - Observe production telemetry for 24 hours before validation.
```

This structure is illustrative rather than normative.

A future version may define a machine-readable schema.

## Relationship to lifecycle

Outcome Lifecycle describes where an outcome stands.

Engineering State describes what is currently known about reality.

An outcome may be **Validated** while Engineering State still contains risks or unknowns.

An outcome may be **Reopened** when Engineering State changes because new evidence weakens a previously supported claim.

## Relationship to evidence

Evidence supports or weakens claims.

Engineering State records the current interpretation of those claims.

Evidence is the support.

Engineering State is the current understanding built from that support.

## Non-goals

This draft does not define:

- A machine-readable state schema
- A graph model
- A database model
- A synchronization protocol
- A worker protocol
- A runtime engine
- A UI representation
- A relationship model
- A belief model

Those may be introduced later if they earn their place.

## Open questions

- Should Engineering State require immutable snapshots?
- Should State Claims have standardized statuses?
- How should conflicting claims be represented?
- How should old state be archived without losing useful history?
- How should Engineering State distinguish evidence-backed claims from assumptions?
- How much state is enough for practical use without adding ceremony?
