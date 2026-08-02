---
axiopra:
  id: AXP-VER-TRUST
  kind: verification.trust-boundaries
  version: 0.1.0
  status: review
  stage: AXP-STAGE-08
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Exact capabilities, limits, evidence records, and independence rules for every AXIOPRA verification layer.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-VER-MODEL, AXP-VER-RULESET]
    refines: [AXP-VER-MODEL]
    constrains: [AXP-REF-ROADCORE]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-002, AXP-SEM-003, AXP-SEM-005, AXP-SEM-008]
  learning:
    external: A verification profile that reports exact checked properties without a misleading universal trust score.
    internal: The reader can distinguish structural closure, logical inference, semantic review, empirical evidence, domain approval, and formal proof.
---

# Trust Boundaries

## Purpose

AXIOPRA must make a repository structurally closed, traceable, reviewable, and selectively provable without pretending that one tool can prove the entire documentation set, implementation, physical domain, and future operation perfect.

Every assurance statement must answer two questions:

1. **What exact property was checked?**
2. **Which verifier is competent to check that property?**

A pass without a named property and scope is not evidence.

## The central boundary

A deterministic verifier can establish facts about the formal representation it receives, for example:

- every discovered canonical artifact conforms to a named schema;
- every identifier is unique;
- every required internal relation resolves exactly once;
- forbidden dependency cycles and self-loops are absent;
- lifecycle values and transitions follow declared rules;
- a named traceability profile has or lacks required paths;
- no two active artifacts declare an unresolved `conflicts_with` relation within the same scope.

Those results do **not** establish by themselves that:

- the user problem is real or important;
- the domain model is physically true;
- prose has one unambiguous intended meaning;
- an LLM found every omission or contradiction;
- tests cover every possible execution;
- a Lean model faithfully represents production Rust and the physical world;
- the released product is safe, useful, lawful, ethical, secure, or correct in every environment.

The platform therefore reports an **assurance profile**, not a single confidence number.

## Assurance layer A — Syntax and schema

**Primary mechanism:** deterministic Rust verifier.

Checks:

- parseability of Markdown and YAML front matter;
- declared schema version;
- required fields and value formats;
- known status, stage, confidence, and relation keys;
- referenced local paths where a rule requires them.

Establishes:

- conformity to a named syntax and schema version for the inspected sources.

Does not establish:

- uniqueness across the repository;
- relation meaning;
- semantic or domain correctness.

## Assurance layer B — Graph and lifecycle integrity

**Primary mechanism:** deterministic Rust verifier.

Checks:

- unique IDs;
- target resolution;
- relation registry membership;
- forbidden graph cycles;
- supersession chains;
- stage prerequisites;
- traceability paths required by a named profile;
- active conflicts;
- unresolved meaning-changing placeholders;
- required external and internal learning outcomes.

Establishes:

- selected formal graph properties of one repository revision under one rule-set version.

Does not establish:

- that a relation declared in metadata accurately captures the prose or the real world.

## Assurance layer C — Declarative rules and inference

**Primary mechanism:** Rust rules initially; a Datalog or Prolog-compatible engine remains an optional experiment.

Possible checks and derivations:

- transitive dependency and impact closure;
- policy implications;
- missing evidence paths;
- conflict conditions;
- explainable inference traces.

Establishes:

- consequences that follow from declared facts and rules under the selected logic semantics.

Does not establish:

- that the supplied facts and rules are true or complete.

A logic engine enters the canonical architecture only if it demonstrates clearer rules, stronger explanations, safer extension, or better correctness than native Rust rules. The semantics must remain specified independently of one engine.

## Assurance layer D — Semantic audit

**Primary mechanisms:** accountable human review and vendor-neutral LLM adapters.

Checks:

- ambiguous or undefined terms;
- incompatible statements hidden in prose;
- missing reasoning steps;
- unsupported conclusions;
- promise-to-specification drift;
- duplicate or drifting concepts;
- narrative/metadata mismatch;
- missing alternatives and consequences;
- loss of the human operator's project thread.

Establishes:

- that a named reviewer found or did not find issues under a declared context, model, prompt or review protocol, and repository revision.

Does not establish:

- proof of complete semantic consistency or absence of omissions.

LLM findings are candidates for review. They must cite artifact IDs and source locations and may return `UNKNOWN` or `INCONCLUSIVE` when context is insufficient.

## Assurance layer E — Empirical evidence

**Primary mechanisms:** tests, simulations, experiments, measurements, benchmarks, reference projects, and operational observations.

