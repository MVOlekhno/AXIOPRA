---
axiopra:
  id: AXP-MTH-STAGES
  kind: methodology.lifecycle
  version: 0.1.0
  status: active
  stage: AXP-STAGE-00
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: The default end-to-end lifecycle and quality gates for AXIOPRA projects.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-MM-ARTIFACT, AXP-MM-RELATION]
    produces: [AXP-REF-ROADCORE, AXP-VER-MODEL]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-006]
    semantic: [AXP-SEM-001, AXP-SEM-006, AXP-SEM-008]
  learning:
    external: A navigable sequence of stages with visible results and gates.
    internal: The reader can identify the current stage and explain why the next stage is justified.
---

# AXIOPRA Lifecycle

The lifecycle is a traceability spine, not a rigid waterfall. Iteration is normal. A backward move must identify the failed assumption, affected artifact IDs, and reason for reopening an earlier gate.

## Stage 00 — Intent and Working Backwards

**Question:** Who has which problem, why does it matter, and what observable value would a finished product create?

**Artifacts:** product intent, press release, FAQ, users, outcomes, non-goals, initial risk profile.

**Visible result:** a stranger can explain the product without mentioning implementation technology.

**Gate:** the user, problem, promised outcome, boundaries, and success evidence are explicit.

## Stage 01 — Domain discovery and DDD

**Question:** What language and rules describe the real problem domain?

**Artifacts:** glossary, bounded contexts, entities, value objects, domain services, events, invariants, context map.

**Visible result:** a domain map showing what exists and where each rule belongs.

**Gate:** important terms are unambiguous inside a context and domain experts can challenge the model.

## Stage 02 — Specification

**Question:** What observable behavior must the system exhibit, including boundaries and failures?

**Artifacts:** requirements, scenarios, examples, acceptance criteria, constraints, assumptions, out-of-scope cases.

**Visible result:** behaviour can be reviewed without reading code.

**Gate:** every promised outcome is refined into testable or otherwise verifiable statements.

## Stage 03 — Contracts

**Question:** What must be true before, during, and after each responsibility is performed?

**Artifacts:** preconditions, postconditions, invariants, ownership of failure, error taxonomy, service contracts.

**Visible result:** responsibility boundaries and invalid conditions are explicit.

**Gate:** no critical operation lacks defined obligations and failure behaviour.

## Stage 04 — Type-driven design

**Question:** Which invalid states can be removed from the representable state space?

**Artifacts:** domain types, value constructors, state machines, units of measure, identifiers, error types.

**Visible result:** a type model showing which guarantees move from prose or runtime checks into construction rules.

**Gate:** primitive obsession and ambiguous states are justified or removed.

## Stage 05 — Architecture and composition

**Question:** How are responsibilities abstracted, composed, interpreted, and isolated from effects?

**Artifacts:** system context, components, boundaries, data flow, pure core/effect shell, ADRs, extension points, Engineering IR decisions.

**Visible result:** a system diagram and decision set connecting domain meaning to deployable components.

**Gate:** architecture realizes contracts and types without introducing untraceable capability.

## Stage 06 — Rust implementation

**Question:** How is the approved model implemented safely and clearly for real users?

**Artifacts:** Rust crates, APIs, adapters, migrations, build configuration, code-level trace links.

**Visible result:** the smallest executable vertical slice.

**Gate:** code compiles, respects upstream contracts, exposes explicit errors, and contains no unexplained requirement drift.

## Stage 07 — Tests and properties

**Question:** What evidence shows that examples, boundaries, integrations, and general properties hold?

**Artifacts:** unit tests, scenario tests, property tests, integration tests, regression tests, test data and coverage map.

**Visible result:** executable evidence connected to specifications and contracts.

**Gate:** critical requirements have appropriate positive, negative, boundary, and property-level evidence or explicit waiver.

## Stage 08 — Semantic audit

**Question:** Does the whole artifact graph still tell one coherent and honest story?

**Artifacts:** LLM audit report, contradiction list, terminology drift report, orphan analysis, uncertainty register.

**Visible result:** a human-readable coherence report with findings classified as PASS, WARN, FAIL, or UNKNOWN.

**Gate:** blocking contradictions and unsupported critical claims are resolved.

## Stage 09 — Selective formal proof

**Question:** Which high-value propositions justify mathematical proof, and under which assumptions?

**Artifacts:** formal proposition, Lean model, proof, assumptions, correspondence argument between model and implementation.

**Visible result:** a machine-checked proof report for a narrowly stated property.

**Gate:** proof scope and limitations are not overstated; implementation correspondence is reviewed.

## Stage 10 — Release, observation, and evolution

**Question:** Does the system deliver the promised value in its real environment, and what did the project teach us?

**Artifacts:** release record, operational evidence, user feedback, incidents, lessons, proposed RFCs, maturity update.

**Visible result:** value and risk are observable after delivery, and learning has an explicit path back into the system.

**Gate:** release evidence is connected to original outcomes; methodology changes enter through RFCs rather than silent edits.

## Universal stage questions

Every stage guide must help the user answer:

1. Why does this stage exist?
2. What uncertainty does it reduce?
3. What inputs are required?
4. What decisions are allowed here?
5. Which decisions are deliberately postponed?
6. What visible result appears?
7. What should the user understand afterward?
8. How is completion checked?
9. What common mistakes and industry lessons apply?
10. What exactly is handed to the next stage?
