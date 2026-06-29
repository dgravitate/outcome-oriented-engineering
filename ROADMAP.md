# Outcome-Oriented Engineering Roadmap

Outcome-Oriented Engineering is being developed in public and in stages.

The purpose of this roadmap is to clarify what belongs in the first draft, what is intentionally deferred, and how the discipline is expected to mature.

This roadmap is not a product roadmap.

It is a discipline roadmap.

## Version 0.1: Foundation

Goal: establish the smallest coherent body of work that explains OOE and makes it possible to discuss the discipline precisely.

### Included

- Foundations of Software Engineering
- Manifesto
- Axioms
- Core Primitives
- OOEP governance
- Public roadmap

### Explicitly deferred

- Formal outcome lifecycle
- Engineering state model
- Evidence strength model
- Belief model
- Relationship model
- Idempotent action model
- Worker protocol
- Machine-readable schemas
- Reference implementation
- Runtime behavior
- Tool integrations

### Success criteria

Version 0.1 succeeds if an experienced engineer can read the repository and understand:

- Why OOE exists
- What problem it is trying to describe
- What foundational assumptions it makes
- What vocabulary it uses
- How the discipline will evolve

Version 0.1 does not need to be complete.

It needs to be coherent.

## Version 0.2: Outcome Lifecycle and Evidence

Goal: define how outcomes move from intention to validation.

Likely topics:

- Outcome lifecycle
- Evidence requirements
- Evidence sufficiency
- Stale evidence
- Conflicting evidence
- Outcome completion
- Outcome reopening
- Outcome invalidation

Potential OOEPs:

- Outcome Lifecycle
- Evidence Model
- Evidence Sufficiency

## Version 0.3: Engineering State

Goal: define how OOE represents the current known state of engineering reality.

Likely topics:

- Engineering state
- State transitions
- State snapshots
- State history
- Unknown or uncertain state
- Derived state
- Relationship between observations, evidence, and state

Potential OOEPs:

- Engineering State Model
- Observation Semantics
- State Transition Semantics

## Version 0.4: Relationships and Impact

Goal: define how OOE represents engineering relationships that are not visible through source code alone.

Likely topics:

- Relationships between outcomes, systems, artifacts, constraints, and workers
- Impact analysis
- Dependency beyond imports
- Operational and organizational coupling
- Relationship strength
- Relationship evidence

Potential OOEPs:

- Relationship Model
- Impact Model
- Dependency Semantics

## Version 0.5: Worker Model

Goal: define how human workers, artificial intelligence systems, automations, and tools participate in OOE.

Likely topics:

- Worker capabilities
- Worker boundaries
- Assignment
- Delegation
- Review
- Escalation
- Replacement
- Worker-generated observations

Potential OOEPs:

- Worker Model
- Worker Protocol
- Review and Escalation Semantics

## Version 0.6: Idempotent Engineering Actions

Goal: define how OOE supports safe retry, recovery, and repeated execution.

Likely topics:

- Idempotent actions
- Side-effect boundaries
- Action identity
- Duplicate prevention
- Recovery semantics
- Guarded non-idempotent actions

Potential OOEPs:

- Idempotent Action Model
- Safe Retry Semantics
- Side-Effect Boundaries

## Version 0.7: Machine-Readable Specification

Goal: define a portable representation for OOE concepts.

Likely topics:

- YAML representation
- JSON schema
- Outcome files
- Evidence files
- Constraint declarations
- Validation rules
- Compatibility rules

Potential OOEPs:

- OOE Document Format
- Outcome Schema
- Evidence Schema
- Constraint Schema

## Version 0.8: Reference Implementation

Goal: provide a minimal implementation that demonstrates the specification without becoming the specification.

Likely topics:

- CLI prototype
- Outcome validation example
- Evidence collection example
- Simple repository integration
- Example workflows

Potential outputs:

- Reference CLI
- Example repository
- Minimal SDK

## Version 1.0: Stable Foundation

Goal: provide a stable first version of Outcome-Oriented Engineering suitable for broader adoption and implementation.

Version 1.0 should include:

- Stable foundations
- Accepted axioms
- Governance process
- Core primitives
- Outcome lifecycle
- Evidence model
- Engineering state model
- Worker model
- Relationship model
- Machine-readable representation
- At least one reference implementation

## Guiding principle

OOE should grow only when a concept has earned its place.

New ideas should be introduced through examples, discussion, implementation experience, and OOEPs before becoming part of the stable specification.

The goal is not to make OOE large.

The goal is to make it useful, coherent, and durable.
