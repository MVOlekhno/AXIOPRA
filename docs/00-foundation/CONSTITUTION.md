---
axiopra:
  schema_version: "0.1.0"
  id: axp.foundation.constitution
  kind: policy
  title: AXIOPRA Constitution
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.foundation.manifesto
  relations:
    - type: governs
      target: axp.metamodel.core
    - type: governs
      target: axp.methodology.lifecycle
    - type: governs
      target: axp.verification.trust-model
    - type: governed-by
      target: axp.foundation.governance
  human_outcome: The reader can identify mandatory platform behavior and the boundaries of acceptable exceptions.
  machine_outcome: Normative requirements can be mapped to future verifier rules and governance checks.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# AXIOPRA Constitution

## 1. Purpose and normative language

This Constitution translates the Manifesto into enforceable project rules.

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative:

- **MUST / MUST NOT** — required for conformance unless an explicit, time-bounded exception artifact has been accepted.
- **SHOULD / SHOULD NOT** — expected by default; deviation requires a recorded reason and consequence.
- **MAY** — permitted but optional.

## 2. Sources of truth

1. The version-controlled repository MUST be the authoritative record for accepted engineering knowledge.
2. Chat transcripts, meeting notes, private prompts, model memory, and undocumented assumptions MUST NOT be treated as accepted project truth until represented by an artifact.
3. Each canonical concept MUST have one declared authoritative artifact at a given version.
4. Translations MAY exist, but the canonical language and conflict-resolution rule MUST be declared.
5. Generated views, indexes, diagrams, and summaries MUST identify their source artifacts and generation version.

## 3. Artifact identity and lifecycle

1. Every material artifact MUST have a globally unique stable identifier within its declared namespace.
2. An artifact MUST declare its kind, version, lifecycle status, maturity, owner or accountable role, dependencies, verification plan, and review policy where applicable.
3. Artifact identity MUST survive file moves and presentation changes.
4. Breaking semantic changes MUST produce a new version and an explicit migration or supersession relation.
5. Deleted accepted artifacts MUST leave a tombstone, supersession record, or other discoverable history unless legal or security requirements prohibit retention.
6. Experimental artifacts MUST be clearly distinguishable from accepted and canonical artifacts.

## 4. Human and machine representation

1. Every canonical artifact MUST provide a human-readable explanation and machine-readable metadata.
2. The human-readable layer MUST explain purpose, context, assumptions, decisions, consequences, and limits in language appropriate to its audience.
3. The machine-readable layer MUST expose identity, type, state, relations, and validation data without requiring an LLM to infer basic structure from prose.
4. Machine-readable metadata MUST NOT contradict the narrative layer.
5. When contradiction exists, the artifact MUST fail semantic acceptance until resolved; neither representation silently overrides the other.

## 5. Traceability and graph integrity

1. Every accepted user promise MUST trace to one or more requirements or an explicit decision not to implement it.
2. Every accepted requirement MUST trace to domain concepts, specifications, contracts, implementation or a justified non-code outcome, and verification evidence appropriate to risk.
3. Every proof claim MUST trace to the exact formal proposition, assumptions, proof source, and toolchain version.
4. Dangling relations, duplicate IDs, unknown relation types, and invalid lifecycle transitions MUST fail deterministic validation.
5. Cycles MUST be interpreted by relation type. A dependency cycle MAY be invalid while a peer, refinement, or mutual-consistency relation MAY be valid.
6. Traceability completeness MUST be reported by explicit rule coverage, not by an unexplained percentage.
7. A missing relation MUST NOT be fabricated solely to make validation pass.

## 6. Verification and evidence

1. Every verification result MUST state the property checked, input scope, tool or reviewer, version, assumptions, and outcome.
2. Structural validation MUST NOT be described as semantic correctness.
3. LLM review MUST be labeled probabilistic and MUST include evidence references for material findings.
4. Human review MUST identify the reviewer role and review scope; approval MUST NOT imply expertise outside that scope.
5. Formal proof MUST NOT be claimed for prose whose meaning has not been translated into an explicit formal statement.
6. Test success MUST NOT be generalized beyond stated cases, generators, environments, and properties.
7. Confidence scores MUST NOT be presented unless the scoring model, calibration basis, and interpretation are versioned and inspectable.
8. The system SHOULD prefer a profile of independent evidence over one aggregate “trust score”.

## 7. User cognition and visible progress

