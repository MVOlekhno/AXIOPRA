---
axiopra:
  id: AXP-REF-ROADCORE
  kind: reference.project
  version: 0.1.0
  status: hypothesis
  stage: AXP-STAGE-00
  language: en
  confidence: unverified
  owners: [MVOlekhno]
  summary: Reference project for validating road longitudinal-profile drainage.
  relations:
    depends_on: [AXP-MTH-STAGES, AXP-VER-MODEL]
    verifies: [AXP-MTH-STAGES]
    produces: [RCD-INTENT-001, RCD-FAQ-001]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-001, AXP-SEM-006, AXP-SEM-008]
  learning:
    external: A real engineering vertical slice that exercises the full methodology.
    internal: The user can see how abstract platform rules become a practical civil-engineering product.
---

# RoadCore Drainage Validator

## Purpose

This is AXIOPRA's first reference project: a small but real engineering module that checks whether a road longitudinal profile and its drainage elements form a coherent gravity-flow system.

The project is close to industrial road and site-development practice while remaining small enough to model, implement, test, and selectively prove end to end.

## Initial user

A road or site-development engineer reviewing a longitudinal profile, surface drainage direction, channels, trays, culverts, and outlets before issuing design documentation.

## Initial problem

Geometry may be drawn correctly while drainage logic remains partially manual. Typical risks include reverse grades, local depressions, disconnected elements, invalid outlet levels, contradictory flow directions, and drainage paths that do not reach an approved outlet.

## First product promise

Given a simplified longitudinal profile and drainage network, the module will identify traceable drainage defects, explain which rule was violated, and show the affected path and recommended review location.

## Deliberate scope of the first vertical slice

- one road alignment represented by ordered stations and elevations;
- longitudinal grade segments;
- drainage nodes and directed connections;
- approved outlets;
- configurable minimum grade and tolerance;
- deterministic validation report;
- no CAD integration, surface triangulation, hydraulic capacity calculation, or automatic design in the first slice.

## Candidate critical proposition

Under explicitly stated assumptions, every valid drainage node has a directed path to an approved outlet and the directed flow graph contains no cycle.

This proposition is only a candidate. It must be refined into a domain contract, tested against engineering reality, and proven only after the abstraction boundary is accepted.

## Technology direction

- production implementation: Rust;
- pure domain core separated from import/export and UI;
- contracts encoded through domain types, constructors, invariants, and `Result`;
- example, boundary, property, and integration tests;
- Lean for one narrowly defined graph or grade property;
- LLM audit for cross-document coherence, never as the only verifier.

## Current Working Backwards artifacts

- [`01-working-backwards/press-release.md`](01-working-backwards/press-release.md)
- [`01-working-backwards/faq.md`](01-working-backwards/faq.md)

No implementation should begin before the Working Backwards gate passes.
