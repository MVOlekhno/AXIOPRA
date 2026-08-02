---
axiopra:
  schema_version: "0.1.0"
  id: axp.methodology.lifecycle
  kind: methodology
  title: AXIOPRA Engineering Lifecycle
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.foundation.manifesto
    - axp.foundation.constitution
    - axp.metamodel.core
  relations:
    - type: governed-by
      target: axp.foundation.governance
    - type: constrained-by
      target: axp.verification.trust-model
    - type: instantiated-by
      target: axp.reference.roadcore-drainage-validator
  human_outcome: The user can see the complete path from vague intent to implementation, evidence, and controlled learning.
  machine_outcome: Each stage has explicit inputs, outputs, gates, and traceability obligations.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# AXIOPRA Engineering Lifecycle

## 1. Purpose

This lifecycle is a meta-methodology: it explains when and why to combine Working Backwards, Domain-Driven Design, specification, contracts, type-driven design, tests, formal proofs, and reflection.

It is not a rigid waterfall. The ordering expresses dependency: later claims depend on earlier clarity. Iteration is expected, but changes must propagate through explicit relations rather than silently invalidating downstream work.

## 2. Entry: idea capture and risk triage

A user may begin with one sentence:

> I want to create a small graphical editor.

The system first creates an **idea artifact**, not production code.

Minimum entry questions:

- What kind of product or system is imagined?
- Who might use it?
- What outcome should become easier or possible?
- Is this an experiment, personal tool, commercial product, regulated system, or safety-relevant system?
- What data, money, safety, privacy, or legal consequences could be involved?
- What is explicitly unknown?

Visible result:

- a named project;
- a one-paragraph intent statement;
- an initial uncertainty ledger;
- a provisional risk profile;
- the first context compass.

This is an entry gate, not a substitute for Working Backwards.

## 3. Stage template

Every lifecycle stage must contain:

1. why the stage exists;
2. the uncertainty it reduces;
3. the main question;
4. required and optional inputs;
5. questions the user should answer;
6. expected artifacts;
7. typical errors and anti-patterns;
8. deterministic checks;
9. semantic and human review checks;
10. visible external result;
11. cognitive result;
12. quality gate;
13. handoff relations to the next stage;
14. reflection questions;
15. industrial cases, failures, evidence, limitations, and sources in the research layer.

## 4. Stage 1 — Working Backwards

### Why it exists

Prevent teams and agents from solving an attractive technical problem that does not create a meaningful user outcome.

### Uncertainty reduced

Who needs the product, which problem matters, what changes for the user, and why the product should exist now.

### Main question

> What user-visible promise are we making, and why should anyone care?

### Core questions

- Who is the primary user?
- In what situation does the problem occur?
- What is painful, slow, risky, expensive, or impossible today?
- What outcome matters more than a list of features?
- Why do existing alternatives fail for this user and context?
- What must the product not become?
- What evidence would show the problem is real?
- What would make the project not worth building?
- Can a non-team member understand the promise in two minutes?
- Which statements are facts, assumptions, and aspirations?

### Required artifacts

- press release;
- internal FAQ;
- user/problem/outcome artifacts;
- non-goals;
- success and failure signals;
- assumption and uncertainty ledger.

### Visible result

A plain-language story of the finished product and a list of hard questions that expose weak assumptions.

### Cognitive result

The user can explain who benefits, what changes, and why code is not yet the question.

### Gate

Proceed when the promise is understandable, scoped, non-contradictory, and supported by explicitly labeled assumptions. Do not demand market certainty for a small experiment, but do not hide uncertainty behind feature lists.

### Handoff

Product promises `motivate` and `constrain` the domain model.

## 5. Stage 2 — Domain-Driven Design

### Why it exists

Create a shared model of the problem space before software structures accidentally redefine the domain.

### Uncertainty reduced

Which concepts exist, what words mean, where boundaries lie, and which rules must always hold.

### Main question

> What must be true in the problem domain for the promised outcome to make sense?

### Core questions

- What are the domain's most important nouns and verbs?
- Which terms are ambiguous or used differently by different people?
- What has identity over time?
- What is defined only by value?
- What events change state?
- Which invariants must never be broken?
- Which boundaries require separate models or vocabularies?
- Which concepts belong to the domain and which belong only to the UI or implementation?
- Where is expert knowledge missing?
- What examples and counterexamples test the model?

### Required artifacts

- ubiquitous-language glossary;
- bounded contexts and context map where needed;
- entities, value objects, domain events, services, policies, and invariants;
- examples and counterexamples;
- unresolved domain questions;
- domain assumptions and expert-review records.

### Visible result

A concept map and glossary that a domain expert and developer can inspect together.

### Cognitive result

The user can describe the product using stable domain language rather than vague feature language.

### Gate

Proceed when critical terms have authoritative meanings, central invariants are explicit, and unresolved expert questions are visible. The model need not cover every future feature.

### Handoff

Domain concepts and invariants `constrain` specifications and contracts.

## 6. Stage 3 — Specification-Driven Development

### Why it exists

Turn product promises and domain rules into observable, reviewable behavior before committing to implementation details.

