---
axiopra:
  id: AXP-RDM-001
  kind: roadmap.platform
  version: 0.1.0
  status: active
  stage: AXP-STAGE-10
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Delivery sequence from Foundation to a scalable AXIOPRA ecosystem.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-MM-ARTIFACT, AXP-MM-RELATION, AXP-MTH-STAGES, AXP-VER-MODEL]
    produces: [AXP-REF-ROADCORE]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-005, AXP-SEM-006, AXP-SEM-008]
  learning:
    external: A bounded delivery plan that prevents premature SDK and ecosystem work.
    internal: The reader can explain why the metamodel and verifier precede plugins and scale.
---

# Roadmap

## Phase 0 — Conceptual foundation

**State:** complete as an initial hypothesis.

Outcome: mission, philosophical direction, knowledge-graph model, human-centered laws, verification layers, controlled recursive evolution, and Rust as the primary production language.

## Phase 1 — Canonical Foundation v0.1

**State:** in progress.

Deliverables: manifesto, constitution, agent contract, project manifest, metamodel, lifecycle, verification rules, research policy, templates, RFC process, and license decision.

Gate: artifacts are mutually consistent and can be parsed by the first verifier prototype.

## Phase 2 — Engineering IR and Rust verifier MVP

Deliverables: Rust workspace, Markdown/YAML parser, JSON Schema validation, artifact registry, typed graph, core structural rules, text and JSON reports, and generated Mermaid graph.

Gate: the verifier correctly accepts a valid minimal project and rejects curated invalid fixtures.

## Phase 3 — RoadCore vertical slice

Deliverables: Working Backwards artifacts, DDD model, specification, contracts, type model, architecture, Rust implementation, tests, semantic audit, and one selective Lean proof.

Gate: traceability is traversable from user promise to executable evidence and back.

## Phase 4 — Beginner experience

Deliverables: guided project initializer, stage navigator, context compass, visible progress map, uncertainty register, explanatory feedback, and a simple graphic-editor starter example.

Gate: an unfamiliar non-programmer completes a small documented product concept without author assistance and can explain each stage.

## Phase 5 — SDK and agent adapters

Deliverables: stable Rust SDK, JSON protocol, plugin API, ChatGPT/Codex guidance, Claude Code integration, CI action, editor integration, and vendor-neutral context packages.

Gate: independent clients consume the same Engineering IR without duplicating canonical knowledge.

## Phase 6 — Logic and proof extensions

Deliverables: rule-engine plugin experiment, possible SWI-Prolog adapter, Lean export and proof packages, and research into category-theoretic composition laws.

Gate: each extension demonstrates a real failure mode it catches better than the deterministic Rust core and does not become mandatory complexity without evidence.

## Phase 7 — Community scale

Deliverables: governance, compatibility policy, migrations, localization, signed releases, security model, telemetry policy, public examples, evidence dossiers, contributor education, and sustainability model.

Gate: a large user population can adopt, update, and extend AXIOPRA without depending on its original authors.

## Current next step

Complete Foundation v0.1, choose a license, then specify the minimum Rust verifier before writing its implementation.
