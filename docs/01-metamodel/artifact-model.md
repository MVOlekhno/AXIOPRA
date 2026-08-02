---
axiopra:
  id: AXP-MM-ARTIFACT
  kind: metamodel.artifact
  version: 0.1.0
  status: active
  stage: AXP-STAGE-01
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Definition, syntax, lifecycle, and invariants of an AXIOPRA artifact.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-MM-README]
    constrains: [AXP-MTH-STAGES, AXP-VER-MODEL]
    realizes: [AXP-FND-CONSTITUTION]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-004]
    semantic: [AXP-SEM-001, AXP-SEM-004, AXP-SEM-008]
  learning:
    external: A minimal artifact contract implementable by the Rust verifier.
    internal: The reader can distinguish artifact identity, content, relations, evidence, verification, and lifecycle.
---

# Artifact Model

## Definition

An **engineering artifact** is a versioned unit of declared knowledge or intent that has one primary purpose, a stable identifier, typed relations, a human-readable explanation, machine-readable metadata, and explicit conditions under which it may be trusted or changed.

A Markdown file may contain one canonical artifact in v0.1. Other serializations may be added later through RFCs.

## Linguistic model

- **Nouns** identify entities and become artifact nodes: user, requirement, road alignment, contract, test, proof, decision.
- **Verbs** express typed relations: derives from, refines, constrains, realizes, verifies, tests, proves, supersedes.
- **Adjectives and measurements** become metadata or properties: active, critical, provisional, 2.5 percent, reviewed.
- **Modal and logical statements** become constraints: must, must not, exactly one, at least one, implies.
- **Free narrative** explains meaning, context, alternatives, and consequences.

The platform does not eliminate natural language. It places its checkable commitments into a structure.

## Required machine layer

Each canonical Markdown artifact contains YAML front matter with the root key `axiopra` and these required fields:

- `id`: globally unique stable identifier inside the project namespace;
- `kind`: semantic artifact type;
- `version`: semantic version of the artifact contract;
- `status`: lifecycle state;
- `stage`: lifecycle stage identifier;
- `language`: narrative language;
- `confidence`: epistemic maturity;
- `owners`: accountable maintainers;
- `summary`: one-sentence purpose;
- `relations`: typed outgoing edges;
- `verification`: declared structural and semantic checks;
- `learning.external`: visible project result;
- `learning.internal`: understanding the user should gain.

The JSON Schema is normative for syntax. This document is normative for meaning. A conflict between them is a defect that blocks release.

## Required human layer

Every working artifact should answer:

1. Why does it exist?
2. What is its primary question?
3. What inputs and assumptions does it use?
4. What decisions or claims does it make?
5. What alternatives and boundaries matter?
6. What visible output does it create?
7. What should the user understand afterward?
8. How is it checked?
9. What remains unknown?
10. What does it hand to the next artifact?

## Lifecycle

- `hypothesis`: an idea that may be useful but lacks sufficient validation;
- `draft`: being developed and not authoritative;
- `review`: proposed for adoption;
- `active`: current source of truth within its declared scope;
- `deprecated`: still readable but must not be used for new work;
- `retired`: historical record only.

Status does not equal confidence. An active project decision may have provisional confidence; the uncertainty must remain explicit.

## Epistemic confidence

- `unverified`: no meaningful check completed;
- `provisional`: reasoned and usable with known uncertainty;
- `validated`: supported by evidence, tests, reference use, or review appropriate to the claim;
- `canonical`: adopted as a stable platform rule through governance.

## Artifact invariants

1. IDs are unique and never silently reused.
2. Active artifacts validate against the declared schema.
3. Every relation target exists or is an explicitly declared external reference.
4. Every artifact has one primary purpose.
5. Narrative and metadata do not contradict each other.
6. An active artifact contains no unresolved placeholder that changes meaning.
7. Every active requirement has, or explicitly waives, a downstream verification strategy.
8. Every stage artifact declares both external and internal outcomes.
9. Supersession preserves history and migration information.
10. Generated graph views are reproducible and are not manually edited as sources of truth.

## Quality gate

An artifact may become `active` only after schema validation, relation validation, semantic review, explicit treatment of unknowns, and accountable approval appropriate to its risk profile.
