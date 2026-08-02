---
axiopra:
  id: AXP-TEMPLATE-REPLACE
  kind: replace.me
  version: 0.1.0
  status: draft
  stage: AXP-STAGE-00
  language: en
  confidence: unverified
  owners: [REPLACE]
  summary: Replace with one sentence describing the artifact's sole primary purpose.
  relations:
    depends_on: []
    produces: []
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-001, AXP-SEM-003, AXP-SEM-008]
  learning:
    external: Replace with the visible result created by this artifact.
    internal: Replace with what the user should be able to explain after completing it.
---

# Artifact title

## Why this artifact exists

State the problem this artifact prevents or resolves. Do not describe the file format as its purpose.

## Primary question

Write one question. If several unrelated questions are required, split the artifact.

## Audience and decision owner

Who reads it, who supplies domain truth, and who approves it?

## Inputs and dependencies

List required artifact IDs, evidence, assumptions, and external inputs. Explain why each is necessary.

## Current understanding

Describe the smallest coherent model of the subject before making decisions.

## Claims and decisions

For each important statement, label it as one of:

- sourced fact;
- inference;
- assumption;
- accepted decision;
- hypothesis;
- unknown.

## Alternatives and consequences

Record serious alternatives, why they were not selected, and what would cause reconsideration.

## Constraints, boundaries, and failure modes

State what must be true, what must not happen, what is out of scope, and how failure is recognized.

## Visible external result

Show what now exists and how the user can inspect it.

## Internal learning result

Complete this sentence: **After this artifact, the user can explain...**

## Verification plan

Identify deterministic rules, semantic questions, tests, evidence, proofs, and human approval appropriate to the claim.

## Open uncertainty

List unresolved matters explicitly. Never hide uncertainty inside confident prose.

## Self-review questions

1. What uncertainty did this artifact reduce?
2. Does it answer one primary question?
3. Are important terms defined consistently?
4. Did I distinguish fact, inference, decision, assumption, hypothesis, and unknown?
5. Are inputs and relation targets complete?
6. Are alternatives and trade-offs represented honestly?
7. What could make this artifact wrong?
8. What visible capability now exists?
9. Can the user explain the result without reading implementation code?
10. Is the handoff to the next artifact sufficiently constrained?

## Definition of done

State objective completion criteria and the authority that may mark the artifact active.

## Handoff

Name the next artifact ID or the question the next stage must answer.
