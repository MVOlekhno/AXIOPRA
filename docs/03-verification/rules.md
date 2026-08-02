---
axiopra:
  id: AXP-VER-RULESET
  kind: verification.ruleset
  version: 0.1.0
  status: active
  stage: AXP-STAGE-08
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Normative initial rule catalogue for the deterministic Rust verifier and LLM semantic auditor.
  relations:
    depends_on: [AXP-VER-MODEL, AXP-MM-ARTIFACT, AXP-MM-RELATION]
    realizes: [AXP-VER-MODEL]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-001, AXP-SEM-002, AXP-SEM-003]
  learning:
    external: Stable rule identifiers with unambiguous intent and expected findings.
    internal: The reader can distinguish a rule definition from a future implementation of that rule.
---

# Verification Rule Catalogue v0.1

This catalogue defines rule meaning. The Rust implementation, fixtures, diagnostics, and severity profiles will be specified before coding.

## Deterministic rules

- `AXP-RULE-001` — every discovered canonical Markdown artifact has front matter that validates against the declared schema.
- `AXP-RULE-002` — every artifact ID matches the project pattern and is unique.
- `AXP-RULE-003` — every internal relation target resolves to exactly one discovered artifact.
- `AXP-RULE-004` — lifecycle state and confidence use valid values and are treated independently.
- `AXP-RULE-005` — forbidden self-loops and graph cycles are absent.
- `AXP-RULE-006` — stage prerequisites and declared gates are satisfied or explicitly waived.
- `AXP-RULE-007` — each active release-bound requirement has a path to implementation and verification, or a documented risk waiver.
- `AXP-RULE-008` — active artifacts contain no meaning-changing placeholders or template markers.
- `AXP-RULE-009` — declared entry points, schemas, and referenced repository paths exist.
- `AXP-RULE-010` — generated graph and traceability outputs are reproducible from canonical sources.
- `AXP-RULE-011` — supersession preserves the replaced artifact and provides compatibility or migration information.
- `AXP-RULE-012` — each stage artifact declares an external visible result and an internal learning result.

## Semantic rules

- `AXP-SEM-001` — the artifact has one coherent primary purpose and answers its primary question.
- `AXP-SEM-002` — it has no unresolved contradiction with related active artifacts.
- `AXP-SEM-003` — it distinguishes evidence, inference, assumption, decision, hypothesis, and unknown.
- `AXP-SEM-004` — terminology is consistent within declared domain contexts.
- `AXP-SEM-005` — alternatives, consequences, limitations, and falsification conditions are represented honestly.
- `AXP-SEM-006` — user value remains traceable through downstream artifacts.
- `AXP-SEM-007` — boundaries, non-goals, and failure modes are explicit.
- `AXP-SEM-008` — the artifact reduces uncertainty and improves the user's ability to explain the project.

## Result vocabulary

- `PASS`: the rule was evaluated and no finding was detected.
- `WARN`: a non-blocking risk or incompleteness exists.
- `FAIL`: a declared gate or invariant is violated.
- `UNKNOWN`: the available information is insufficient to evaluate the claim.
- `NOT_RUN`: the verifier or audit was not executed.

A report must retain rule ID, artifact ID, severity, evidence location, explanation, and recommended correction. A combined confidence profile may summarize dimensions but must not erase individual results.
