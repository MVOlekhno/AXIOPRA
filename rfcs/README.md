---
axiopra:
  id: AXP-RFC-PROCESS
  kind: governance.rfc-process
  version: 0.1.0
  status: active
  stage: AXP-STAGE-10
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Controlled process for proposing, validating, and adopting canonical AXIOPRA changes.
  relations:
    depends_on: [AXP-FND-CONSTITUTION]
    realizes: [AXP-FND-CONSTITUTION]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-003, AXP-SEM-005, AXP-SEM-008]
  learning:
    external: A reviewable lifecycle for changes to canonical platform semantics.
    internal: The reader can explain why discussion or agent output alone cannot modify the canon.
---

# AXIOPRA RFC Process

An RFC is required for changes to the Constitution, artifact schema, relation semantics, lifecycle stages, compatibility guarantees, verifier rule meaning, Engineering IR, plugin protocol, or other canonical behaviour.

## Lifecycle

1. `draft` — problem and alternatives are being developed.
2. `review` — ready for structural, semantic, technical, and governance review.
3. `accepted` — approved but not necessarily implemented.
4. `implemented` — canonical artifacts and migrations are complete.
5. `rejected` — preserved with reasons.
6. `withdrawn` — author stopped the proposal.
7. `superseded` — replaced by a later RFC.

## Required content

Use [`../templates/rfc.md`](../templates/rfc.md). Every RFC states the problem, scope, alternatives, evidence, consequences, compatibility, migration, reference validation, security and human-understanding effects, falsification criteria, and version impact.

## Rule

Discussion alone never changes the canon. The accepted RFC, canonical artifact updates, schema or verifier changes, migration instructions, and tests must remain traceably connected.
