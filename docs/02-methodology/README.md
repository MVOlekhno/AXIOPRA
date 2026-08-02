---
axiopra:
  id: AXP-MTH-README
  kind: methodology.guide
  version: 0.1.0
  status: active
  stage: AXP-STAGE-00
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Entry guide to the AXIOPRA lifecycle, stage artifacts, and quality gates.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-MM-ARTIFACT, AXP-MM-RELATION]
    produces: [AXP-MTH-STAGES]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-001, AXP-SEM-006, AXP-SEM-008]
  learning:
    external: A clear entry point to the end-to-end engineering lifecycle.
    internal: The reader can identify the current stage, its purpose, visible result, gate, and handoff.
---

# Methodology

## Why this layer exists

Individual techniques answer different questions. Working Backwards clarifies value; DDD clarifies domain meaning; specifications and contracts clarify behaviour and obligations; types remove invalid states; Rust delivers a practical system; tests and proofs provide different evidence. AXIOPRA supplies the sequence and traceability between them.

## Primary question

**Which uncertainty must be reduced next, and what artifact proves that the reduction happened?**

## Canonical lifecycle

The current lifecycle is defined in [`stages.md`](stages.md).

Each stage must state:

- why it exists;
- its primary question;
- required inputs;
- allowed and deferred decisions;
- visible external result;
- internal learning result;
- common mistakes and evidence dossier;
- deterministic and semantic checks;
- definition of done;
- handoff to the next stage.

## Iteration rule

The lifecycle is not a waterfall. When later work reveals an upstream defect, reopen the affected artifact explicitly, record the reason and impact, restore consistency, and rerun downstream gates. Quietly editing history is forbidden.

## Visible result

At any moment a user can locate the current stage and answer: what is being decided, what is already known, what is still uncertain, and what completion unlocks next.
