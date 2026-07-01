# OOEP-0001: Governance of Outcome-Oriented Engineering

Status: Accepted  
Author: David Graves  
Created: 2026-06-28  
Type: Process  
Requires: None  
Supersedes: None

## Abstract

This document defines the initial governance process for Outcome-Oriented Engineering Proposals, or OOEPs.

OOEPs are the mechanism by which Outcome-Oriented Engineering evolves.

The purpose of the OOEP process is to allow the discipline to change deliberately, transparently, and with a clear record of reasoning.

## Motivation

Outcome-Oriented Engineering is intended to become a coherent engineering discipline rather than a collection of disconnected essays, examples, or implementation ideas.

That requires a lightweight governance model.

The governance model should make it easy to propose ideas, debate them, revise them, accept them, reject them, or supersede them without losing the history of why those decisions were made.

OOE should evolve through evidence and argument rather than preference or authority.

## Proposal types

An OOEP may have one of the following types:

### Foundation

A Foundation OOEP affects the philosophical or axiomatic basis of OOE.

These proposals should be rare and treated with particular care.

### Specification

A Specification OOEP defines or changes normative OOE concepts, structures, semantics, or required behavior.

### Process

A Process OOEP defines how the project itself operates.

This document is a Process OOEP.

### Informational

An Informational OOEP records guidance, explanation, rationale, or best practices that are not normative.

## Proposal statuses

An OOEP may have one of the following statuses:

### Draft

The proposal is under active development and has not been accepted.

### Review

The proposal is considered ready for broader review.

### Accepted

The proposal has been accepted as part of Outcome-Oriented Engineering.

### Rejected

The proposal has been rejected and is retained for historical context.

### Superseded

The proposal has been replaced by a later OOEP.

### Withdrawn

The author has withdrawn the proposal before acceptance or rejection.

## Required sections

Each OOEP should include the following sections unless clearly unnecessary:

- Title
- Status
- Author
- Created date
- Type
- Requires
- Supersedes
- Abstract
- Motivation
- Specification or proposal
- Rationale
- Alternatives considered
- Open questions

## Acceptance criteria

A proposal should not be accepted merely because it is interesting.

A proposal should be accepted only if it strengthens OOE as a discipline.

Before acceptance, a proposal should answer these questions:

- Does this fit within the foundations of OOE?
- Does this clarify or strengthen the discipline?
- Does this introduce unnecessary terminology?
- Does this belong in the foundation, the specification, examples, or external writing?
- Can an experienced engineer understand the proposal without knowing any private implementation details?
- Would the idea still make sense if today's artificial intelligence systems disappeared?

## Stewardship

Initial stewardship belongs to the repository maintainer.

The maintainer is responsible for preserving coherence, encouraging useful critique, and preventing the discipline from becoming a collection of unrelated ideas.

Future governance may define additional roles, maintainers, working groups, or voting procedures.

This first draft intentionally keeps governance lightweight.

## Relationship to implementations

OOE is implementation independent.

An accepted OOEP may influence reference implementations, runtimes, tools, or commercial systems, but no implementation defines the discipline by itself.

Implementations may experiment ahead of the specification.

The specification should incorporate implementation experience only when the resulting concept is useful beyond a single product or tool.

## Versioning

The OOE specification should eventually adopt explicit versioning.

Until then, accepted OOEPs serve as the historical record of changes.

A future OOEP should define formal versioning rules.

## Open questions

- When should OOE move from maintainer stewardship to a broader governance model?
- Should accepted OOEPs be immutable, or may they be amended in place?
- How should disputes over foundational axioms be resolved?
- Should examples and reference implementations require OOEPs, or only specification changes?
- What level of implementation evidence should be required before accepting a specification proposal?
