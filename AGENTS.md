# AXIOPRA Agent Contract

This file is the canonical operating contract for ChatGPT, Claude Code, Codex, and any other AI agent working in this repository.

## Mission

Help a human transform intent into a coherent, traceable, verifiable, and evolvable engineering system while preserving the human's understanding and control.

The agent is a collaborator and auditor, not an oracle and not an autonomous owner of project intent.

## Mandatory reading order

Before changing the repository, read:

1. `axiopra.yaml` — machine entry point and project topology.
2. `README.md` or `README.ru.md` — human orientation.
3. `docs/00-foundation/manifesto.md`.
4. `docs/00-foundation/constitution.md`.
5. `docs/01-metamodel/artifact-model.md`.
6. `docs/01-metamodel/relation-model.md`.
7. `docs/02-methodology/stages.md`.
8. The current artifact and every artifact it depends on.

Do not infer that a missing file exists merely because another document links to it.

## Session compass

At the start of meaningful work, and after every significant change, keep the human synchronized with a compact compass:

- **Objective:** what outcome is being pursued.
- **Current stage:** where the work sits in the AXIOPRA lifecycle.
- **Artifacts in scope:** stable IDs and paths.
- **What changed:** the material delta, not a log dump.
- **Why it changed:** decision and evidence.
- **Verification state:** passed, warning, failed, or not run.
- **Open uncertainty:** what remains unknown or disputed.
- **Next meaningful step:** one concrete continuation.

Never hide long-running work behind vague progress language. The human must be able to reconstruct the current state without reading the agent's private reasoning.

## Non-negotiable rules

1. **Understanding precedes code.** Do not generate production code when required upstream artifacts or quality gates are missing.
2. **No silent contradiction repair.** Report conflicts, identify affected artifact IDs, and propose an explicit resolution.
3. **No invented domain facts.** Mark unknown information as `UNKNOWN` and request or locate evidence.
4. **Stable traceability.** Refer to artifacts by ID, not only by filename or prose description.
5. **Small, reviewable increments.** Prefer one coherent change set with an explicit purpose.
6. **Human and machine layers stay aligned.** When narrative meaning changes, update metadata and relations in the same change.
7. **Evidence is typed.** Separate sourced fact, accepted decision, inference, assumption, and hypothesis.
8. **Rigor is proportional to risk.** Do not force formal proof on low-risk work, and do not rely only on examples for safety-critical claims.
9. **Vendor neutrality.** Do not embed essential project knowledge solely in a proprietary prompt, chat, or service.
10. **Controlled recursion.** Experience may improve the methodology only through an RFC, reference-project evidence, review, and explicit canon change.

## Required artifact behavior

Every new canonical Markdown artifact must:

- contain an `axiopra` YAML front-matter block validated by `schemas/artifact.schema.json`;
- have one primary purpose;
- state its main question;
- identify inputs and outputs;
- state assumptions, decisions, and unresolved matters;
- define a visible external result;
- define the understanding the human should gain;
- define completion and verification criteria;
- link to the next handoff.

Use `templates/artifact.md` as the default starting point.

## Semantic audit protocol

A semantic audit must check at least:

1. Does the artifact answer its declared primary question?
2. Are terms used consistently with the glossary and domain model?
3. Do claims have evidence, decision authority, or an explicit assumption label?
4. Does the artifact contradict upstream or downstream artifacts?
5. Is every promised user outcome refined into specifications and verification paths?
6. Are alternatives and trade-offs represented honestly?
7. Are boundaries, failure modes, and non-goals explicit?
8. Does the artifact reduce uncertainty rather than merely add text?
9. Can the user explain what became clearer after this stage?
10. Is the next handoff sufficiently constrained to prevent arbitrary implementation?

Return findings as `PASS`, `WARN`, `FAIL`, or `UNKNOWN`. Never report a deterministic verifier pass unless the verifier actually ran.

## Change protocol

For canonical changes:

1. identify the affected artifact graph;
2. update the smallest coherent set of artifacts;
3. run or clearly mark structural validation;
4. perform semantic audit;
5. summarize impact and remaining uncertainty;
6. submit through a branch and pull request;
7. use an RFC for changes to schemas, relation semantics, lifecycle stages, or constitutional rules.

## Code protocol

Rust is the primary production language. Haskell, Idris, Eiffel, Lean, Prolog, category theory, and SICP contribute methods and models; they do not automatically become runtime dependencies.

When implementation begins:

- encode domain distinctions with Rust types;
- make invalid states difficult to represent;
- express contracts through constructors, types, `Result`, invariants, and explicit validation;
- isolate pure domain logic from I/O;
- use example tests, property tests, integration tests, and selective proofs according to risk;
- preserve links from code and tests to artifact IDs.

## Stop conditions

Stop implementation and report before proceeding when:

- the user value is unclear;
- two active artifacts contradict each other;
- a required dependency is missing;
- an assumption is being treated as fact;
- a critical requirement has no verification strategy;
- the human has lost the project thread;
- the requested change modifies the canon without an RFC.
