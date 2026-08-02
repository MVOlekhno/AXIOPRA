---
axiopra:
  schema_version: "0.1.0"
  id: axp.verification.trust-model
  kind: assurance-model
  title: AXIOPRA Trust and Verification Model
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.foundation.constitution
    - axp.metamodel.core
    - axp.methodology.lifecycle
  relations:
    - type: constrains
      target: axp.verifier.rust-core
    - type: constrains
      target: axp.auditor.llm
    - type: constrains
      target: axp.proofs.lean
  human_outcome: The reader can distinguish structural closure, logical consistency, semantic review, empirical evidence, domain validation, and formal proof.
  machine_outcome: Verification records and diagnostics can declare exact scope without collapsing into an unsupported universal score.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# AXIOPRA Trust and Verification Model

## 1. Purpose

AXIOPRA aims to make an engineering repository structurally closed, traceable, internally reviewable, and selectively provable. It must not confuse that goal with a claim that all prose, domain assumptions, user needs, implementations, and future behavior can be proved perfect by one tool.

The trust model answers two questions:

1. What property is being checked?
2. Which verifier is competent to check that property?

## 2. The central boundary

A static verifier can prove facts about the formal representation it receives, for example:

- every required file or artifact exists;
- every identifier is unique;
- every relation resolves;
- forbidden dependency cycles are absent;
- accepted requirements have paths to specified evidence kinds;
- lifecycle transitions obey declared rules;
- no active accepted artifacts are linked by an unresolved contradiction relation.

It cannot, by structure alone, prove that:

- the chosen user problem is real or important;
- a domain expert's statement is physically true;
- prose has exactly one intended interpretation;
- an LLM has found every contradiction;
- tests cover every possible execution;
- the production code corresponds perfectly to a mathematical model;
- the complete product is safe, useful, lawful, ethical, or correct in every environment.

AXIOPRA therefore reports a **profile of evidence**, never an unexplained “100% trust” claim.

## 3. Assurance layers

### Layer A — Syntax and schema validation

**Primary engine:** deterministic Rust verifier.

Checks:

- parseability;
- schema versions;
- required fields and types;
- value formats;
- source locations;
- metadata/narrative presence.

Can establish:

- conformity to a named schema version.

Cannot establish:

- graph coherence or truth of content.

### Layer B — Graph and lifecycle integrity

**Primary engine:** deterministic Rust verifier.

Checks:

- stable and unique IDs;
- target resolution;
- relation registry membership;
- source/target kind constraints;
- allowed lifecycle transitions;
- canonical uniqueness;
- dependency cycles;
- supersession chains;
- required traceability paths;
- stale review dates;
- orphaned obligations.

Can establish:

- selected formal graph properties for a repository revision and conformance profile.

Cannot establish:

- correctness of narrative meaning or domain truth.

### Layer C — Declarative policy and inference

**Primary engine:** initially Rust rules; optional future Datalog or Prolog-compatible engine.

Checks and derives:

- transitive dependencies;
- policy implications;
- coverage rules;
- conflict conditions;
- impact propagation;
- explainable rule traces.

A logic engine is justified only if it improves rule clarity, explainability, extensibility, or correctness over native Rust rules. Rule semantics must be specified independently of the engine so the implementation remains replaceable.

Can establish:

- logical consequences of declared facts and rules under the chosen logic semantics.

Cannot establish:

- that input facts and rules accurately represent the world.

### Layer D — Semantic audit

**Primary engines:** humans and vendor-neutral LLM adapters.

Checks:

- ambiguous or undefined terms;
- inconsistent definitions;
- missing reasoning steps;
- incompatible promises and requirements;
- unsupported conclusions;
- hidden assumptions;
- duplicated or drifting concepts;
- contradictory constraints stated only in prose;
- gaps between narrative and metadata;
- loss of user cognitive synchronization.

LLM output must contain artifact references, quoted or precisely located evidence, severity, rationale, and remediation. Findings are review candidates, not automatic truth.

Can establish:

- that a reviewer found or did not find known semantic issues under a stated prompt, model, context, and scope.

Cannot establish:

- complete semantic consistency or proof of absence of omissions.

### Layer E — Empirical verification

**Primary engines:** tests, experiments, measurements, benchmarks, simulations, and operational observations.

Checks:

- behavior under examples and generated cases;
- properties within tested domains;
- integrations and environments;
- performance and resource constraints;
- regressions;
- real-user outcomes where measured responsibly.

Can establish:

- observed results under stated conditions.

Cannot establish:

- unbounded universal correctness unless combined with a valid proof over a complete model.

### Layer F — Formal verification

**Primary engine:** Lean for initial proof work; other systems may be supported through adapters.

Checks:

- whether an explicitly formalized proposition follows from definitions and assumptions accepted by the proof environment.

Can establish:

- machine-checked proof of a named formal statement under a named trusted computing base and toolchain.

Cannot establish automatically:

- that the formal statement matches the intended prose or physical domain;
- that production implementation matches the model;
- that assumptions hold in deployment;
- that unrelated product properties are correct.

### Layer G — Domain and accountable human validation

**Primary engine:** qualified and accountable people supported by evidence and tools.

Checks:

- domain fidelity;
- user value;
- ethical and legal acceptability;
- appropriateness of assumptions;
- trade-offs;
- release and operational accountability.

Can establish:

- an accountable decision within the reviewer's declared competence and organizational authority.

Cannot establish:

- infallibility.

## 4. Verification record

Every check produces a verification record with at least:

