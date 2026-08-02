---
axiopra:
  schema_version: "0.1.0"
  id: axp.schema.artifact-v0-1
  kind: specification
  title: Artifact Metadata Schema 0.1
  version: "0.1.0"
  status: draft
  maturity: exploratory
  canonical: true
  owner: AXIOPRA maintainers
  language: en
  summary: Registry artifact for the JSON Schema that validates the machine-readable metadata of AXIOPRA artifacts.
  tags:
    - schema
    - metamodel
  depends_on:
    - axp.metamodel.core
  relations:
    - type: specifies
      target: axp.metamodel.core
    - type: references
      target: axp.template.artifact
  claims:
    - id: C-001
      statement: The linked JSON Schema validates the minimal metadata object declared under the axiopra Markdown frontmatter key for schema version 0.1.0.
      evidence_class: structural-rule
      confidence: specified
      evidence:
        - schemas/artifact.schema.json
  assumptions: []
  constraints:
    - id: K-001
      statement: Cross-artifact graph rules are outside JSON Schema and must be evaluated after parsing and normalization.
      status: active
  human_outcome: The reader understands what the schema checks and which properties require the graph verifier.
  machine_outcome: The schema has a stable artifact ID and can be referenced from the metamodel and verification records.
  verification:
    structural: required
    semantic: required
    human_review: required
    empirical: required
    formal: not-required
    notes: Schema fixtures and the Rust verifier will provide empirical validation.
  review:
    cadence_days: 90
    required_roles:
      - metamodel-reviewer
      - verifier-reviewer
    expiry_behavior: block-acceptance
  supersedes: []
  external_references: []
---

# Schemas

## Artifact metadata schema

Canonical file for the current draft:

```text
schemas/artifact.schema.json
```

The schema validates the object under the `axiopra` key in Markdown YAML frontmatter or an equivalent normalized representation.

It checks local properties such as:

- identifier and version formats;
- artifact kind and lifecycle values;
- dependencies and relation shapes;
- claims, assumptions, and constraints;
- human and machine outcomes;
- verification and review plans.

It does not by itself check:

- whether referenced artifacts exist;
- duplicate IDs across files;
- allowed source and target kinds for a relation;
- graph cycles;
- traceability coverage;
- lifecycle history;
- contradictions across narratives;
- truth of claims.

Those properties belong to the Rust verifier, optional rule engine, semantic audit, tests, domain review, or formal proof as defined by the trust model.

## Schema evolution

A schema change must state whether it is:

- compatible clarification;
- backward-compatible extension;
- breaking structural change.

Breaking changes require a new schema version, fixtures, migration guidance, and an RFC once public compatibility is declared.

## Planned fixtures

```text
schemas/fixtures/valid/
schemas/fixtures/invalid/
```

Each invalid fixture will declare the expected diagnostic ID so the verifier tests both rejection and explanation quality.
