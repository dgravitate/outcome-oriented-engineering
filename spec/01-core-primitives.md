# Core Primitives

Status: Draft  
Version: 0.1  
Scope: Foundational vocabulary

This document defines the minimal vocabulary used by the first draft of Outcome-Oriented Engineering.

The goal of this document is not to define every concept OOE may eventually require.

The goal is to define the smallest set of primitives required to discuss outcomes, evidence, workers, and engineering progress with precision.

## Primitive 1: Outcome

An **Outcome** is a desired state of engineering reality.

An outcome describes what should become true, not merely what work should be performed.

Examples:

- Users can sign in using an external identity provider.
- Payment processing remains correct after a provider migration.
- API latency remains below an agreed threshold under expected load.
- A release can be rolled back safely.
- A compliance requirement is satisfied and demonstrable.

An outcome should be specific enough that evidence can be gathered for or against it.

### Non-outcomes

The following are not outcomes by themselves:

- Write code.
- Merge a pull request.
- Close a ticket.
- Add tests.
- Deploy to production.

These may be activities or artifacts that support an outcome, but they do not define the outcome.

## Primitive 2: Engineering Reality

**Engineering Reality** is the current observed state of the engineering system relevant to one or more outcomes.

Engineering reality includes source code, deployed systems, tests, documentation, operational behavior, user behavior, constraints, known risks, decisions, and available evidence.

Engineering reality is not the same as repository state.

A repository may contain code that appears correct while production behavior, documentation, observability, or user impact tells a different story.

OOE treats engineering reality as the object being transformed.

## Primitive 3: Observation

An **Observation** is an event or measurement that reveals something about engineering reality.

Examples:

- A test passes or fails.
- A benchmark produces a result.
- A deployment succeeds or fails.
- Telemetry shows increased error rates.
- A reviewer identifies a security concern.
- A customer completes or fails to complete a workflow.

Observations are how engineering reality becomes known.

An observation may support, weaken, or complicate the evidence for an outcome.

## Primitive 4: Evidence

**Evidence** is interpreted information derived from one or more observations that bears on whether an outcome is true.

Observations are raw events or measurements.

Evidence is what those observations mean in relation to an outcome.

For example:

- Observation: The test suite passed.
- Evidence: Existing expected behavior was preserved under the tested conditions.

- Observation: Production error rates increased after deployment.
- Evidence: The deployed change may have violated the reliability outcome.

- Observation: Documentation was updated to describe the new authentication flow.
- Evidence: The documentation aspect of the outcome may be satisfied.

Evidence can be strong or weak.

Evidence can conflict.

Evidence can become stale.

Evidence is not the same as certainty.

## Primitive 5: Constraint

A **Constraint** is a condition that limits what may count as an acceptable outcome.

Constraints define the boundaries of valid engineering work.

Examples:

- Passwords must never be stored in plaintext.
- P95 latency must remain below 200 ms.
- Existing API consumers must not break.
- Changes must comply with applicable regulation.
- Operating cost must remain within budget.
- Users relying on assistive technology must be able to complete the workflow.

A solution that achieves a desired behavior while violating an essential constraint does not satisfy the outcome.

Constraints may be technical, business, regulatory, operational, architectural, ethical, or human.

## Primitive 6: Worker

A **Worker** is any actor capable of advancing an outcome.

Workers may include:

- Individual engineers
- Engineering teams
- Artificial intelligence systems
- Automation scripts
- CI/CD pipelines
- Reviewers
- Operations personnel
- External systems

Workers perform activity.

Workers may produce artifacts.

Workers may generate observations.

Workers may interpret evidence.

Workers do not own outcomes.

The outcome persists independently of any worker that advances it.

## Primitive 7: Artifact

An **Artifact** is something produced during engineering work.

Examples:

- Source code
- Tests
- Documentation
- Pull requests
- Tickets
- Build outputs
- Architecture diagrams
- Deployment manifests
- Runbooks

Artifacts are important because they may change reality or provide evidence.

Artifacts are not automatically outcomes.

## Primitive 8: Progress

**Progress** is observable movement of engineering reality toward a desired outcome.

Progress is not identical to effort.

A worker may spend time without producing progress.

A small observation may produce significant progress if it clarifies reality.

In OOE, progress should eventually be expressible in terms of outcomes, constraints, observations, and evidence.

## Minimal outcome structure

A minimal OOE outcome should be expressible as:

```yaml
outcome:
  name: External identity provider sign-in
  desired_state: Users can sign in using the approved external identity provider.
  constraints:
    - Existing username/password sign-in must continue to work.
    - Authentication events must be audit logged.
    - No credentials or tokens may be stored in plaintext.
  evidence:
    - Automated tests cover successful sign-in.
    - Automated tests cover failed sign-in.
    - Audit events are visible in the audit log.
    - Documentation describes the new sign-in option.
    - Production telemetry shows no increase in authentication failures after release.
```

This structure is illustrative rather than normative.

A future specification may define a formal representation.

## Concepts intentionally deferred

This draft intentionally does not define several concepts that are likely to become important:

- Engineering State
- Beliefs
- Relationships
- Outcome Lifecycle
- Evidence Strength
- Idempotent Action
- Worker Protocol
- Reference Runtime

These concepts should be introduced only after the foundational vocabulary is stable.

## Open questions

- What is the minimum required structure of an outcome?
- How should evidence strength be represented?
- How should stale or conflicting evidence affect an outcome?
- Should constraints be evaluated independently from outcomes or as part of outcome validation?
- What representation should be used for machine-readable OOE documents?
