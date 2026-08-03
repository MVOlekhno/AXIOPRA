---
axiopra:
  id: AXP-RFC-0001
  kind: governance.rfc
  version: 0.1.0
  status: active
  stage: AXP-STAGE-10
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Adopt English canonical artifacts with mandatory synchronized Russian localization and machine-readable drift metadata.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-RFC-PROCESS]
    produces: [AXP-FND-LANGUAGE]
    realizes: [AXP-FND-CONSTITUTION]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003, AXP-RULE-009]
    semantic: [AXP-SEM-002, AXP-SEM-004, AXP-SEM-005, AXP-SEM-008]
  learning:
    external: An adopted repository-wide localization architecture and migration plan.
    internal: The reader can explain why one canon plus synchronized translations is safer than two independently editable normative versions.
---

# RFC 0001 — Synchronized Russian Localization

## Status

**Adopted for implementation in Foundation v0.1.** The project owner approved first-class Russian documentation on 3 August 2026. The implementation remains provisional until the translation verifier and complete migration are tested.

## Problem

AXIOPRA is designed for global use, but its founder, first engineering reference project, and a major initial user group work in Russian. English-only normative documentation creates an unnecessary barrier. Two independently maintained normative languages, however, create a more dangerous problem: semantic divergence that tools and users may not notice.

The project needs a model that provides full Russian usability while preserving one coherent engineering graph.

## Decision

- English remains the canonical artifact language.
- Russian becomes a required first-class localization for user-facing material.
- Localized files use the sibling suffix `.ru.md`.
- Localized documents carry machine-readable translation metadata.
- Localized files are excluded from canonical artifact discovery and do not receive duplicate artifact IDs.
- Canonical and localized changes travel in the same pull request, or the translation is explicitly marked stale.
- A Russian translation becomes `synchronized` only after human review.
- Public Russian-language releases require full synchronized coverage.

The detailed contract is defined by `AXP-FND-LANGUAGE`.

## Alternatives considered

### English only

Rejected because it conflicts with AXIOPRA's beginner-access mission and the practical needs of its founding domain work.

### Russian as the only canon

Rejected for the platform layer because it would raise the adoption and contribution barrier for an international ecosystem and many current engineering tools.

### Two equal canonical languages

Rejected because independently editable normative texts inevitably drift. Determining which version governs a conflict would require a third authority.

### Automatic translation at view time

Rejected as the sole model because results would be vendor-dependent, non-reproducible, difficult to review, and unable to support stable links or release evidence.

### Separate translation repository

Deferred. It may become useful at community scale, but would add synchronization and contribution complexity before the core model is stable.

## Consequences

### Positive

- Russian users receive a complete guided path.
- One canonical semantic graph remains authoritative.
- Drift becomes visible and eventually machine-checkable.
- Any LLM vendor may assist without owning the translation state.
- Translation itself becomes a semantic review mechanism: unclear source text must be corrected upstream.

### Costs

- Every user-facing change carries translation work.
- Release gates become stricter.
- Review capacity is required in both languages.
- CLI diagnostics and tutorials need localization architecture before public alpha.

### Risks

- Russian files may appear current while actually stale.
- Literal translation may distort obligation strength or technical meaning.
- Contributors may update only the language they understand.
- A model may falsely claim human-reviewed synchronization.

The metadata schema, same-change rule, stale status, human review requirement, and future verifier checks mitigate these risks.

## Compatibility

No existing canonical artifact ID changes. Existing Russian root and RoadCore documents remain valid. Canonical discovery is updated to exclude `.ru.md` translations, preventing false schema failures and duplicate nodes.

## Migration plan

1. Add translation schema, template, manifest configuration, and agent protocol.
2. Translate the core reading path: Foundation, metamodel, lifecycle, verification, research, governance, and roadmap.
3. Translate detailed verification and evidence contracts.
4. Add required RU files to every new specification PR from the start.
5. Implement localization checks in the Rust verifier.
6. Reach full `synchronized` coverage before the first Russian-language public alpha.

## Validation plan

- Review translation metadata against its JSON Schema.
- Confirm canonical discovery ignores `.ru.md` files.
- Verify every translation resolves to an existing source path and artifact ID.
- Perform human comparison of normative high-risk documents.
- Run a beginner navigation exercise using only Russian entry points.
- Add positive and negative localization fixtures to the verifier suite.

## Falsification criteria

Revisit this decision if the sibling-file model produces unmanageable drift, materially harms contributor flow, or prevents reliable tooling. Alternative packaging may be proposed through a later RFC, but one semantic authority remains a constitutional requirement unless the Constitution itself is amended.
