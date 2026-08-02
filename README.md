# AXIOPRA

**From intent to a verified system.**

AXIOPRA is an open operating system for engineering thought: a human- and machine-readable framework that helps people and AI agents transform vague ideas into traceable, verifiable, and evolvable engineering systems.

> Complex systems should begin with understanding, not code.

[Русская версия](README.ru.md)

## Status

**Pre-alpha · Foundation phase**

The conceptual Phase 0 is complete and frozen as the initial hypothesis. Phase 1 is turning that foundation into explicit, versioned, machine-checkable artifacts. AXIOPRA is not production-ready yet.

## The problem

A person may know what they want to build and still have no reliable way to move from an idea to a coherent product. AI coding agents can produce large amounts of work, but the human operator can lose the thread: what is being built, why decisions were made, which requirements remain uncovered, and whether the resulting documents and code still agree.

AXIOPRA addresses that gap by keeping four things synchronized:

1. **Human understanding** — the user can see the current goal, state, decisions, uncertainties, and next step.
2. **Engineering knowledge** — every important claim, requirement, decision, contract, test, and proof is an explicit artifact.
3. **Machine verification** — artifacts have stable identifiers, typed relations, schemas, and rules that a deterministic verifier can check.
4. **Implementation** — code is produced only after intent, domain, specification, contracts, types, and verification paths are sufficiently clear.

## Core model

AXIOPRA treats a project as a **directed graph of engineering artifacts**, not as a folder of unrelated documents.

Each artifact has:

- a stable identifier and type;
- a purpose and owner;
- explicit inputs, outputs, and dependencies;
- claims, assumptions, constraints, and evidence;
- completion criteria and verification rules;
- lifecycle state, version, and review history;
- a human-readable narrative layer;
- a machine-readable semantic layer.

Nouns become graph nodes. Verbs become typed relations. Qualities become metadata. Constraints become executable validation rules.

## Default engineering lifecycle

AXIOPRA combines established schools of engineering rather than pretending that one technique solves every problem:

1. **Working Backwards** — clarify the user, problem, value, and expected outcome through a press release and FAQ.
2. **Domain-Driven Design** — establish a shared language, domain boundaries, entities, value objects, rules, and events.
3. **Specification-Driven Development** — state observable behavior, constraints, examples, and acceptance criteria.
4. **Contract-Driven Development** — define preconditions, postconditions, invariants, responsibilities, and failure modes.
5. **Type-Driven Development** — make invalid states difficult or impossible to represent, with Rust as the primary production language.
6. **Test-Driven Development** — verify examples, properties, boundaries, integrations, and regressions.
7. **Proof-Driven Development** — selectively prove critical properties with tools such as Lean when the cost of error justifies it.
8. **Reflection and evolution** — feed verified project experience back into the methodology through evidence, RFCs, reference projects, and controlled canon changes.

## Trust model

AXIOPRA uses independent verification layers:

- **Deterministic verifier in Rust** for schemas, identifiers, graph integrity, required fields, lifecycle rules, and traceability.
- **LLM semantic auditor** for ambiguity, omissions, contradictions, unsupported reasoning, terminology drift, and cross-document coherence.
- **Formal verification** for selected algorithms and invariants where mathematical assurance is valuable.
- **Human review** for intent, ethics, domain truth, trade-offs, and accountability.

No single layer is treated as an oracle. Confidence comes from agreement between independent checks.

## Human-centered rule

Every stage must produce two outcomes:

- an **external result**: a visible, inspectable engineering artifact;
- an **internal result**: a clearer mental model that the user can explain in their own words.

A stage has failed if it produces files while leaving the user less able to explain the project. AXIOPRA must continuously show:

- the current objective;
- where the user is in the process;
- what changed;
- why it changed;
- what is verified and what remains uncertain;
- the next meaningful step.

## Repository architecture

```text
AXIOPRA/
├── README.md
├── README.ru.md
├── AGENTS.md
├── axiopra.yaml
├── docs/
│   ├── 00-foundation/       # manifesto, constitution, axioms, governance
│   ├── 01-metamodel/        # artifact and relation semantics
│   ├── 02-methodology/      # lifecycle stages and quality gates
│   ├── 03-verification/     # deterministic, semantic, and formal checks
│   ├── 04-research/         # evidence, industry cases, sources, critiques
│   ├── 05-reference/        # reference projects and worked examples
│   └── 06-roadmap/          # delivery plan and maturity model
├── schemas/                 # machine-readable schemas
├── templates/               # self-explaining artifact templates
├── crates/                  # future Rust verifier, CLI, SDK, and libraries
├── proofs/                  # future formal models and proofs
└── examples/                # minimal and domain-specific examples
```

This structure is an initial architecture, not an immutable taxonomy. Changes to the canonical model must follow the project RFC process.

## Near-term roadmap

The first usable vertical slice will:

1. define the minimal artifact and relation metamodel;
2. provide self-explaining templates;
3. validate a project manifest and artifact metadata deterministically;
4. build and visualize the artifact graph;
5. detect missing, dangling, cyclic, contradictory, and unverified traceability paths;
6. guide a beginner through one small reference project;
7. expose the same model to humans, CLI tools, SDKs, and AI agents.

The first domain reference project will be an engineering module for validating road longitudinal-profile drainage, implemented in Rust and selectively verified with Lean.

## Intellectual roots

AXIOPRA draws from, among other sources:

- *Structure and Interpretation of Computer Programs* — abstraction, composition, interpretation, and metalinguistic thinking;
- lambda calculus, functional programming, and type theory;
- Haskell and Idris as schools of functional and type-driven design;
- Eiffel and Design by Contract;
- Rust for practical type safety, ownership, reliability, and deployable systems;
- Lean and formal methods for selective proof;
- Domain-Driven Design, specification by example, TDD, property testing, and architecture decision records;
- knowledge graphs, logic programming, category-theoretic composition, compilers, intermediate representations, and reproducible research.

These are sources of ideas, not authorities beyond criticism. AXIOPRA must distinguish established evidence, informed judgment, and active hypotheses.

## Non-goals

AXIOPRA is not:

- a promise that all engineering truth can be proved automatically;
- a replacement for domain experts or accountable human decisions;
- a wrapper around one LLM vendor;
- a code generator that hides reasoning from its user;
- a universal process that forces maximum ceremony on every project.

The level of rigor must be proportional to risk, while traceability and intellectual honesty remain mandatory.

## License and contribution policy

Licensing, governance, contribution rules, compatibility guarantees, and the RFC process will be defined during the Foundation phase before the first public release.
