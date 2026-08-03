---
axiopra:
  id: AXP-RSH-EVIDENCE
  kind: research.evidence-policy
  version: 0.1.0
  status: review
  stage: AXP-STAGE-10
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Detailed source registry, case-study questions, evidence classes, negative-evidence rules, and AXIOPRA adoption decisions.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-RSH-GUIDE]
    refines: [AXP-RSH-GUIDE]
    informs: [AXP-MTH-STAGES, AXP-REF-ROADCORE]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-003, AXP-SEM-005, AXP-SEM-007]
  learning:
    external: A repeatable evidence dossier that records origins, applications, benefits, failures, alternatives, and limitations for each methodology stage.
    internal: The reader can distinguish a primary source, an industry account, an inference, an AXIOPRA observation, and an untested hypothesis.
---

# Evidence and Industry-Case Policy

## Purpose

Every methodology stage must eventually be supported by an evidence dossier showing where the idea came from, how it has been applied, what benefits and failures have been reported, and which parts AXIOPRA adopts, adapts, rejects, or leaves experimental.

The research layer prevents two equal mistakes:

- copying famous practices without understanding their context;
- presenting AXIOPRA hypotheses as established scientific or industrial fact.

## Standard dossier

A mature stage dossier should contain or link to:

```text
WHY.md                 # failure or uncertainty the stage addresses
HISTORY.md             # origin and evolution
THEORY.md              # conceptual or mathematical foundations
INDUSTRY_CASES.md      # real applications and outcomes
FAILURES.md            # counterexamples, costs, misuse, and anti-patterns
ALTERNATIVES.md        # competing approaches and trade-offs
SOURCES.yaml           # structured source registry
ADOPTION.md            # adopt, adapt, experiment, reject, or defer
EXAMPLES/              # beginner and expert worked artifacts
```

A small dossier may combine these as sections in one artifact. It should split only when ownership, size, review, or update cadence makes separation useful.

## Required questions for each industry case

1. Who applied the practice?
2. In which domain, organization size, team structure, and risk context?
3. Which concrete problem were they trying to solve?
4. Which exact version or interpretation of the method did they use?
5. What changed after adoption?
6. Which benefits were measured, directly observed, self-reported, or merely claimed?
7. Which costs, delays, or new failure modes appeared?
8. What mistakes occurred during adoption?
9. What corrective action was taken?
10. What primary evidence supports the account?
11. What alternative explanation could produce the same result?
12. Which conditions limit transfer to another project or to AXIOPRA?
13. What is the most dangerous beginner misunderstanding of this case?
14. What remains uncertain, contested, or unavailable?

A case that reports only success is incomplete.

## Evidence classes

### Primary formal source

Examples: a specification, original paper, official language or theorem-prover documentation.

Use for definitions, algorithms, semantics, and formal claims.

### Primary empirical source

Examples: original dataset, experiment, incident report, controlled user study, reproducible benchmark.

Use for measured outcomes within the reported design and limitations.

### First-party engineering account

Examples: official architecture document, technical report, repository, migration report, or postmortem from the organization involved.

Use for implementation context and organizational lessons while accounting for incentives and missing independent validation.

### Independent synthesis

Examples: systematic review, standards guidance, or a well-supported technical synthesis.

Use for comparison, history, and broader context.

### Practitioner account

Examples: conference talk, engineering blog, retrospective, or detailed tutorial.

Use as a practical signal and hypothesis source, not automatically as causal proof.

### Anecdote

Examples: forum post, personal recollection, isolated social-media account.

Use for discovery only until stronger evidence exists.

### AXIOPRA observation

A result recorded from a reference project, usability study, verifier fixture, or real project under declared conditions.

Use as scoped evidence about that context.

### AXIOPRA hypothesis

A proposed explanation or rule not yet validated.

Use as input to an experiment or RFC, never as established fact.

## Structured source record

```yaml
id: AXP-SRC-<stable-id>
title: <source title>
authors: []
publisher: <publisher or organization>
published: <date>
accessed: <date>
uri: <stable URI or persistent identifier>
source_class: <evidence class>
primary_or_secondary: primary | secondary
supports: []
challenges: []
relevant_location: <page, section, figure, heading, commit, or issue>
summary: <paraphrased relevance>
limitations: []
conflicts_of_interest: []
archive_or_persistent_id: <DOI, RFC, standard number, archived URI>
```

Publication and access dates matter because vendor documentation, web pages, repositories, and practices change.

## Claim discipline

A research artifact must separate:

- what a source explicitly reports;
- what AXIOPRA infers;
- what AXIOPRA proposes independently;
- what remains unknown.

Statistics must include population, measurement definition, time period, date, and source. Unsourced adoption percentages or future projections must not enter canonical documents.

A citation supports only the claim its source actually supports. Citation quantity does not compensate for weak relevance or method.

## Negative evidence

Every dossier must actively search for:

- failed adoption;
- ceremony without measurable benefit;
- organizational prerequisites;
- maintenance and migration cost;
- security, privacy, or safety problems;
- tool-specific limitations;
- incentives that distort success reports;
- survivorship and selection bias;
- criticism from credible alternative schools;
- contexts where a simpler method performs better.

An approach with no documented limitations is insufficiently researched, not universally successful.

## Reproducibility

Where practical, record:

- research question and search date;
- sources, databases, and search engines consulted;
- inclusion and exclusion criteria;
- extraction notes;
- calculations, scripts, or datasets;
- persistent identifiers or versioned snapshots;
- disagreements between reliable sources;
- missing evidence.

An LLM summary is not itself evidence. The underlying source and the exact supported claim remain mandatory.

## Adoption decision

The conclusion of a dossier uses one of these states:

- **Adopt** — use substantially as defined.
- **Adapt** — use a modified form and state the differences.
- **Experiment** — test in reference projects before deciding.
- **Reject** — do not use; preserve reasons and reconsideration conditions.
- **Defer** — potentially useful but unjustified now.

The decision states intended benefit, applicable profiles, known costs, alternatives, validation plan, failure criteria, and conditions for reassessment.

## Initial research program

Priority dossiers:

1. SICP: abstraction, composition, interpreters, and metalinguistic thinking.
2. Working Backwards.
3. Domain-Driven Design.
4. Specification by Example and executable specifications.
5. Design by Contract and Eiffel.
6. Type-driven development across Haskell, Idris, and Rust.
7. TDD and property-based testing.
8. Lean and selective formal verification.
9. Knowledge graphs and requirements traceability.
10. Datalog and Prolog for explainable rule evaluation.
11. Category-theoretic composition as a possible formal design lens.
12. Compiler and IR architecture for engineering knowledge.
13. Human-AI cognitive synchronization in long-running agent workflows.

Presence on this list grants no method canonical status.
