---
axiopra:
  id: AXP-VER-LLM
  kind: verification.llm-auditor
  version: 0.1.0
  status: review
  stage: AXP-STAGE-08
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Provider-neutral input, finding, provenance, permission, and evaluation contract for semantic LLM audits.
  relations:
    depends_on: [AXP-MM-ARTIFACT, AXP-MM-RELATION, AXP-VER-MODEL, AXP-VER-TRUST]
    realizes: [AXP-VER-MODEL]
    informs: [AXP-MTH-STAGES]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-002, AXP-SEM-003, AXP-SEM-004, AXP-SEM-006, AXP-SEM-008]
  learning:
    external: A common audit contract usable by ChatGPT, Claude Code, Codex, local models, and future agent environments.
    internal: The reader can explain why an LLM is a probabilistic critic rather than an oracle or owner of project intent.
---

# Semantic LLM Auditor

## Purpose

The semantic auditor examines meaning that schemas and graph algorithms cannot fully determine. It identifies candidate ambiguity, omissions, incompatible claims, terminology drift, unsupported conclusions, weak alternatives, and breaks in the human operator's project continuity.

It is a critic and collaborator. It is not a theorem prover, deterministic verifier, domain authority, or autonomous owner of intent.

## Required audit package

An audit invocation should identify:

```yaml
repository_revision: <commit SHA>
axiopra_version: <version>
profile: <risk or conformance profile>
objective: <current intended outcome>
stage: <current lifecycle stage>
active_artifacts: []
authoritative_definitions: []
recent_decisions: []
claims_assumptions_unknowns: []
deterministic_diagnostics: []
audit_questions: []
retrieval_limits: []
permissions:
  read: true
  propose: true
  write: false
```

The context builder should retrieve the smallest coherent subgraph needed for the question, not dump an uncontrolled repository into one prompt.

## Required finding format

```yaml
finding_id: <audit-local stable id>
category: ambiguity | omission | contradiction | unsupported_claim | terminology_drift | traceability_gap | evidence_overreach | cognitive_desync
severity: info | warning | error | critical
artifacts: []
source_locations: []
repository_evidence: <what the sources actually state>
inference: <why this may be a defect>
consequence: <affected decision, stage, or downstream artifact>
confidence: low | medium | high
questions: []
remediation_options: []
verification_needed: []
status: proposed
```

Qualitative confidence is a model self-assessment, not a calibrated probability unless a separate evaluation proves calibration for the defined task.

## Audit modes

### Stage audit

Checks whether one stage answers its declared primary question, reduces the named uncertainty, produces visible and learning outcomes, and meets its quality gate.

### Cross-stage traceability audit

Follows user promises through domain meaning, specification, contracts, types, architecture, implementation, evidence, and release outcomes.

### Terminology audit

Detects undefined, duplicated, conflicting, or drifting terms while respecting bounded contexts and legitimate scoped meanings.

### Decision audit

Checks alternatives, rationale, consequences, reversibility, supersession, and whether a decision was made at the correct lifecycle stage.

### Assurance audit

Finds evidence claims that exceed the scope of schemas, rules, tests, measurements, reviews, or formal proofs.

### Cognitive synchronization audit

Checks whether the objective, current stage, recent changes, verified facts, uncertainty, and next step remain reconstructable by the human.

### Change-impact audit

Examines downstream meaning after a proposed upstream change and lists artifacts requiring review or regeneration.

### Independent re-audit

Uses a different model, context construction, reviewer, or prompt family to reduce correlated failure for high-risk findings.

## Write boundary

The default auditor is read-only. It may propose:

- a finding artifact;
- questions for the human;
- a patch or change set;
- corrected relation metadata;
- a test, experiment, review request, or RFC draft.

It must not silently rewrite accepted intent, canonical terminology, or governance rules. A write action requires explicit permission and returns a reviewable diff. Contradictions are surfaced before any attempted repair.

## Context compass obligation

Long-running agent work must keep this compact state current:

```yaml
objective: <current outcome>
stage: <current stage>
artifacts_in_scope: []
what_changed: []
why_changed: []
verification_state: []
open_uncertainty: []
next_meaningful_step: <one action>
```

The compass is derived from repository artifacts and recent accepted changes. It is navigation, not proof.

An agent that continues substantial work after the compass becomes stale creates a cognitive-desynchronization finding against its own session.

## Provider neutrality

ChatGPT, Claude Code, Codex, local models, and future systems should consume and produce the same AXIOPRA semantic package.

Provider adapters may optimize tool invocation, retrieval, caching, local instructions, or user interface. They must preserve:

- artifact IDs and versions;
- repository revision;
- source provenance;
- permissions and write boundaries;
- finding semantics;
- model and adapter identity;
- incomplete-context disclosure;
- human approval state.

Essential project meaning must never live only in a vendor prompt or private conversation.

## Semantic audit protocol

The auditor checks at least:

1. Does each artifact answer its declared question?
2. Are claims distinguishable from assumptions, decisions, hypotheses, and unknowns?
3. Are terms consistent inside the declared context?
4. Do active artifacts contradict one another in the same scope?
5. Does every user promise have downstream refinement or an explicit rejection?
6. Are acceptance criteria measurable or otherwise reviewable?
7. Are contracts, types, implementation, and evidence aligned?
8. Are alternatives and consequences represented honestly?
9. Are proof and test claims scoped correctly?
10. Are stale or orphaned artifacts misleading current decisions?
11. Did automation introduce capability not justified upstream?
12. Can the user still explain the current project state and next step?

The auditor may report `UNKNOWN` or `INCONCLUSIVE`. Forced certainty is a defect.

## Evaluation plan

The audit layer must be tested against repositories with seeded:

- direct contradictions;
- subtle unit and scope conflicts;
- missing traceability links;
- unsupported confidence claims;
- terminology drift;
- circular justification;
- stale artifacts;
- valid alternatives that should not be treated as contradictions;
- semantic defects present only across several files;
- technically correct work performed while the context compass becomes stale.

Evaluation dimensions:

- precision and recall within the seeded set;
- false-alarm burden;
- provenance accuracy;
- artifact and source-location accuracy;
- explanation usefulness;
- remediation usefulness;
- agreement with independent human review;
- sensitivity to model and prompt changes;
- ability to admit insufficient context.

No benchmark result proves complete semantic consistency in arbitrary projects.

## Security and privacy boundary

An adapter must declare which repository content leaves the local environment, which provider receives it, how long it may be retained, and which secrets or personal data are excluded. Retrieval filters and redaction are security controls; they must not be silently bypassed for audit completeness.

## Acceptance principle

An LLM audit is accepted as a review artifact when its scope, model, repository revision, source evidence, findings, uncertainty, and human disposition are recorded. It never substitutes for a deterministic pass, domain approval, empirical evidence, or formal proof.
