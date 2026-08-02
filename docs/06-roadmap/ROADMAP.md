---
axiopra:
  schema_version: "0.1.0"
  id: axp.roadmap.platform
  kind: roadmap
  title: AXIOPRA Platform Roadmap
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.foundation.governance
    - axp.metamodel.core
    - axp.methodology.lifecycle
    - axp.verification.trust-model
  relations:
    - type: organizes
      target: axp.verifier.rust-core
    - type: organizes
      target: axp.reference.roadcore-drainage-validator
  human_outcome: The reader can see the order in which the platform becomes usable without confusing long-term vision with current capability.
  machine_outcome: Planned deliverables and phase gates can be represented as traceable work artifacts.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# AXIOPRA Platform Roadmap

## 1. Delivery principle

Build one thin, end-to-end, usable path before expanding the platform horizontally.

The order is:

```text
foundation -> metamodel -> deterministic verifier -> guided workflow
-> reference project -> SDK and agent adapters -> logic and proofs
-> compiler ecosystem and scale
```

Do not build plugins, a rule language, a theorem library, or a marketplace before the shared artifact model works in one real project.

## 2. Repository strategy

AXIOPRA begins as a monorepository so semantics, schemas, verifier, templates, examples, and adapters evolve together.

Planned top-level structure:

```text
AXIOPRA/
├── AGENTS.md
├── axiopra.yaml
├── docs/
│   ├── 00-foundation/
│   ├── 01-metamodel/
│   ├── 02-methodology/
│   ├── 03-verification/
│   ├── 04-research/
│   ├── 05-reference/
│   └── 06-roadmap/
├── schemas/
├── templates/
├── rfcs/
├── crates/
│   ├── axiopra-model/
│   ├── axiopra-parser/
│   ├── axiopra-graph/
│   ├── axiopra-rules/
│   ├── axiopra-diagnostics/
│   ├── axiopra-verifier/
│   ├── axiopra-cli/
│   └── axiopra-sdk/
├── adapters/
│   ├── chatgpt/
│   ├── claude-code/
│   ├── codex/
│   └── protocol/
├── proofs/
│   ├── metamodel/
│   └── roadcore/
├── examples/
│   ├── minimal-graphics-editor/
│   └── roadcore-drainage-validator/
└── tools/
```

Components split into separate repositories only when independent release cadence, permissions, security boundaries, or ecosystem ownership justify the cost.

## 3. Phase 1 — Foundation bootstrap

**Goal:** turn the Phase 0 conversation into a small canonical artifact graph.

Deliverables:

- project README in English and Russian;
- machine-readable repository manifest;
- agent guide;
- manifesto, Constitution, and governance;
- minimal metamodel;
- complete methodology lifecycle;
- trust model;
- artifact metadata schema;
- self-explaining generic template;
- research evidence policy;
- roadmap;
- initial graph inventory and validation test data.

Exit gate:

- every canonical document has valid metadata;
- every declared internal relation resolves;
- terminology is consistent;
- contradictions and open questions are listed;
- one human review is recorded;
- Foundation Baseline Revision 1 is frozen for verifier implementation.

Current state: **in progress**.

## 4. Phase 2 — Rust verifier MVP

**Goal:** prove that AXIOPRA documentation can be parsed and checked deterministically.

Crates:

- `axiopra-model` — typed IR and registries;
- `axiopra-parser` — Markdown/YAML frontmatter discovery and source spans;
- `axiopra-graph` — typed multigraph and traversal;
- `axiopra-diagnostics` — stable diagnostic model;
- `axiopra-rules` — versioned core invariant rules;
- `axiopra-verifier` — orchestration library;
- `axiopra-cli` — user-facing commands.

Initial CLI:

```text
axiopra init
axiopra scan
axiopra validate
axiopra graph
axiopra status
axiopra explain <diagnostic-id>
```

MVP checks:

- parse and schema validity;
- duplicate IDs;
- unresolved targets;
- unknown kinds and relation types;
- illegal lifecycle states and transitions;
- forbidden dependency cycles;
- canonical role conflicts;
- basic traceability paths;
- metadata/narrative presence;
- exact human-readable diagnostics and JSON output.

Exit gate:

- the verifier validates its own repository;
- intentional invalid fixtures produce expected diagnostics;
- output is deterministic across supported platforms;
- no LLM is required for core validation;
- diagnostics link to governing rules and source locations.

## 5. Phase 3 — Guided authoring and context compass

**Goal:** make the methodology usable by a person who has never designed software professionally.

Deliverables:

- `axiopra init` interactive project creation;
- stage-specific templates;
- beginner, build, assurance, and research profiles;
- question-by-question guided workflow;
- uncertainty ledger;
- context compass;
- visible “what you now have / understand / can do” checkpoint;
- graph visualization;
- impact view and unresolved-path view;
- safe artifact generation without silent acceptance.

Likely interfaces:

- CLI first;
- terminal UI or local web UI after the workflow stabilizes;
- machine-readable API shared by every interface.

Exit gate:

