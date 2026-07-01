# OOEP-0002: Outcome Lifecycle

Status: Accepted  
Author: David Graves  
Created: 2026-07-01  
Type: Specification  
Requires: OOEP-0001  
Supersedes: None

## Abstract

This proposal defines the first draft of the Outcome Lifecycle for Outcome-Oriented Engineering.

The Outcome Lifecycle describes how an outcome moves from initial intention to validated reality.

The lifecycle is intentionally small. It exists to clarify the difference between activity, completion claims, and evidence-backed validation.

## Motivation

OOE begins with the claim that software engineering is the disciplined transformation of reality until desired outcomes become true.

That claim requires a lifecycle.

Without a lifecycle, an outcome can easily collapse back into a task, ticket, or worker assertion. A worker can say work is done. A pull request can be merged. A deployment can complete. None of those events, by themselves, prove that the outcome is true.

The Outcome Lifecycle provides a shared vocabulary for discussing where an outcome currently stands and what must happen next.

## Specification

The initial lifecycle contains the following states:

1. Proposed
2. Defined
3. In Progress
4. Observed
5. Validated

It also includes three exceptional states:

- Blocked
- Reopened
- Abandoned

### Proposed

An outcome is Proposed when a desired change has been named but not yet made precise enough for evaluation.

A Proposed outcome may describe intent, but it lacks enough structure to determine what evidence would demonstrate completion.

Example:

> Add external identity provider sign-in.

This may be a valid intention, but it is not yet a sufficiently defined outcome.

### Defined

An outcome is Defined when it includes a desired state, relevant constraints, and at least an initial description of what evidence would demonstrate success.

A Defined outcome should answer:

- What should become true?
- What constraints must remain satisfied?
- What evidence would support validation?

### In Progress

An outcome is In Progress when one or more workers are actively attempting to transform engineering reality toward the desired state.

In Progress does not imply partial completion.

It only means work is underway.

### Observed

An outcome is Observed when relevant observations have been collected and interpreted as evidence.

Observed does not mean validated.

It means evidence exists and can be evaluated.

### Validated

An outcome is Validated when sufficient evidence demonstrates that the desired state has become true under the stated constraints.

Validation is evidence-backed.

It is not a worker assertion.

### Blocked

An outcome is Blocked when progress cannot continue without resolving an impediment.

A blocked outcome may need a decision, missing information, unavailable access, failed dependency, unresolved constraint, or additional evidence.

### Reopened

An outcome is Reopened when evidence that previously supported validation is weakened, invalidated, contradicted, or made stale by later observations.

Reopening is not failure.

It is recognition that engineering reality has changed or become better understood.

### Abandoned

An outcome is Abandoned when the desired state is no longer being pursued.

An Abandoned outcome should preserve the reason for abandonment when possible.

## State transitions

The normal lifecycle is:

```text
Proposed
  ↓
Defined
  ↓
In Progress
  ↓
Observed
  ↓
Validated
```

Exceptional transitions may occur from multiple states:

```text
Defined / In Progress / Observed
  ↓
Blocked
```

```text
Validated
  ↓
Reopened
```

```text
Proposed / Defined / In Progress / Blocked
  ↓
Abandoned
```

The lifecycle is not intended to enforce a rigid workflow.

It is intended to make the current status of an outcome explicit.

## Rationale

The lifecycle separates three ideas that are often conflated:

- Work is happening.
- Evidence has been observed.
- The outcome has been validated.

This distinction is central to OOE.

A pull request may move an outcome to In Progress.

A test run may contribute observations.

A release may provide evidence.

Only sufficient evidence under constraints can validate the outcome.

## Alternatives considered

### More states

A more detailed lifecycle could include states such as Planned, Implemented, Tested, Deployed, Verified, Accepted, or Released.

This draft avoids those states because they tend to describe activities or artifacts rather than outcome truth.

### Fewer states

A simpler lifecycle could contain only Proposed, In Progress, and Validated.

This draft includes Defined and Observed because OOE depends on distinguishing intent from evaluable outcomes and observations from validation.

## Open questions

- Should Blocked be a state or a condition attached to another state?
- Should Validated outcomes expire automatically when evidence becomes stale?
- Should Abandoned outcomes preserve evidence and constraints for future reuse?
- Should an outcome be allowed to move directly from Defined to Observed when evidence already exists?
- How should partially validated outcomes be represented?
