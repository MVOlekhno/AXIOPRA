---
axiopra:
  schema_version: "0.1.0"
  id: axp.foundation.manifesto
  kind: principle-set
  title: AXIOPRA Manifesto
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.foundation.index
  relations:
    - type: constrains
      target: axp.foundation.constitution
    - type: motivates
      target: axp.metamodel.core
    - type: motivates
      target: axp.methodology.lifecycle
  human_outcome: The reader can state the mission, vision, values, and core laws of AXIOPRA.
  machine_outcome: Downstream rules can trace to explicit canonical principles.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# AXIOPRA Manifesto

## Mission

Enable any person — from a first-time builder to an experienced engineer — to transform an uncertain idea into a coherent, traceable, testable, and responsibly verified engineering system while preserving their understanding and agency throughout the process.

## Vision

Engineering work should be navigable as a living graph of knowledge. Humans and machines should be able to see where each important statement came from, what it affects, how it is checked, what remains uncertain, and how experience may improve the system without erasing its history.

## Core thesis

> We do not automate thought away. We make engineering thought explicit, composable, inspectable, and verifiable.

Code is not the starting point and not the sole source of truth. Code is one artifact in the lifecycle of engineering knowledge.

## Values

### 1. Understanding before acceleration

Speed without a maintained mental model creates hidden risk. AXIOPRA should accelerate work only while keeping the user cognitively synchronized with it.

### 2. Explicit knowledge before implicit convention

Important intent, assumptions, rules, decisions, and evidence must not live only in a person's memory, a chat transcript, or undocumented code behavior.

### 3. Traceability before confidence theatre

Confidence must be supported by visible links between promises, models, specifications, contracts, implementations, tests, and proofs. Polished output is not evidence.

### 4. Independent checks before a single oracle

No human, LLM, compiler, test suite, theorem prover, or static analyzer can establish every kind of correctness. Trust grows through independent and appropriately scoped checks.

### 5. Practical rigor before maximal ceremony

The level of formality must match risk and consequence. Low-risk experiments may remain lightweight. Safety-critical claims demand stronger evidence. Traceability and honesty are never optional.

### 6. Evolution before dogma

The Foundation is stable enough to guide implementation, but no principle is protected from evidence. Canon changes through an explicit, reviewable path rather than silent drift.

### 7. Human agency before opaque autonomy

AI agents may propose, analyze, generate, and verify within declared limits. They must not silently redefine intent, hide unresolved contradictions, or rewrite canon without accountable human approval.

## Laws of the platform

### Law 1 — Every complex system begins with understanding

A vague idea is a legitimate starting point. The first engineering act is to reduce uncertainty about the user, problem, value, constraints, and desired outcome — not to generate production code.

### Law 2 — A project is a graph of engineering artifacts

Every material engineering artifact is a node with a stable identity. Every material dependency or transformation is a typed relation. A folder hierarchy is only one view of this graph.

### Law 3 — Every artifact has a human layer and a machine layer

The narrative layer explains meaning and context. The semantic layer exposes identity, type, relations, lifecycle state, constraints, and validation rules. Neither layer is sufficient alone.

### Law 4 — Every stage produces an external and an internal result

The external result is an inspectable artifact. The internal result is a clearer mental model the user can explain. A stage that creates files but reduces understanding has failed.

### Law 5 — Every stage must reduce named uncertainty

Progress is not the amount of generated content. Progress is a defensible reduction in uncertainty, accompanied by new capabilities, decisions, or evidence.

### Law 6 — Every material claim declares its evidence class

Claims must be distinguishable as hypothesis, expert judgment, empirical observation, domain validation, structural validation, semantic review, test result, or formal proof.

### Law 7 — Verification claims may not exceed verifier scope

A valid schema proves conformity to a schema. A closed graph proves selected graph properties. Tests establish observed behavior under stated cases. A formal proof establishes only the formalized proposition under its assumptions. An LLM review is probabilistic critique, not proof.

### Law 8 — Contradictions are first-class engineering findings

A contradiction must be surfaced with affected artifacts and consequences. It must not be silently reconciled by an agent merely to continue implementation.

### Law 9 — Exploratory work is allowed but must be labeled

Spikes, prototypes, and speculative models are useful. They must declare the question being explored, isolation boundary, assumptions, expiry condition, and path either to acceptance or deletion.

### Law 10 — The human must never lose the process

At any meaningful checkpoint the system must show the objective, current stage, changed artifacts, decisions, verified facts, uncertainties, and next step. Long-running automation without a context compass is a design defect.

### Law 11 — Improvement is recursive but governed

Project experience may generate reflection, hypotheses, RFCs, prototypes, and evidence. Canon changes only after explicit review. The platform must be able to improve itself without being allowed to rewrite itself impulsively.

### Law 12 — The stable core must support open extension

Canonical semantics, identifiers, versioning, and compatibility rules must remain stable enough for tools and communities to build upon them. Specialized domains, rule engines, agents, visualizations, and proof systems belong in replaceable layers.

## What success looks like

AXIOPRA succeeds when an unfamiliar person can begin with a sentence such as “I want to create a small graphical editor” and, without pretending to already be an engineer, can:

- understand the purpose of each stage;
- see a useful result at each stage;
- build an accurate mental model of the product;
- distinguish decisions from assumptions;
- trace important promises to implementation and evidence;
- work with AI agents without losing control of the process;
- produce a repository that another human or agent can inspect and continue;
- scale the same principles to more demanding systems with proportionate rigor.

## What AXIOPRA is not

AXIOPRA is not a guarantee that an inexperienced user can create any safe or correct system without expert input. It is not a substitute for engineering responsibility, regulation, domain competence, security review, usability research, or professional judgment.

AXIOPRA's promise is more disciplined and more realistic: it makes uncertainty, reasoning, dependencies, verification, and missing expertise visible early enough to act on them.
