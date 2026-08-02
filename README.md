# AXIOPRA

**From intent to a verified system.**

AXIOPRA is an open operating system for engineering thought: a human- and machine-readable framework that helps people and AI agents transform vague ideas into traceable, verifiable, and evolvable engineering systems.

> Complex systems should begin with understanding, not code.

[Русская версия](README.ru.md)

## Status

**Pre-alpha · Foundation v0.1**

The conceptual Phase 0 is complete and frozen as the initial hypothesis. Phase 1 turns that foundation into explicit, versioned, machine-checkable artifacts. AXIOPRA is not production-ready yet.

## The problem

A person may know what they want to build and still have no reliable way to move from an idea to a coherent product. AI coding agents can produce large amounts of work, but the human operator can lose the thread: what is being built, why decisions were made, which requirements remain uncovered, and whether documents and code still agree.

AXIOPRA keeps four things synchronized:

1. **Human understanding** — the user can see the current goal, state, decisions, uncertainties, and next step.
2. **Engineering knowledge** — every important claim, requirement, decision, contract, test, and proof is an explicit artifact.
3. **Machine verification** — artifacts have stable identifiers, typed relations, schemas, and deterministic rules.
4. **Implementation** — code follows sufficiently clear intent, domain, specification, contracts, types, and verification paths.

## Core model

AXIOPRA treats a project as a **directed graph of engineering artifacts**, not as a folder of unrelated documents.

Each artifact has a stable identity, purpose, lifecycle, machine-readable metadata, human-readable explanation, explicit relations, completion criteria, and verification rules.

**Nouns become nodes. Verbs become typed relations. Qualities become metadata. Constraints become executable rules.**

## Start here

- Human entry point: this README and [`docs/00-foundation/README.md`](docs/00-foundation/README.md)
- Russian entry point: [`README.ru.md`](README.ru.md)
- AI-agent contract: [`AGENTS.md`](AGENTS.md)
- Machine project manifest: [`axiopra.yaml`](axiopra.yaml)
- Artifact metamodel: [`docs/01-metamodel/artifact-model.md`](docs/01-metamodel/artifact-model.md)
- Methodology lifecycle: [`docs/02-methodology/stages.md`](docs/02-methodology/stages.md)
- Verification model: [`docs/03-verification/README.md`](docs/03-verification/README.md)
- First reference project: [`RoadCore Drainage Validator`](docs/05-reference/roadcore-drainage-validator/README.md)

## Default engineering lifecycle

AXIOPRA combines complementary schools instead of pretending one technique solves every problem:

1. Working Backwards.
2. Domain-Driven Design.
3. Specification-Driven Development.
4. Contract-Driven Development.
5. Type-Driven Development.
6. Architecture through abstraction, composition, and interpretation.
7. Rust implementation.
8. Test-Driven and property-based verification.
9. LLM semantic audit.
10. Selective Proof-Driven Development with Lean.
11. Release, observation, reflection, and controlled evolution through RFCs.

The stages provide traceability and quality gates; they are not a rigid waterfall. Feedback is expected, but every backward step must be explicit and recorded.

## Trust model

AXIOPRA uses independent layers:

- **Deterministic verifier in Rust** for schemas, identifiers, graph integrity, lifecycle rules, and traceability.
- **LLM semantic auditor** for ambiguity, omissions, contradictions, unsupported reasoning, and terminology drift.
- **Formal verification** for selected critical properties.
- **Human review** for intent, ethics, domain truth, trade-offs, and accountability.

No single layer is an oracle. Confidence comes from agreement between independent checks.

## Human-centered rule

Every stage must produce two outcomes:

- an **external result**: a visible, inspectable artifact;
- an **internal result**: a clearer mental model the user can explain.

A stage fails if it creates files while making the user less able to explain the project. AXIOPRA must continuously show the objective, current stage, changes, reasons, verified facts, uncertainties, and next meaningful step.

## Repository architecture

```text
AXIOPRA/
├── README.md
├── README.ru.md
├── AGENTS.md
├── LLM_GUIDE.md
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
├── crates/        # future Rust implementation
├── proofs/        # future Lean proofs
└── examples/      # future starter projects
```

## Intellectual roots

AXIOPRA draws from SICP; lambda calculus; functional programming and type theory; Haskell and Idris; Eiffel and Design by Contract; Rust; Lean and formal methods; DDD; specification by example; TDD and property testing; knowledge graphs; logic programming; category-theoretic composition; compilers and intermediate representations; and reproducible research.

These are sources of ideas, not authorities beyond criticism. AXIOPRA distinguishes established evidence, informed judgment, and active hypotheses.

## Non-goals

AXIOPRA is not a claim that all engineering truth can be proved automatically, a replacement for domain experts, a wrapper around one AI vendor, or a code generator that hides reasoning. Rigor is proportional to risk; traceability and intellectual honesty are mandatory.

## License

No open-source license has been selected yet. Until a license is added, normal copyright restrictions apply. Selecting the license is an explicit Foundation milestone.
