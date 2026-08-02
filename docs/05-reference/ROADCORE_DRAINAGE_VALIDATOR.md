---
axiopra:
  schema_version: "0.1.0"
  id: axp.reference.roadcore-drainage-validator
  kind: reference-project
  title: RoadCore Drainage Validator
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  owner: MVOlekhno
  language: en
  summary: First domain reference project for validating the AXIOPRA lifecycle on longitudinal road profiles and drainage logic.
  tags:
    - reference-project
    - civil-engineering
    - roads
    - drainage
    - rust
    - lean
  depends_on:
    - axp.methodology.lifecycle
    - axp.verification.trust-model
  relations:
    - type: observes
      target: axp.methodology.lifecycle
    - type: references
      target: axp.verifier.rust-core
    - type: references
      target: axp.proofs.lean
  claims:
    - id: C-001
      statement: Longitudinal road profile and drainage validation provides a small but meaningful domain for testing geometry, units, invariants, contracts, Rust types, property tests, and selective proof.
      evidence_class: expert-judgment
      confidence: medium
      evidence:
        - Initial domain selection by a civil engineer specializing in roads and master planning
  assumptions:
    - id: A-001
      statement: The first reference-project scope can remain independent of full CAD file integration.
      status: active
    - id: A-002
      statement: A simplified one-dimensional flow model is sufficient for the first vertical slice.
      status: active
  constraints:
    - id: K-001
      statement: The reference project validates the methodology and does not claim to replace hydraulic design software or professional review.
      status: active
  human_outcome: The reader understands why this domain was selected and what the first vertical slice will and will not validate.
  machine_outcome: The roadmap and lifecycle have a resolvable reference-project node with explicit scope and dependencies.
  verification:
    structural: required
    semantic: required
    human_review: required
    domain_review: required
    empirical: required
    formal: recommended
    notes: Formal verification is selective; domain and empirical validation remain mandatory.
  review:
    cadence_days: 60
    required_roles:
      - civil-road-domain-reviewer
      - rust-reviewer
      - verification-reviewer
    expiry_behavior: warn
  supersedes: []
  external_references: []
---

# RoadCore Drainage Validator

## 1. Purpose

RoadCore Drainage Validator is the first engineering reference project for AXIOPRA. It will test whether the methodology can turn a real civil-engineering concern into a coherent artifact graph, a safe Rust implementation, executable evidence, and one carefully bounded formal proof.

It is a reference implementation and methodology experiment — not yet a commercial CAD module.

## 2. Initial user

A road or site-development designer who reviews a longitudinal profile and needs early warning about drainage-related geometric problems before issuing design documentation.

## 3. Initial problem hypothesis

Longitudinal profiles, surfaces, culverts, channels, and outlets are often reviewed through a mixture of software tools, visual inspection, calculations, and engineer experience. The first module will explore whether explicit rules and traceability can identify selected issues consistently and explain why each finding matters.

This statement remains a hypothesis until the Working Backwards and research stages provide evidence and domain review.

## 4. Candidate vertical-slice scope

Inputs:

- ordered alignment stations;
- design elevations at stations or breakpoints;
- segment gradients;
- optional surface elevations;
- drainage outlets;
- simplified locations and invert elevations of pipes or channels;
- units, tolerances, and coordinate/reference metadata.

Candidate checks:

- station order and duplicate stations;
- missing or inconsistent units;
- gradient/elevation consistency;
- flat or reverse-gradient segments under configurable rules;
- local low points without a declared discharge path;
- outlet elevation incompatible with the connected profile or drainage element;
- discontinuities exceeding a declared tolerance;
- incomplete traceability between a finding, rule, input, and suggested next engineering question.

Outputs:

- typed findings with severity and rule IDs;
- exact source station or interval;
- explanation of the violated rule;
- evidence and assumptions;
- visualization-ready profile annotations;
- machine-readable result for downstream CAD integration.

## 5. Explicit non-goals for the first slice

- full two-dimensional surface-flow simulation;
- hydraulic sizing of pipes, channels, or culverts;
- rainfall/runoff modeling;
- automatic design approval;
- replacement of domain expert review;
- direct dependency on one CAD product or proprietary format;
- proof that the entire drainage design is safe or correct.

## 6. Domain concepts to model

Initial candidates:

- station;
- elevation;
- length and gradient;
- profile point and profile segment;
- tolerance;
- local minimum and local maximum;
- drainage direction;
- outlet;
- pipe, culvert, or channel connection;
- invert elevation;
- discharge path;
- validation rule;
- finding;
- evidence location.

Each quantity must carry units and validity constraints rather than being represented as an unqualified floating-point number throughout the system.

## 7. Methodology artifacts to produce

1. Press release and FAQ.
2. User/problem/outcome model.
3. Ubiquitous language and domain examples.
4. Domain invariants and boundary assumptions.
5. Observable specifications and acceptance examples.
6. Contracts for profile construction and validation.
7. Rust type model and error taxonomy.
8. Unit, example, boundary, and property-based tests.
9. Formal-proof selection decision.
10. One Lean proof if the selected proposition is stable and valuable.
11. Traceability and assurance report.
12. Reflection on methodology usability and ceremony.

## 8. Candidate proof targets

No proof target is accepted yet. Candidates for evaluation include:

- a constructed profile with strictly increasing stations has an unambiguous segment order;
- under a simplified monotone-gradient model, flow direction along a segment is consistent with elevation order;
- a particular graph algorithm reports every unreachable declared low point under explicit finite-graph assumptions;
- a verified transformation preserves station order and unit consistency.

The selected theorem must be small, explicit, stable, and connected to a real engineering risk. The proof must not be advertised as validation of the entire drainage system.

## 9. Success criteria for the reference project

The reference project succeeds as a methodology test when:

- a civil engineer can inspect and challenge the domain model;
- important rules trace from user promise to specification, implementation, and evidence;
- Rust types eliminate at least several meaningful invalid states;
- diagnostics are understandable without reading source code;
- intentional defects are caught by the appropriate assurance layers;
- the user can maintain cognitive synchronization through the full workflow;
- reflection identifies both value and unnecessary ceremony;
- proposed methodology changes enter governance instead of silently altering the canon.

## 10. First next action

Apply Stage 1, Working Backwards, to this reference project and create the press release as the first product artifact only after the Phase 1 foundation graph passes its initial structural review.