```yaml
record_id: <stable id>
verifier_kind: schema | graph | rule | llm | human | test | measurement | proof
verifier_name: <tool, model, person-role, or workflow>
verifier_version: <version or immutable identifier>
repository_revision: <commit sha>
profile: <conformance or risk profile>
property: <exact property checked>
scope:
  artifacts: []
  claims: []
  paths: []
assumptions: []
inputs: []
result: pass | fail | warning | inconclusive | not-run
findings: []
evidence: []
timestamp: <UTC timestamp>
reproducibility: <commands, environment, seed, or review protocol>
limits: []
```

A pass without a stated property is invalid evidence.

## 5. Diagnostic model

Diagnostics must be actionable and stable enough for tools and documentation.

```text
AXP-<AREA>-<NUMBER>
```

Proposed areas:

- `PARSE` — source parsing;
- `SCHEMA` — metadata schema;
- `ID` — identity and namespace;
- `REL` — relation semantics;
- `GRAPH` — graph integrity;
- `LIFE` — lifecycle;
- `TRACE` — traceability;
- `CONFLICT` — contradictions;
- `EVIDENCE` — evidence scope;
- `COGNITION` — missing context or user synchronization artifacts;
- `POLICY` — conformance rules;
- `PROOF` — formal statement and proof linkage.

Every diagnostic should include:

- severity;
- rule ID and version;
- source location;
- affected artifact IDs;
- why it matters;
- actual and expected state;
- remediation options;
- whether automated repair is safe;
- links to the governing rule.

The verifier should prefer precise diagnostics over a single pass/fail verdict.

## 6. Structural completeness

“Complete documentation” must always be qualified by a named profile.

Example profile rule:

```text
For every accepted requirement R classified as critical:
  there exists at least one accepted specification S where S refines R;
  there exists at least one accepted contract or type model C constraining S;
  there exists at least one implementation I implementing S;
  there exists at least one passing evidence artifact E verifying R or S;
  and no active unresolved contradiction affects the path.
```

The verifier may prove that such paths exist. It must also report their exact nodes and evidence freshness.

Existence of a path does not prove that the linked implementation truly satisfies the user's intent. Semantic, empirical, domain, and sometimes formal checks remain necessary.

## 7. Contradiction handling

Contradictions may be:

- **formal** — incompatible structured values or rules;
- **logical** — mutually unsatisfiable declared propositions;
- **semantic** — conflicting prose or terminology detected by review;
- **domain** — incompatible expert claims or measurements;
- **temporal** — both claims were valid at different times;
- **scoped** — claims apply to different profiles, users, contexts, or versions.

The system must avoid flattening all disagreement into “error”. It must represent scope and allow competing hypotheses. Acceptance is blocked only when incompatible active claims affect the same decision scope without resolution.

## 8. Assurance profile

A project status should present dimensions such as:

```yaml
assurance:
  syntax_schema: pass
  graph_integrity: pass
  policy_rules: warning
  semantic_audit: reviewed-with-findings
  empirical_evidence: partial
  formal_proof: selected-properties-only
  domain_review: pending
  human_cognitive_sync: current
```

Each dimension links to evidence records and unresolved findings.

AXIOPRA should not combine these into one universal number. A future UI may show coverage metrics for a named rule set, but every number must have a transparent denominator and drill-down.

## 9. Independence and correlated failure

Multiple green checks are valuable only when their failure modes differ.

Examples of correlated failure:

- tests and implementation generated from the same misunderstood requirement;
- an LLM reviewing text it previously authored without independent context;
- a formal proof and production code sharing an incorrect domain assumption;
- a rule engine and schema both derived from the same flawed metamodel.

The platform should record provenance and encourage independent review for high-risk claims. Independence is a spectrum, not a checkbox.

## 10. Rust verifier responsibilities

The first deterministic verifier should remain intentionally narrow and trustworthy.

MVP responsibilities:

1. discover artifacts;
2. parse YAML frontmatter;
3. validate artifact metadata against JSON Schema;
4. construct a symbol table;
5. normalize relation aliases;
6. resolve targets;
7. build the typed multigraph;
8. run core invariants;
9. evaluate a small versioned rule set;
10. emit human-readable and JSON diagnostics;
11. export graph data for visualization;
12. produce a context-compass summary from accepted artifacts without inventing missing facts.

MVP non-responsibilities:

- judging whether the product idea is valuable;
- proving prose consistent;
- rewriting documents automatically;
- generating production code;
- assigning a universal trust score;
- embedding a specific LLM vendor.

## 11. LLM auditor responsibilities

An LLM auditor may:

- retrieve the relevant subgraph;
- compare claims and terminology;
- identify candidate contradictions and omissions;
- explain why a finding matters;
- propose questions, edits, relations, or tests;
- create a review artifact for human acceptance.

It must:

- cite artifact IDs and source locations;
- separate repository facts from inference;
- expose uncertainty;
- avoid silent edits to canonical intent;
- preserve the context compass;
- return `inconclusive` when context is insufficient.

## 12. Formalization roadmap

Formal verification will begin with narrow, stable propositions. Candidate layers include:

- uniqueness and resolution invariants of the normalized IR;
- selected lifecycle transition properties;
- properties of graph transformations;
- selected RoadCore drainage algorithms;
- consistency between generated diagnostics and rule semantics.

The first proof target must be selected through an artifact that compares value, cost, stability, and correspondence risk.

## 13. Acceptance principle

AXIOPRA accepts a claim only at the strongest level actually supported by evidence.

A repository may be:

- structurally valid but semantically disputed;
- semantically reviewed but empirically untested;
- thoroughly tested but unproved;
- formally proved for selected properties but operationally unsafe;
- domain-approved but poorly traceable.

The platform's job is to make that profile visible, not to hide it behind confidence theatre.
