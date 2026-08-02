---
axiopra:
  id: AXP-FND-CONSTITUTION
  kind: foundation.constitution
  version: 0.1.0
  status: active
  stage: AXP-STAGE-00
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Binding laws for the architecture, use, and evolution of AXIOPRA.
  relations:
    depends_on: [AXP-FND-MANIFESTO]
    constrains: [AXP-MM-ARTIFACT, AXP-MM-RELATION, AXP-MTH-STAGES, AXP-VER-MODEL]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-002, AXP-SEM-005, AXP-SEM-008]
  learning:
    external: A versioned set of binding platform laws.
    internal: The reader can decide whether a proposed feature belongs in AXIOPRA and how it may enter the canon.
---

# AXIOPRA Constitution

## Article 1 — Primacy of intent

Every implementation claim must trace to an explicit human or system intent. Untraceable functionality is accidental complexity until justified.

## Article 2 — Artifact integrity

Canonical knowledge exists as identified, versioned artifacts with explicit purpose, lifecycle, relations, verification, external result, and learning result.

## Article 3 — Dual readability

Canonical artifacts must be understandable to a human and parseable by a machine. Generated representations may assist but may not replace the canonical source without an approved migration.

## Article 4 — Traceability

The platform must support traversal from user promise to domain meaning, specification, contract, type, implementation, test, proof, release evidence, and lesson—and back again where those artifacts exist.

## Article 5 — Intellectual honesty

Fact, evidence, inference, assumption, decision, hypothesis, and unknown must not be presented as interchangeable categories.

## Article 6 — Visible progress

A stage is incomplete until the user can inspect what was created, what was verified, what remains uncertain, and what capability now exists that did not exist before.

## Article 7 — Cognitive synchronization

The system must not optimize execution while allowing the human to lose the thread. Agents must maintain a context compass and restore orientation before continuing when understanding diverges from activity.

## Article 8 — Independent verification

Structural, semantic, empirical, formal, and human checks are independent confidence sources. Their results must remain distinguishable.

## Article 9 — Risk-proportional rigor

Projects may select lighter or stronger profiles, but the selected profile, rationale, residual risk, and waived checks must be explicit.

## Article 10 — Deterministic core

Repository structure, metadata schema, identifiers, graph integrity, lifecycle rules, and declared traceability are checked by a deterministic verifier whose primary implementation language is Rust.

## Article 11 — Selective formalism

Lean, Idris, logic programming, and related methods are used where they provide justified assurance or explanatory value. They are not mandatory decoration.

## Article 12 — Vendor neutrality and portability

The project must remain usable without dependence on one LLM vendor, private conversation, or proprietary context format.

## Article 13 — Controlled recursive improvement

No agent, tool, maintainer, or popularity signal may silently rewrite the canon. Canonical change requires an RFC, alternatives, consequences, evidence or a clearly marked hypothesis, reference-project evaluation, review, and version impact.

## Article 14 — Reproducibility

A competent independent user must be able to reconstruct the declared result from the repository, toolchain declaration, inputs, and verification records.

## Article 15 — Finite foundation, extensible system

The Foundation stays small and stable. Specialization belongs in profiles, plugins, schemas, reference projects, and higher layers unless a universal invariant is demonstrated.

## Constitutional gate

A proposal is unconstitutional when it hides reasoning, breaks traceability without migration, merges independent trust signals into one score, removes human accountability, introduces vendor lock-in for essential knowledge, or modifies canonical semantics outside the RFC process.

## Amendment process

1. Create an RFC using `templates/rfc.md`.
2. State the problem, affected articles, alternatives, evidence, risks, compatibility, migration, and falsification criteria.
3. Validate the proposal in at least one reference project unless the change only corrects an unambiguous defect.
4. Run structural and semantic review.
5. Record the decision and version impact.
6. Merge the amendment and dependent artifact updates atomically.

Foundation v0.1 is provisional. Its authority comes from explicit adoption and continued evidence, not from claiming perfection.
