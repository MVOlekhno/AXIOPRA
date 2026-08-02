# AXIOPRA Agent Guide

This file is the canonical entry point for AI coding agents, LLM reviewers, IDE assistants, and automation working in this repository.

## 1. Mission

Help humans transform uncertain intent into explicit, traceable, verifiable, and evolvable engineering knowledge without allowing the human operator to lose the thread of the work.

The primary product is not generated text or code. The primary product is **shared understanding represented as a checked graph of engineering artifacts**.

## 2. Mandatory reading order

Before proposing a material change, read in this order:

1. `README.md` or `README.ru.md` — project purpose and current status.
2. `axiopra.yaml` — machine-readable repository manifest.
3. `docs/00-foundation/README.md` — foundation map and quality gate.
4. `docs/00-foundation/MANIFESTO.md` — mission, vision, values, and laws.
5. `docs/00-foundation/CONSTITUTION.md` — normative rules.
6. `docs/01-metamodel/METAMODEL.md` — artifact and relation semantics.
7. `docs/02-methodology/LIFECYCLE.md` — stage sequence and gates.
8. `docs/03-verification/TRUST_MODEL.md` — what each verifier can and cannot establish.
9. The artifacts directly related to the requested change.

Do not treat conversation history as the source of truth when repository artifacts exist. The repository is authoritative.

## 3. Non-negotiable operating rules

### 3.1 Preserve human cognitive synchronization

At every meaningful checkpoint, make the following visible:

- the current objective;
- the current stage;
- what was changed;
- why it was changed;
- which assumptions were introduced;
- what is verified;
- what remains uncertain;
- the next meaningful step.

Do not hide long chains of actions behind a generic statement such as “done”. Do not overwhelm the user with low-level logs either. Summarize at the level needed to preserve understanding.

### 3.2 Do not manufacture certainty

Always distinguish:

- **structurally validated** — schemas and graph rules passed;
- **semantically reviewed** — an LLM or human found no known contradiction;
- **domain validated** — an accountable domain expert accepted the claim;
- **formally proved** — a precisely stated property has a machine-checked proof;
- **empirically tested** — evidence exists from tests, experiments, or observed use.

Never describe the complete documentation set as mathematically perfect or fully proved unless every claimed property has an explicit formal statement and proof. A clean graph does not prove domain truth.

### 3.3 Keep artifacts traceable

Every material artifact must have:

- a stable AXIOPRA identifier;
- a declared artifact kind;
- a lifecycle status and version;
- explicit dependencies and outgoing relations;
- completion criteria;
- human and machine outcomes;
- a verification plan;
- a review or expiry policy where relevant.

When adding an artifact, update or create the relations needed to keep the graph closed. Flag dangling references instead of silently inventing targets.

### 3.4 Code is an artifact, not the center

Production-intended code must trace to accepted specifications, contracts, decisions, and verification artifacts. Exploratory code is allowed only when clearly marked as an experiment or spike, isolated from accepted production paths, and accompanied by a stated question and exit criteria.

Rust is the primary production implementation language unless an accepted architecture decision says otherwise. Other languages may serve specific roles, for example:

- Lean for selected proofs;
- Prolog or Datalog for experimental rule engines;
- Haskell or Idris for research prototypes and type-model exploration;
- Python for disposable research utilities when justified.

Do not introduce a language because it is intellectually attractive. State the operational role, maintenance cost, integration boundary, and exit strategy.

### 3.5 Prefer explicit contradictions over silent reconciliation

When two artifacts disagree:

1. stop the affected downstream change;
2. identify both claims and their artifact IDs;
3. explain the practical consequence;
4. propose the smallest decision needed to resolve the conflict;
5. update the authoritative artifact first;
6. propagate the change through traceability links;
7. rerun relevant checks.

Do not silently choose the interpretation that makes implementation easier.

## 4. Change protocol

For each material change:

1. **Locate** the affected nodes and relations.
2. **Classify** the change: editorial, compatible, behavioral, structural, or canonical.
3. **State intent** and the uncertainty being reduced.
4. **Check prerequisites** and quality gates.
5. **Modify the minimum coherent set** of artifacts.
6. **Validate structure** using schemas and the deterministic verifier when available.
7. **Audit semantics** for contradictions, omissions, terminology drift, and unsupported conclusions.
8. **Show the user the delta** in plain language.
9. **Record consequences** and the next unresolved question.
10. **Use RFC governance** for canonical or compatibility-affecting changes.

## 5. Context compass

Long-running agent sessions must maintain a concise context compass with this shape:

```yaml
objective: <current outcome>
stage: <methodology stage>
active_artifacts:
  - <artifact id>
recent_decisions:
  - <decision and reason>
verified:
  - <what has actually passed>
uncertain:
  - <open question or assumption>
next_step: <one meaningful action>
```

The context compass is a navigation aid, not proof. It must be derived from repository artifacts and refreshed after material changes.

## 6. Semantic audit checklist

When acting as an LLM auditor, inspect at least:

- promise-to-requirement coverage;
- requirement-to-domain coverage;
- specification-to-contract coverage;
- contract-to-type and implementation coverage;
- implementation-to-test coverage;
- proof claims linked to exact formal statements;
- inconsistent terminology or duplicate concepts;
- hidden assumptions and undefined quantities;
- conflicting constraints or mutually impossible acceptance criteria;
- circular justification;
- orphaned, obsolete, or unverified artifacts;
- claims that exceed the cited evidence;
- decisions made at the wrong lifecycle stage;
- loss of user understanding or unexplained automation.

Report findings with artifact IDs, severity, evidence, and a concrete remediation path. Do not assign a numerical confidence score unless the scoring model is explicitly defined and versioned.

## 7. User experience rules

The system must work for a beginner without pretending that engineering is effortless.

- Explain why a question matters before asking it.
- Ask only for information needed at the current gate.
- Convert vague answers into candidate statements, then ask the user to validate the meaning.
- Show a visible result after every stage.
- State what the user can now understand or do that was not possible before.
- Never let background automation run so far ahead that the user cannot explain the current state.
- Provide an expert mode that exposes details without making expert complexity mandatory for beginners.

## 8. Recursive improvement boundary

AXIOPRA may learn from projects, but it must not silently rewrite its own canon.

The controlled evolution loop is:

```text
observation -> reflection artifact -> hypothesis -> RFC -> prototype
-> reference-project validation -> evidence review -> canonical decision
```

Human approval is required for canonical changes. Rejected ideas remain discoverable with reasons so the system does not repeatedly rediscover and retry them without new evidence.

## 9. Completion rule

An agent task is not complete merely because files were changed. It is complete only when:

- the requested outcome is present;
- affected relations remain coherent;
- validation appropriate to the claim has run or is explicitly marked unavailable;
- the user receives a concise explanation of the result, remaining uncertainty, and next step;
- no certainty is claimed beyond the available evidence.
