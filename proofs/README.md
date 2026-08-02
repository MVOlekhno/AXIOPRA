---
axiopra:
  schema_version: "0.1.0"
  id: axp.proofs.lean
  kind: assurance-policy
  title: Selective Formal Verification with Lean
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  owner: AXIOPRA maintainers
  language: en
  summary: Policy and packaging rules for selecting, implementing, reproducing, and interpreting Lean proofs in AXIOPRA.
  tags:
    - lean
    - proof
    - formal-verification
  depends_on:
    - axp.verification.trust-model
    - axp.metamodel.core
  relations:
    - type: constrains
      target: axp.reference.roadcore-drainage-validator
    - type: references
      target: axp.foundation.constitution
  claims: []
  assumptions:
    - id: A-001
      statement: Selective proofs can provide useful assurance when propositions are stable, critical, and connected to production behavior.
      status: active
  constraints:
    - id: K-001
      statement: Every proof must link to an exact formal statement, assumptions, toolchain version, and correspondence argument.
      status: active
    - id: K-002
      statement: A proof must never be described as proving unrelated prose, implementation details, or the entire product.
      status: active
  human_outcome: The reader can decide when a proof is justified and interpret its assurance boundary correctly.
  machine_outcome: Formal artifacts have a stable root ID and packaging contract for future Lean projects.
  verification:
    structural: required
    semantic: required
    human_review: required
    domain_review: recommended
    empirical: recommended
    formal: required
    notes: This policy itself is not formally proved; individual proof packages must check reproducibly.
  review:
    cadence_days: 90
    required_roles:
      - formal-methods-reviewer
      - domain-reviewer
      - implementation-reviewer
    expiry_behavior: warn
  supersedes: []
  external_references: []
---

# Selective Formal Verification with Lean

## Role

Lean is the initial reference proof assistant for selected AXIOPRA propositions. It is not a universal documentation verifier and not the main production language.

## Proof-selection criteria

A candidate property is suitable when:

- failure has meaningful consequence;
- the property can be stated precisely;
- definitions and assumptions are sufficiently stable;
- proof cost is proportionate to risk;
- tests or types alone leave significant residual uncertainty;
- a reviewer can evaluate whether the formal statement matches the intended domain meaning;
- correspondence to production implementation can be explained and maintained.

## Required proof package

```text
proofs/<area>/<proof-id>/
├── README.md              # purpose, scope, assumptions, limits
├── STATEMENT.md           # human explanation and exact artifact links
├── lakefile.toml          # reproducible Lean project configuration
├── lean-toolchain         # pinned toolchain
├── Axiopra/<...>.lean     # definitions and proofs
├── CORRESPONDENCE.md      # model-to-domain and model-to-code argument
└── VERIFICATION.yaml      # reproducible result metadata
```

## Acceptance gate

A proof is accepted only when:

- Lean checks it with the pinned toolchain;
- no prohibited placeholders or admitted propositions remain;
- the exact proposition and assumptions are linked to artifact IDs;
- domain review accepts the intended meaning of the statement;
- implementation review documents correspondence and gaps;
- the assurance claim is worded no more broadly than the theorem;
- CI can reproduce the result.

## Initial candidate areas

- selected Engineering IR invariants;
- selected graph-transformation properties;
- RoadCore station ordering or simplified flow-direction properties;
- correctness of narrowly scoped validation algorithms.

The first proof target will be chosen through a proof-selection decision artifact after the Rust verifier and RoadCore domain model exist.
