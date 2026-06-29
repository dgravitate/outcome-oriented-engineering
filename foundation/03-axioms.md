# Axioms of Outcome-Oriented Engineering

The axioms of Outcome-Oriented Engineering are the statements treated as foundational within the discipline.

They are not implementation details.

They are not process recommendations.

They are the assumptions from which the rest of OOE is derived.

An axiom should be simple enough to understand, strong enough to support other ideas, and fundamental enough that Outcome-Oriented Engineering would no longer make sense if the axiom were false.

## Axiom 1: Engineering exists to produce outcomes

Software engineering does not exist to produce artifacts.

Artifacts matter because they help make outcomes true.

Source code, tests, documentation, deployments, tickets, diagrams, and metrics are valuable only insofar as they contribute to a desired engineering outcome.

## Axiom 2: Outcomes require evidence

An outcome is not complete because work was performed.

An outcome is complete only when sufficient evidence demonstrates that the desired state has been achieved.

Evidence may come from tests, reviews, telemetry, benchmarks, customer behavior, operational results, compliance checks, or other observations of reality.

## Axiom 3: Reality is observed, not assumed

The state of an engineering system is determined by observation.

Plans, intentions, predictions, estimates, and confidence are useful, but they do not define reality.

Reality is what the available evidence demonstrates.

## Axiom 4: Constraints define acceptable outcomes

A working solution is not necessarily an acceptable solution.

Engineering outcomes are valid only within the constraints that govern them.

Security, reliability, performance, cost, compliance, maintainability, accessibility, usability, architectural integrity, and human impact may all constrain whether an outcome is acceptable.

## Axiom 5: Workers advance outcomes but do not own them

Humans, artificial intelligence systems, automations, tools, teams, and organizations may all act as workers.

Workers perform activity, produce artifacts, and generate observations.

The outcome persists independently of any worker that advances it.

## Axiom 6: Progress is observable state change

Engineering progress occurs when observed reality moves closer to a desired outcome.

Activity that produces no observable change may be necessary, but it is not itself evidence of progress.

Progress must ultimately be reflected in what is known, what exists, what has changed, or what has been validated.

## Axiom 7: Engineering knowledge must outlive workers

Engineering work depends on knowledge that cannot safely remain only inside individual workers.

Intentions, constraints, decisions, evidence, failures, and completed outcomes should persist in forms that future workers can inspect and use.

A system that repeatedly rediscovers its own reality is losing engineering capacity.

## Derived principles

Several important OOE principles follow from these axioms.

Because outcomes require evidence, confidence is not enough.

Because reality is observed, engineering systems need observations.

Because constraints define acceptability, unconstrained code generation is insufficient.

Because workers do not own outcomes, engineering state must persist outside any individual worker.

Because progress is observable state change, activity should not be confused with completion.

Because knowledge must outlive workers, durable engineering memory is not optional in complex systems.

## Open questions

This first draft intentionally leaves several questions open:

- What amount of evidence is sufficient for a given outcome?
- How should conflicting evidence be represented?
- How should engineering reality be measured when observations are incomplete?
- Which principles are truly axiomatic, and which should move into the specification as derived concepts?
- How should OOE represent uncertainty without reducing engineering judgment to a single confidence score?

These questions are part of the ongoing development of the discipline.