- a first-time user can start from one sentence and complete a minimal Working Backwards stage;
- the user can explain the produced artifacts in a usability review;
- the system never implies checks that were not run;
- sessions can resume from repository state without relying on chat memory.

## 6. Phase 4 — Reference projects

### 4.1 Minimal graphics editor

Purpose:

- test beginner onboarding;
- demonstrate the whole documentation path on an understandable product;
- keep implementation scope small;
- expose where the methodology becomes unnecessary ceremony.

### 4.2 RoadCore Drainage Validator

Purpose:

- validate the methodology in a real engineering domain;
- model stations, elevations, gradients, low points, outlets, pipes, and channels;
- exercise units, tolerances, geometry, domain invariants, errors, Rust types, property tests, and a selected Lean proof;
- evaluate the workflow with a practicing civil engineer;
- produce reflection artifacts for methodology improvement.

Exit gate:

- both projects pass the selected conformance profiles;
- every critical promise has traceability to evidence or an explicit accepted gap;
- lessons remain scoped and enter governance rather than silently changing canon;
- the reference repositories can be understood by a new human and a new agent.

## 7. Phase 5 — SDK, protocol, and AI integrations

**Goal:** expose one stable model to tools and agents without vendor lock-in.

### SDK

Planned capabilities:

- load and validate a repository;
- query artifacts and graph paths;
- create typed artifacts;
- register extensions and rules;
- produce diagnostics and views;
- record verification results;
- maintain context compass state;
- calculate change impact;
- serialize Engineering IR.

### Open protocol layer

The protocol must expose:

- repository identity and specification versions;
- artifact retrieval by ID;
- graph queries;
- diagnostics;
- proposed change sets;
- verification records;
- human approval boundaries;
- capability negotiation;
- no dependence on one prompt format or model provider.

### Agent adapters

Planned adapters:

- ChatGPT-oriented workflow;
- Claude Code-oriented workflow;
- Codex-oriented workflow;
- generic local or hosted LLM workflow;
- future editor and CI integrations.

Adapters translate provider capabilities into the stable AXIOPRA protocol. They must not own canonical project meaning.

Exit gate:

- two independent agent environments can perform the same repository audit using the same artifact graph;
- results preserve provenance and model identity;
- provider replacement does not require rewriting project documents;
- permissions and write operations are explicit and auditable.

## 8. Phase 6 — Logic rules and formal verification

**Goal:** determine where declarative logic and proof deliver real value beyond native Rust checks.

Experiments:

- express selected graph policies in Datalog or Prolog-style rules;
- compare readability, diagnostics, performance, and maintenance with Rust-native rules;
- build explanation traces for inferred findings;
- formalize selected IR or graph-transformation properties in Lean;
- complete the first RoadCore algorithm proof;
- document model-to-implementation correspondence gaps.

Decision gate:

- adopt a logic engine only if evidence shows a clear advantage;
- keep rule semantics implementation-independent;
- accept formal proofs only for explicit, stable, high-value propositions;
- reject theoretical complexity that does not improve assurance or composition.

## 9. Phase 7 — Engineering knowledge compiler

**Goal:** evolve the verifier into a compiler for engineering knowledge.

Compiler stages:

```text
sources -> parser -> schema -> symbol resolution -> normalization
-> Engineering IR -> typed graph -> rule evaluation -> diagnostics
-> views, tests, code scaffolds, agent context, and proof obligations
```

Potential outputs:

- traceability matrices;
- diagrams and knowledge maps;
- test skeletons and property generators;
- contract and type-model scaffolds;
- change-impact reports;
- proof obligations;
- context packages for agents;
- migration plans;
- domain-specific DSL projections.

Generated code or proofs remain derived artifacts. Generation must preserve source links and never replace human acceptance of intent.

## 10. Phase 8 — Ecosystem and internet scale

**Goal:** support large adoption without losing semantic stability or user trust.

Deliverables:

- stable specification and conformance profiles;
- extension registry and compatibility policy;
- signed releases and supply-chain security;
- migration tooling;
- localization system;
- accessibility standards;
- public examples and training paths;
- contributor governance;
- privacy-preserving telemetry only with explicit consent;
- reproducible research and benchmark suite;
- long-term archival of schemas and identifiers.

Scale criteria:

- new users can begin without knowing the authors;
- maintainers can evolve the platform without breaking silent assumptions;
- older projects remain readable and migratable;
- agents from different vendors operate against the same semantics;
- every public assurance claim remains inspectable.

## 11. What is deliberately deferred

Until the Rust verifier and reference projects provide evidence, AXIOPRA defers:

- a custom programming language;
- a large graphical desktop application;
- a plugin marketplace;
- automatic canon self-modification;
- a universal trust score;
- broad theorem libraries;
- mandatory category-theoretic architecture;
- mandatory Prolog/Datalog infrastructure;
- generation of entire production systems from incomplete artifacts.

Deferral protects the core from speculative complexity. These ideas remain valid research directions, not current deliverables.

## 12. Immediate next milestone

Complete Phase 1 as a coherent pull request, review contradictions, then create the Rust workspace and implement only enough parser and diagnostics code to validate the repository's own artifact metadata.
