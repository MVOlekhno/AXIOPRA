---
axiopra:
  schema_version: "0.1.0"
  id: axp.verifier.rust-core
  kind: architecture
  title: AXIOPRA Deterministic Verifier
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  owner: AXIOPRA maintainers
  language: en
  summary: Architectural boundary and MVP responsibilities for the deterministic Rust verifier and engineering-knowledge compiler core.
  tags:
    - rust
    - verifier
    - compiler
    - diagnostics
  depends_on:
    - axp.metamodel.core
    - axp.verification.trust-model
    - axp.schema.artifact-v0-1
  relations:
    - type: implements
      target: axp.metamodel.core
    - type: verifies
      target: axp.schema.artifact-v0-1
    - type: constrained-by
      target: axp.verification.trust-model
  claims: []
  assumptions:
    - id: A-001
      statement: A deterministic local verifier can provide useful structural guarantees before semantic or formal layers are available.
      status: active
  constraints:
    - id: K-001
      statement: Core validation must not require network access or an LLM.
      status: active
    - id: K-002
      statement: Diagnostics must be stable, source-located, and reproducible for a repository revision and verifier version.
      status: active
  human_outcome: The reader understands what the Rust verifier will check, what it will not check, and how it may evolve into a compiler.
  machine_outcome: The verifier has a resolvable architecture node for roadmap, reference projects, and implementation artifacts.
  verification:
    structural: required
    semantic: required
    human_review: required
    empirical: required
    formal: optional
    notes: Implementation tests and invalid fixtures are required before claims of conformance.
  review:
    cadence_days: 60
    required_roles:
      - rust-reviewer
      - metamodel-reviewer
      - verifier-reviewer
    expiry_behavior: warn
  supersedes: []
  external_references: []
---

# AXIOPRA Deterministic Verifier

## Purpose

The deterministic verifier is the cold, repeatable layer that compiles repository artifacts into Engineering IR and checks precisely specified structural, lifecycle, graph, and policy properties.

It must be useful without an internet connection, model API, or proprietary service.

## MVP pipeline

```text
repository discovery
  -> Markdown/frontmatter parsing
  -> local schema validation
  -> source-span index
  -> artifact symbol table
  -> kind and relation registry resolution
  -> typed multigraph
  -> lifecycle and graph rules
  -> traceability profile rules
  -> diagnostics
  -> JSON IR and visualization export
```

## Planned crate boundaries

- `axiopra-model` — IDs, kinds, lifecycle, relations, claims, evidence, IR types.
- `axiopra-parser` — source discovery, Markdown/frontmatter parsing, source spans.
- `axiopra-graph` — typed multigraph, traversal, cycles, impact paths.
- `axiopra-rules` — versioned deterministic rules and conformance profiles.
- `axiopra-diagnostics` — stable rule IDs, severities, explanations, rendering.
- `axiopra-verifier` — orchestration API.
- `axiopra-cli` — human and CI interface.
- `axiopra-sdk` — external integration surface after the model stabilizes.

## Initial commands

```text
axiopra init
axiopra scan
axiopra validate
axiopra graph
axiopra status
axiopra explain <diagnostic-id>
```

## Design rules

1. Parsing and validation errors are values, not panics.
2. The same inputs, configuration, and version produce equivalent diagnostics.
3. Every diagnostic links to source spans, affected artifact IDs, governing rule, and remediation guidance.
4. Rules are versioned independently from presentation.
5. The IR remains serializable and inspectable.
6. Core semantics are not hidden inside an LLM prompt.
7. Automatic repair is opt-in and produces a reviewable change set.
8. Performance optimizations must not erase explanation traces.
9. Unsafe Rust is avoided unless an accepted decision documents necessity and invariants.
10. File-system, parser, and rule-engine boundaries are testable independently.

## MVP non-goals

- understanding all prose;
- judging product value;
- replacing domain review;
- generating complete applications;
- producing a universal confidence score;
- proving the full implementation correct;
- embedding Prolog, Datalog, or Lean before evidence justifies integration.

## Evolution toward a compiler

After the verifier works on reference projects, it may produce derived artifacts such as diagrams, traceability matrices, test skeletons, proof obligations, agent context packages, migration plans, and typed scaffolds.

Every generated output must retain provenance to source artifacts and remain subordinate to accepted human intent.