1. Every methodology stage MUST declare the uncertainty it reduces.
2. Every completed stage MUST produce a visible artifact and a stated cognitive outcome.
3. The system MUST maintain a context compass showing objective, current stage, active artifacts, recent decisions, verified facts, uncertainties, and next step.
4. Long-running automated work MUST publish meaningful checkpoints before the human operator is likely to lose the thread.
5. The platform MUST explain why a requested input matters before requiring it from a beginner.
6. The platform MUST NOT use progress indicators that imply certainty or completion unsupported by artifact state.
7. The user MUST be able to inspect the reasoning basis of material recommendations without requiring access to private model internals.

## 8. Development discipline

1. Production-intended implementation MUST trace to accepted upstream artifacts before release acceptance.
2. Exploratory implementation MAY precede accepted specifications only when labeled as a spike or experiment with a question, scope, isolation boundary, and exit criteria.
3. Rust is the default production language for core tooling. A different language MAY be used through an accepted architecture decision that states the role, benefit, maintenance cost, interoperability boundary, and exit strategy.
4. Invalid domain states SHOULD be prevented through types when practical.
5. Preconditions, postconditions, invariants, error semantics, and failure ownership SHOULD be explicit at component boundaries.
6. Tests SHOULD cover examples, boundaries, properties, integrations, and regressions according to risk.
7. Formal verification SHOULD be selective and driven by the consequence of error, proof feasibility, and stability of the formalized property.

## 9. AI and automation conduct

1. AI agents MUST read the canonical repository guidance before material work.
2. An agent MUST surface contradictions rather than silently choosing a convenient interpretation.
3. An agent MUST distinguish retrieved fact, repository fact, inference, proposal, and uncertainty.
4. An agent MUST NOT rewrite accepted intent, canonical terminology, or governance rules without an explicit change artifact.
5. An agent MUST NOT claim that work ran, passed, was committed, or was deployed unless the corresponding action actually succeeded.
6. Autonomous actions MUST remain bounded by declared permissions and reversible where practical.
7. Vendor-specific adapters MUST NOT become the only representation of project knowledge.
8. The platform SHOULD support equivalent workflows across multiple agents and model providers through stable schemas and protocols.

## 10. Governance and recursive improvement

1. The Foundation MUST be stable enough to implement and test, but MUST remain challengeable through evidence.
2. Canonical changes MUST follow the governance path defined in `GOVERNANCE.md`.
3. Project experience MUST enter the methodology as an observation or reflection artifact before becoming a rule.
4. The platform MUST NOT canonize a lesson from one project without stating its transfer assumptions and counterexamples.
5. Canonical self-modification MUST require accountable human approval.
6. Rejected proposals SHOULD remain discoverable with rejection reasons and conditions that could justify reconsideration.
7. Compatibility-affecting changes MUST include migration guidance and a deprecation window appropriate to ecosystem scale.

## 11. Scalability and openness

1. Stable identifiers, schemas, relation semantics, and versioning MUST be documented independently of one implementation.
2. The core model SHOULD remain small; domain-specific complexity SHOULD live in extensions.
3. Extensions MUST declare compatibility ranges and MUST NOT silently redefine core semantics.
4. The project SHOULD support offline and deterministic validation for core structural checks.
5. Public releases MUST include reproducible examples and migration notes.
6. Security, privacy, accessibility, localization, and regulatory needs MUST be treated as engineering concerns, not deferred indefinitely as “later polish”.

## 12. Conformance and exceptions

A project or tool may claim AXIOPRA conformance only against a named specification version and conformance profile.

An exception to a MUST-level rule requires an artifact containing:

- the exact rule;
- reason for deviation;
- affected scope;
- risk and consequence;
- compensating control;
- accountable owner;
- expiry or review date;
- restoration or migration plan.

An undocumented exception is non-conformance.

## 13. Maturity of knowledge

An idea is not canonical knowledge merely because it is persuasive. AXIOPRA distinguishes:

1. **Observation** — something noticed in a project or source.
2. **Hypothesis** — an explanatory or prescriptive claim worth testing.
3. **Exploratory model** — a structured proposal with assumptions and predicted consequences.
4. **Validated practice** — supported by reference use, review, and evidence within a stated scope.
5. **Canonical rule** — accepted for a specification version through governance.
6. **Deprecated rule** — retained for compatibility and historical understanding but no longer recommended.

Promotion between levels MUST leave a traceable decision record.
