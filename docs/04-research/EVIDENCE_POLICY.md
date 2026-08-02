---
axiopra:
  schema_version: "0.1.0"
  id: axp.research.evidence-policy
  kind: policy
  title: Research, Evidence, and Industry Case Policy
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.foundation.constitution
    - axp.foundation.governance
    - axp.metamodel.core
  relations:
    - type: constrains
      target: axp.methodology.lifecycle
  human_outcome: The reader can distinguish historical context, evidence, criticism, and AXIOPRA's own design choices.
  machine_outcome: Research artifacts have a consistent evidence structure and source policy.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# Research, Evidence, and Industry Case Policy

## 1. Purpose

Every methodology stage must be supported by a research layer showing where the idea came from, how it has been used, what benefits and failures have been reported, and which parts AXIOPRA adopts or rejects.

This layer prevents two equal mistakes:

- copying fashionable practices without understanding their context;
- presenting AXIOPRA's own hypotheses as established scientific or industrial fact.

## 2. Required research pack for each stage

Each canonical lifecycle stage should eventually contain or link to:

```text
WHY.md                 # why the stage exists and which failure it addresses
HISTORY.md             # origin and evolution of the idea
THEORY.md              # conceptual and mathematical foundations
INDUSTRY_CASES.md      # real applications and reported outcomes
FAILURES.md            # counterexamples, misuse, costs, and anti-patterns
ALTERNATIVES.md        # competing approaches and trade-offs
SOURCES.yaml           # structured source registry
ADOPTION.md            # what AXIOPRA adopts, adapts, rejects, and why
EXAMPLES/              # worked artifacts for beginner and expert profiles
```

These may begin as sections in one file and split only when size or ownership justifies it.

## 3. Questions every case study must answer

1. Who applied the practice?
2. In which domain, organization size, team structure, and risk context?
3. What concrete problem were they trying to solve?
4. What exact form of the method did they use?
5. What changed after adoption?
6. Which benefits were measured, observed, or merely claimed?
7. Which costs, delays, or new failure modes appeared?
8. What mistakes were made during adoption?
9. What corrective action was taken?
10. What evidence supports the account?
11. What alternative explanation could produce the same result?
12. Which conditions limit transfer to AXIOPRA or another project?
13. What should a beginner misunderstand least about this case?
14. What remains uncertain or disputed?

## 4. Evidence classes

AXIOPRA uses descriptive evidence classes rather than pretending all sources are equal.

| Class | Example | Appropriate use |
|---|---|---|
| Primary formal source | specification, original paper, official theorem-prover documentation | definitions, algorithms, formal claims |
| Primary empirical source | published experiment, original dataset, incident report | measured outcomes and limitations |
| First-party engineering account | official technical report, architecture document, postmortem | implementation context and organizational lessons |
| Independent synthesis | systematic review, respected technical book, standards guidance | comparison and broader context |
| Practitioner account | conference talk, engineering blog, retrospective | hypotheses and practical signals |
| Anecdote | forum post, personal recollection | discovery only, not strong support |
| AXIOPRA observation | result from a reference project or user study | scoped project learning |
| AXIOPRA hypothesis | proposed explanation or rule | experiment and RFC input |

Evidence strength depends on relevance, method, transparency, reproducibility, and independence — not only publisher prestige.

## 5. Source record

Each external source should have a structured record:

```yaml
id: source.<stable-name>
title: <source title>
authors: []
publisher: <publisher or organization>
published: <date>
accessed: <date>
uri: <stable URI>
source_class: <evidence class>
primary_or_secondary: primary | secondary
supports:
  - <artifact or claim id>
challenges:
  - <artifact or claim id>
relevant_excerpt_location: <section, page, figure, or heading>
summary: <paraphrased relevance>
limitations: []
license_or_usage_notes: <when relevant>
archive_or_persistent_id: <DOI, RFC, standard number, archived URI>
```

Source records must identify access dates because web content and vendor documentation change.

## 6. Claim discipline

A research artifact must separate:

- what a source explicitly reports;
- what AXIOPRA infers from the source;
- what AXIOPRA proposes independently;
- what remains unknown.

Statistics must include the population, measurement definition, date, and source. Unsourced adoption numbers or projections must not enter canonical documents.

A citation supports only the claim actually made by its source. Multiple weak citations do not become strong evidence through quantity.

## 7. Negative evidence and failures

Each stage must actively search for:

- failed adoptions;
- contexts where the method added ceremony without benefit;
- incentives that distorted reported success;
- survivorship and selection bias;
- tool-specific limitations;
- organizational prerequisites;
- security or safety failures;
- maintenance and migration costs;
- criticism from credible alternative schools.

An idea with no documented limitations is not ready for canon; it is insufficiently researched.

## 8. Reproducibility

Where practical, research artifacts should include:

- query strategy and date;
- databases or search engines used;
- inclusion and exclusion criteria;
- data extraction notes;
- calculations or scripts;
- versioned snapshots or persistent identifiers;
- unresolved disagreements between sources.

LLM-assisted research must record the underlying sources. The model's summary is not itself the evidence.

## 9. Adoption decision

The final research artifact for a stage must state:

```text
Adopt       — use the idea substantially as defined.
Adapt       — use a modified form with explicit differences.
Experiment  — test in reference projects before deciding.
Reject      — do not use; record why.
Defer       — potentially valuable, but not justified now.
```

The decision must include:

- intended benefit;
- applicable profiles and contexts;
- known costs and failure modes;
- alternatives;
- validation plan;
- conditions for reconsideration.

## 10. Initial research program

Priority research packs:

1. SICP and abstraction/composition/interpreters;
2. Amazon Working Backwards;
3. Domain-Driven Design;
4. specification by example and executable specifications;
5. Design by Contract and Eiffel;
6. type-driven development across Haskell, Idris, and Rust;
7. TDD and property-based testing;
8. Lean and selective formal verification;
9. knowledge graphs and traceability models;
10. Datalog/Prolog rule engines for explainable validation;
11. category-theoretic composition as a possible formal design lens;
12. compiler and IR architecture for engineering knowledge;
13. human-AI cognitive synchronization in long-running agent workflows.

No item enters the core merely because it appears on this list.