### Uncertainty reduced

What the system must do, under which conditions, with which outputs and failure behavior.

### Main question

> What observable behavior would demonstrate that the system fulfills the intended outcome?

### Core questions

- What are the main scenarios?
- What inputs, states, and actors are involved?
- What output or state change is expected?
- What are boundary and invalid cases?
- What quantities, units, tolerances, precision, and coordinate systems apply?
- What errors must be distinguishable?
- What acceptance criteria are objectively checkable?
- Which requirements conflict or compete?
- Which behavior is intentionally unspecified?
- What examples would falsify the current interpretation?

### Required artifacts

- behavioral specifications;
- scenarios and examples;
- acceptance criteria;
- constraints, units, tolerances, and data rules;
- error taxonomy;
- requirement coverage links;
- open specification decisions.

### Visible result

A set of examples and rules showing what success and failure look like without requiring knowledge of internal code.

### Cognitive result

The user can judge proposed behavior before paying for its implementation.

### Gate

Proceed when critical behavior is observable, major boundaries are represented, and acceptance criteria do not depend on unstated interpretation.

### Handoff

Specifications are `refined-by` contracts and `implemented-by` components.

## 7. Stage 4 — Contract-Driven Development

### Why it exists

Make responsibilities between components explicit and localize blame when an obligation is violated.

### Uncertainty reduced

Who guarantees what, before and after an operation, and which conditions must remain invariant.

### Main question

> What must the caller provide, what must the component guarantee, and what must always remain true?

### Core questions

- What are the preconditions?
- What are the postconditions?
- What state invariants hold before and after operations?
- Which failures are expected and recoverable?
- Who owns validation at each boundary?
- What resources, timing, ordering, or concurrency obligations exist?
- Which contracts are externally stable?
- How are contract violations represented and diagnosed?
- Which assumptions can become types?
- Which contracts require runtime checks even after type checking?

### Required artifacts

- interface contracts;
- preconditions, postconditions, and invariants;
- error and responsibility model;
- boundary validation policy;
- contract examples and violation cases;
- compatibility obligations.

### Visible result

A responsibility map showing what each boundary accepts, guarantees, rejects, and reports.

### Cognitive result

The user can identify which side is responsible when a rule is violated.

### Gate

Proceed when critical obligations are unambiguous, testable or otherwise checkable, and consistent with specifications and domain invariants.

### Handoff

Contracts `constrain` type models, APIs, and implementations.

## 8. Stage 5 — Type-Driven Development

### Why it exists

Move stable constraints into representations that make invalid states difficult or impossible to construct.

### Uncertainty reduced

Which states are representable, which conversions are permitted, and which invariants the compiler can enforce.

### Main question

> Which mistakes can be prevented by construction rather than detected later?

### Core questions

- Which domain distinctions deserve separate types?
- Which raw primitives hide units, coordinate systems, identity, or validity?
- Which states are illegal?
- Which transitions require validation?
- What should be immutable?
- Where are ownership and lifetime boundaries?
- Which errors belong in `Result` or equivalent explicit channels?
- Where would a stronger type create excessive complexity?
- Which properties remain runtime or proof obligations?
- How will serialized and external data cross into trusted types?

### Required artifacts

- type model;
- legal state transitions;
- conversion and validation boundaries;
- error types;
- ownership and resource model;
- mapping from contracts to types and remaining runtime checks;
- architecture decisions for type trade-offs.

### Visible result

A diagram or code-level model showing which invalid states can no longer be represented.

### Cognitive result

The user understands that types are executable design decisions, not merely labels attached to data.

### Gate

Proceed when core representations preserve domain meaning, conversion boundaries are explicit, and complexity is proportionate to risk.

### Handoff

The type model `constrains` implementation and test generation.

## 9. Stage 6 — Test-Driven Development

### Why it exists

Create executable evidence for behavior, properties, boundaries, integrations, and regressions.

### Uncertainty reduced

Whether the implementation behaves as specified across known examples and systematically generated cases.

### Main question

> What executable evidence would expose an incorrect implementation quickly and clearly?

### Core questions

- Which acceptance examples become tests?
- Which domain invariants become property-based tests?
- What boundary, precision, and invalid-input cases matter?
- What integration contracts need independent tests?
- What regressions must never return?
- Which tests are deterministic and reproducible?
- What environments or external dependencies affect results?
- What mutations or fault injections test the tests themselves?
- Which behavior cannot be demonstrated sufficiently by tests?
- What evidence links each accepted obligation to a test or justified alternative?

### Required artifacts

- test plan and traceability map;
- unit, property, integration, end-to-end, and regression tests as appropriate;
- fixtures and generators;
- environment and reproducibility metadata;
- test results and uncovered obligations;
- defect and regression records.

### Visible result

A report that shows passed and failed properties, uncovered obligations, and exact diagnostics — not only a green badge.

### Cognitive result

The user can explain what the tests establish and, equally important, what they do not establish.

### Gate

Proceed toward release acceptance when required evidence paths pass for the selected risk profile and known gaps are accepted explicitly.

### Handoff

