# Outcome Lifecycle

Status: Draft  
Version: 0.2  
Scope: Outcome progression and validation status

The Outcome Lifecycle defines how an outcome moves from intention to validated reality.

The lifecycle exists to prevent a common engineering mistake: treating activity as completion.

A worker may finish a task.

A pull request may merge.

A deployment may complete.

An outcome is complete only when sufficient evidence demonstrates that the desired state has become true under the stated constraints.

## Lifecycle states

The initial Outcome Lifecycle contains five primary states:

```text
Proposed → Defined → In Progress → Observed → Validated
```

It also recognizes three exceptional states:

```text
Blocked
Reopened
Abandoned
```

## Proposed

An outcome is **Proposed** when a desired change has been named but is not yet precise enough to evaluate.

A Proposed outcome expresses intention.

It does not yet define the desired state, constraints, or evidence required for validation.

Example:

```text
Add external identity provider sign-in.
```

This may be a reasonable intention, but it does not yet answer what must become true, what constraints must hold, or what evidence would demonstrate success.

## Defined

An outcome is **Defined** when it includes:

- A desired state
- Relevant constraints
- Initial evidence requirements

A Defined outcome should be specific enough that workers can reason about how to advance it and reviewers can reason about how it might be validated.

Example:

```text
Users can sign in using the approved external identity provider while existing sign-in continues to work, authentication events are audit logged, and tokens are not stored in plaintext.
```

## In Progress

An outcome is **In Progress** when one or more workers are actively attempting to transform engineering reality toward the desired state.

In Progress does not mean the outcome is partially true.

It means work is underway.

## Observed

An outcome is **Observed** when relevant observations have been collected and interpreted as evidence.

Observed does not mean Validated.

It means there is evidence to evaluate.

An outcome may be Observed and still fail validation if the evidence is insufficient, stale, conflicting, or shows that a constraint has been violated.

## Validated

An outcome is **Validated** when sufficient evidence demonstrates that the desired state has become true under the stated constraints.

Validation is a claim about engineering reality.

It should be supported by evidence.

It should not depend solely on a worker saying the work is done.

## Blocked

An outcome is **Blocked** when progress cannot continue without resolving an impediment.

Examples of blockers include:

- Missing information
- Unresolved decision
- Failed dependency
- Unavailable access
- Conflicting constraints
- Insufficient evidence
- External approval requirement

Blocked may be treated as a state or as a condition attached to another state. This draft treats it as an exceptional state for simplicity.

## Reopened

An outcome is **Reopened** when later observations weaken, contradict, invalidate, or make stale the evidence that previously supported validation.

Examples:

- A production incident reveals that a validated reliability outcome no longer holds.
- A new requirement invalidates earlier acceptance criteria.
- A security review identifies a constraint violation after release.
- Telemetry shows that the desired behavior does not hold under real usage.

Reopening an outcome is not necessarily failure.

It is recognition that engineering reality has changed or become better understood.

## Abandoned

An outcome is **Abandoned** when the desired state is no longer being pursued.

Abandoned outcomes should preserve the reason for abandonment when possible.

This allows future workers to distinguish between outcomes that failed, outcomes that became unnecessary, and outcomes that were deferred for strategic reasons.

## Transition guidance

The normal path is:

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

Common exceptional transitions include:

```text
Defined → Blocked
In Progress → Blocked
Observed → Blocked
Validated → Reopened
Proposed → Abandoned
Defined → Abandoned
In Progress → Abandoned
Blocked → Abandoned
```

The lifecycle is descriptive before it is prescriptive.

Implementations may enforce stricter transition rules, but the specification should remain small until more implementation experience exists.

## Completion rule

An outcome is not complete because:

- A task was closed
- Code was merged
- A worker finished
- Tests passed
- A deployment completed

Those events may produce evidence.

They do not, by themselves, validate an outcome.

The completion rule is:

> **An outcome is complete only when sufficient evidence demonstrates that the desired state has become true under the stated constraints.**

## Open questions

- What criteria determine evidence sufficiency for different classes of outcomes?
- Should lifecycle transitions be machine-enforceable in future specifications?
- How should partially validated outcomes be represented?
- Should Reopened return an outcome to In Progress, Observed, or a distinct state?
- How should lifecycle history be preserved?
