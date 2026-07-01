# OOEP-0004: Engineering State

Status: Draft  
Author: David Graves  
Created: 2026-07-01  
Type: Specification  
Requires: OOEP-0001, OOEP-0002, OOEP-0003  
Supersedes: None

## Abstract

This proposal defines the first draft of Engineering State for Outcome-Oriented Engineering.

Engineering State is the current known, evidence-backed representation of engineering reality relevant to one or more outcomes.

It explains what is known, what is unknown, what is believed to be true, what evidence supports that understanding, and how that understanding changes over time.

## Motivation

OOE defines outcomes, lifecycle states, observations, claims, and evidence.

Those concepts require a place to accumulate.

Without Engineering State, engineering knowledge remains scattered across tickets, pull requests, chat messages, logs, dashboards, test results, and individual memory.

A worker may know something during a task.

A conversation may contain useful context.

A test run may produce evidence.

A deployment may change reality.

But unless that knowledge persists as part of Engineering State, future workers cannot reliably reason from it.

Engineering State exists to preserve the current understanding of reality in a form that outlives any single worker, artifact, or conversation.

## Specification

Engineering State is a representation of what is currently known about engineering reality.

It is not the same as source code.

It is not the same as deployed infrastructure.

It is not the same as a ticket backlog.

It is not the same as a worker's memory.

It is a structured understanding of reality derived from outcomes, constraints, observations, claims, evidence, decisions, and known unknowns.

## Core concepts

The initial Engineering State model contains the following concepts:

1. State Subject
2. State Claim
3. State Snapshot
4. State Transition
5. State History
6. Unknown
7. Decision
8. Assumption
9. Risk

### State Subject

A State Subject is the thing the state describes.

Examples:

- An outcome
- A constraint
- A claim
- A system
- A workflow
- A deployment
- A dependency
- A user-facing behavior

Engineering State should make clear what subject it describes.

### State Claim

A State Claim is a claim currently held about a State Subject.

State Claims are supported, weakened, or made uncertain by evidence.

Example:

```text
Existing username/password sign-in continues to work in production.
```

A State Claim may be true, false, uncertain, stale, or disputed depending on available evidence.

### State Snapshot

A State Snapshot is a point-in-time representation of Engineering State.

A snapshot should answer:

- What do we currently know?
- What evidence supports that knowledge?
- What remains unknown?
- What constraints are relevant?
- What decisions have shaped this state?
- What risks remain visible?

Snapshots do not need to contain all possible engineering knowledge.

They should contain the knowledge relevant to reasoning about outcomes.

### State Transition

A State Transition is a change in Engineering State.

Transitions may be caused by:

- New observations
- New evidence
- Changed constraints
- Worker actions
- Deployment events
- Incidents
- Reviews
- Decisions
- Stale or invalidated evidence

A State Transition should preserve what changed and why.

### State History

State History is the sequence of snapshots and transitions that explain how the current Engineering State was reached.

State History helps workers understand not only what is believed now, but why earlier beliefs changed.

### Unknown

An Unknown is a relevant question that has not yet been answered.

Unknowns are first-class parts of Engineering State.

Example:

```text
It is unknown whether users with legacy account configuration can sign in using the external identity provider.
```

An unknown is not a failure.

It is a visible gap in knowledge.

### Decision

A Decision is a recorded choice that affects Engineering State.

Decisions may explain why an outcome, constraint, implementation path, validation threshold, or tradeoff exists.

Example:

```text
Production telemetry must be observed for 24 hours before validating the authentication outcome.
```

### Assumption

An Assumption is a claim being used for reasoning without sufficient evidence.

Assumptions should be visible because they may later require validation, revision, or removal.

Example:

```text
Existing users are expected to retain active sessions during the sign-in change.
```

### Risk

A Risk is a visible possibility that the desired outcome may not become true, may not remain true, or may violate a constraint.

Risks may be reduced, accepted, transferred, or invalidated by later evidence.

## Rationale

Engineering State provides the durable context needed for outcome-oriented work.

The Outcome Lifecycle tells where an outcome stands.

The Evidence Model explains what supports or weakens claims.

Engineering State records the current structured understanding that emerges from those concepts.

This allows OOE to distinguish between:

- What happened
- What was observed
- What evidence suggests
- What is currently believed
- What remains unknown
- What changed since the last known state

## Alternatives considered

### Treating source code as state

Source code is an important part of engineering reality, but it is not sufficient to represent Engineering State.

Code does not explain all decisions, constraints, evidence, risks, unknowns, operational behavior, or user impact.

### Treating tickets as state

Tickets may contain useful state, but they often mix intent, discussion, activity, status, and implementation notes.

OOE requires a clearer representation of what is currently known about reality.

### Treating state as runtime state only

Runtime state is important, but Engineering State is broader.

It includes development, operational, organizational, evidentiary, and decision context relevant to outcomes.

## Open questions

- How much Engineering State should be required for a minimal OOE implementation?
- Should State Snapshots be immutable?
- How should stale State Claims be represented?
- How should conflicting State Claims be handled?
- Should Engineering State distinguish between human-authored and machine-derived claims?
- How should Engineering State relate to future machine-readable schemas?