Checks:

- examples and boundary cases;
- generated properties within defined domains;
- component and system integrations;
- performance and resource constraints;
- regressions;
- observed user and operational outcomes.

Establishes:

- observed results under stated inputs, environments, generators, samples, and tool versions.

Does not establish:

- universal correctness outside the measured or generated domain.

## Assurance layer F — Formal proof

**Primary mechanism:** Lean for the initial proof program.

Checks:

- whether an exact proposition follows from explicit definitions and assumptions in a pinned proof environment.

Establishes:

- a machine-checked proof of the named formal statement within its trusted computing base.

Does not automatically establish:

- that the formal statement matches the intended natural-language requirement;
- that the assumptions hold in operation;
- that production Rust corresponds to the model;
- that unrelated product properties are correct.

Every proof must link the domain intent, formal statement, assumptions, proof source, toolchain, and model-to-implementation correspondence argument.

## Assurance layer G — Domain and accountable human judgment

**Primary mechanism:** qualified and accountable people supported by evidence and tools.

Checks:

- intended user value;
- domain fidelity;
- ethical, legal, safety, privacy, and security acceptability;
- trade-offs and residual risk;
- release accountability.

Establishes:

- an accountable decision within the reviewer's declared competence and authority.

Does not establish:

- infallibility or unlimited transfer to another context.

## Verification record

Every executed check should produce a versioned record equivalent to:

```yaml
record_id: AXP-CHECK-<unique-id>
repository_revision: <commit SHA>
profile: <named conformance or risk profile>
verifier_kind: schema | graph | rule | llm | human | test | measurement | proof
verifier_name: <tool, model, workflow, or reviewer role>
verifier_version: <immutable version or identifier>
property: <exact property checked>
scope:
  artifacts: []
  claims: []
  paths: []
assumptions: []
inputs: []
result: pass | warn | fail | unknown | inconclusive | not-run
findings: []
evidence: []
reproducibility: <command, environment, seed, or protocol>
limits: []
```

A check record is evidence about the property declared in `property`; it is not a certificate for the entire repository.

## Structural completeness is profile-relative

The phrase “complete documentation” is invalid unless attached to a named profile and rule set.

A possible critical-requirement rule is:

```text
For each active critical requirement R:
  at least one active specification refines R;
  at least one active contract or type artifact constrains that specification;
  at least one implementation realizes it;
  at least one passing evidence artifact verifies or tests it;
  and no unresolved active conflict affects the path.
```

The verifier may establish whether such paths exist. It must expose the actual nodes and missing edges.

Path existence still does not prove that the implementation truly fulfills the user's real intent. Semantic, empirical, domain, and sometimes formal assurance remain necessary.

## Contradiction classes

The system distinguishes:

- **structured conflict** — incompatible machine-readable values or relations;
- **logical conflict** — declared propositions cannot jointly hold under the same assumptions;
- **semantic conflict** — incompatible prose or terminology found by review;
- **domain conflict** — expert claims or measurements disagree;
- **temporal conflict** — claims were valid at different times;
- **scoped alternative** — claims apply to different users, profiles, versions, or contexts.

Not every disagreement blocks the repository. A block occurs when incompatible active claims affect the same acceptance scope without a resolution artifact.

## Independence and correlated failure

Several green checks are valuable only when their failure modes differ.

Examples of correlated failure:

- tests and code generated from the same misunderstood requirement;
- an LLM reviewing text it authored without independent retrieval or critique;
- a proof and implementation sharing an incorrect domain assumption;
- schema and rule set derived from the same flawed metamodel.

Verification records should preserve provenance so reviewers can judge independence. High-risk claims should use different reviewers, models, evidence types, or derivation paths where practical.

## Assurance profile

A project status view may report:

```yaml
assurance:
  syntax_schema: pass
  graph_integrity: pass
  declarative_rules: warn
  semantic_audit: reviewed-with-findings
  empirical_evidence: partial
  formal_proof: selected-properties-only
  domain_review: pending
  human_context_compass: current
```

Every dimension links to check records and unresolved findings. AXIOPRA must not combine these dimensions into one universal “trust score”. Any coverage percentage must show its exact numerator, denominator, rule version, and drill-down.

## Acceptance principle

AXIOPRA states a claim only at the strongest level actually supported by evidence.

A repository may be structurally valid yet semantically disputed, heavily tested yet unproved, formally proved for one property yet operationally unsafe, or domain-approved yet poorly traceable. The platform's purpose is to make that profile visible rather than hide it behind confidence theatre.
