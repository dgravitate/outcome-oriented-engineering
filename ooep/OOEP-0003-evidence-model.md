# OOEP-0003: Evidence Model

Status: Accepted  
Author: David Graves  
Created: 2026-07-01  
Type: Specification  
Requires: OOEP-0001, OOEP-0002  
Supersedes: None

## Abstract

This proposal defines the first draft of the Evidence Model for Outcome-Oriented Engineering.

The Evidence Model explains how observations become evidence, how evidence relates to outcomes, and why evidence must be evaluated for sufficiency, freshness, and conflict.

## Motivation

OOE asserts that outcomes require evidence.

This requires a distinction between activity, observation, evidence, and validation.

A test run is an observation.

A passing test may become evidence that a behavior holds under tested conditions.

That evidence may or may not be sufficient to validate the outcome.

Without an evidence model, engineering systems tend to treat artifacts as completion. A merged pull request, a passing build, or a completed deployment becomes a proxy for truth.

OOE requires a more precise model.

## Specification

The Evidence Model begins with five concepts:

1. Observation
2. Evidence
3. Claim
4. Sufficiency
5. Freshness

It also recognizes conflict as a normal property of engineering evidence.

### Observation

An Observation is an event, measurement, or reviewable fact that reveals something about engineering reality.

Examples:

- A test passes.
- A benchmark produces a latency measurement.
- A deployment completes.
- Telemetry shows an increase in errors.
- A reviewer identifies a security issue.
- A customer fails to complete a workflow.

Observations are not automatically evidence.

They become evidence only when interpreted in relation to a claim about an outcome.

### Evidence

Evidence is interpreted information derived from one or more observations that supports or weakens a claim about engineering reality.

Evidence is always evidence for or against something.

It should be attached to a claim, outcome, constraint, or validation decision.

### Claim

A Claim is a statement about engineering reality that evidence may support or weaken.

Examples:

- Users can sign in using the external identity provider.
- Existing username/password sign-in still works.
- Authentication events are audit logged.
- Tokens are not stored in plaintext.
- Production authentication failure rates did not increase after release.

Claims make evidence evaluable.

### Sufficiency

Sufficiency describes whether available evidence is enough to validate a claim or outcome.

Evidence can support a claim without being sufficient to validate it.

For example, unit tests may support a behavioral claim but may not be sufficient to validate production readiness.

### Freshness

Freshness describes whether evidence is recent and relevant enough to remain useful.

Evidence may become stale when engineering reality changes.

For example, a passing test result from before a major refactor may no longer provide useful evidence for the current system.

### Conflict

Evidence may conflict.

A test suite may pass while production telemetry shows failure.

A security review may approve one aspect of a change while identifying risk in another.

An outcome may have strong evidence for one claim and weak evidence for another.

Conflicting evidence should not be hidden.

It should be represented and evaluated.

## Rationale

The Evidence Model is intentionally separate from the Outcome Lifecycle.

The lifecycle defines where an outcome stands.

The Evidence Model defines why it stands there.

This separation allows future implementations to support multiple evidence strategies without changing the lifecycle itself.

## Alternatives considered

### Evidence as binary proof

One alternative is to treat evidence as proving or disproving an outcome.

This draft avoids that model because engineering evidence is often incomplete, contextual, stale, or conflicting.

### Confidence scores

Another alternative is to reduce evidence to a numeric confidence score.

This draft avoids making confidence primary. Confidence may become a useful derived property, but OOE should preserve the evidence and reasoning behind a conclusion.

### Test-centric evidence

A simpler model could treat tests as the primary evidence type.

This draft rejects that limitation because many engineering outcomes require telemetry, reviews, customer behavior, documentation, compliance checks, operational evidence, or human judgment.

## Open questions

- Should evidence be categorized by source, strength, freshness, or claim type?
- How should conflicting evidence be represented in a machine-readable format?
- How should evidence sufficiency be determined for different outcome classes?
- Should OOE define standard evidence levels?
- How should human judgment be represented alongside automated observations?
