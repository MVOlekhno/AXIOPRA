---
axiopra:
  id: AXP-MM-README
  kind: metamodel.guide
  version: 0.1.0
  status: active
  stage: AXP-STAGE-01
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Entry guide to the artifact and relation metamodel.
  relations:
    depends_on: [AXP-FND-CONSTITUTION]
    produces: [AXP-MM-ARTIFACT, AXP-MM-RELATION]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-001, AXP-SEM-008]
  learning:
    external: A map of the machine-checkable knowledge model.
    internal: The reader can explain how text becomes a typed graph without pretending that all meaning is deterministic.
---

# Metamodel

## Why this stage exists

A linter cannot check a philosophy. It can check declared objects, relations, lifecycle states, schemas, and invariants. The metamodel is the bridge between human meaning and machine verification.

## Primary question

**What is the smallest useful, machine-checkable unit of engineering knowledge, and how may such units relate?**

## Outputs

- [`artifact-model.md`](artifact-model.md) defines nodes.
- [`relation-model.md`](relation-model.md) defines edges and graph invariants.
- [`../../schemas/artifact.schema.json`](../../schemas/artifact.schema.json) validates artifact metadata.
- [`../../templates/artifact.md`](../../templates/artifact.md) guides authors.

## Boundary

The metamodel verifies declared structure and traceability. It does not prove that a domain statement is true. Semantic audit, evidence, tests, formal proof, and accountable human review remain necessary.