Tests `verify` specifications, contracts, invariants, and implementations within stated scope.

## 10. Stage 7 — Proof-Driven Development

### Why it exists

Provide machine-checked assurance for selected critical propositions where tests and review leave unacceptable residual risk.

### Uncertainty reduced

Whether a precisely formalized proposition follows from stated assumptions and definitions.

### Main question

> Which small set of stable, critical properties is worth proving formally?

### Core questions

- What exact proposition is being claimed?
- Why is the consequence of error high enough to justify proof cost?
- Are definitions and assumptions stable enough to formalize?
- What part of the production implementation corresponds to the formal model?
- Which gaps remain between model and implementation?
- Can a simpler algorithm or type eliminate the need for proof?
- What theorem prover and trusted computing base are involved?
- How will proof breakage be detected as models evolve?
- Who can review the formal statement for domain fidelity?
- What must never be implied by this proof?

### Required artifacts

- proof-selection decision;
- formal statement and assumptions;
- model-to-domain mapping;
- machine-checked proof source;
- toolchain and reproducibility data;
- model-to-implementation correspondence argument;
- explicitly documented assurance limits.

### Visible result

A reproducible proof check for a named proposition, linked to the exact requirement or invariant it supports.

### Cognitive result

The user can distinguish “the theorem is proved” from “the entire product is correct”.

### Gate

The proof is accepted only when the proposition reflects the intended domain property, assumptions are explicit, the proof checks reproducibly, and correspondence gaps are documented.

### Handoff

Proofs `prove` formal statements and contribute evidence to assurance profiles.

## 11. Stage 8 — Reflection and Evolution

### Why it exists

Convert project experience into inspectable learning without allowing uncontrolled changes to the methodology.

### Uncertainty reduced

What actually worked, what failed, where understanding was lost, and which lessons may transfer to future projects.

### Main question

> What did this project teach us, and what evidence would justify changing our future behavior?

### Core questions

- What did we expect?
- What actually occurred?
- Where did the user lose cognitive synchronization?
- Which artifacts created clarity and which created ceremony?
- Which defects escaped existing checks?
- Which checks produced false confidence or excessive noise?
- What assumptions were falsified?
- What lesson appears reusable?
- Where might that lesson fail to transfer?
- Should the result remain an observation, become a hypothesis, or enter the RFC pipeline?

### Required artifacts

- reflection report;
- lessons and counterexamples;
- evidence and limitations;
- proposed experiments or RFCs;
- deprecation candidates;
- updated uncertainty ledger;
- post-release review.

### Visible result

A map from observed outcomes to proposed improvements, with no silent canon changes.

### Cognitive result

The user understands how experience changes future decisions and why learning must be governed like code.

### Gate

Reflection is complete when lessons are scoped, evidence is linked, transfer assumptions are explicit, and any proposed canonical change has entered governance.

## 12. Tailoring by risk

AXIOPRA does not require identical ceremony for every project.

A conformance profile should consider:

- consequence of incorrect behavior;
- number and vulnerability of users;
- financial, physical, environmental, privacy, and legal exposure;
- reversibility of failure;
- novelty and domain uncertainty;
- operational lifespan;
- integration and supply-chain complexity.

Example profiles:

- **Explore** — personal experiments and disposable prototypes;
- **Build** — ordinary production software;
- **Assure** — high-consequence or regulated systems;
- **Research** — new methodology, rule engine, compiler, or formal model.

All profiles preserve identity, uncertainty disclosure, context compass, and honest evidence labeling. Profiles vary depth, required review, and assurance coverage.

## 13. Stage skipping and iteration

A stage may be abbreviated or skipped only through a decision artifact that states:

- which stage or outputs are omitted;
- why they add insufficient value in this context;
- risks created;
- compensating controls;
- accountable owner;
- conditions requiring the stage to be restored.

When downstream work reveals a flawed upstream assumption, return to the authoritative artifact, update it, and propagate impact through the graph. Do not patch only the code and leave the knowledge model false.

## 14. Progress and the context compass

AXIOPRA should show progress through completed evidence-bearing capabilities, not opaque percentages.

At each checkpoint, report:

```yaml
objective: <current outcome>
stage: <stage name>
visible_result: <artifact or view produced>
capability_gained: <what is now possible>
uncertainty_reduced:
  - <named uncertainty>
verified:
  - <property, scope, verifier>
unresolved:
  - <open question or risk>
next_step: <one meaningful action>
```

Dashboards may summarize coverage, but every metric must drill down to explicit artifacts and rules.

## 15. First reference project

The lifecycle will first be validated on **RoadCore Drainage Validator**, a small but real engineering module concerned with longitudinal road profile and drainage correctness.

The project will exercise:

- stations, elevations, gradients, surfaces, low points, outlets, pipes, and channels as domain concepts;
- measurable geometric and hydraulic constraints;
- contracts and strict Rust types;
- example and property-based tests;
- one carefully selected Lean proof;
- graph traceability from product promise to evidence;
- reflection on which parts of the methodology help or hinder a practicing civil engineer.

The reference project validates the methodology; it is not evidence that the methodology works universally.
