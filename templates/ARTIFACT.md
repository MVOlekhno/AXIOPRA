---
axiopra:
  schema_version: "0.1.0"
  id: axp.template.artifact
  kind: guide
  title: Self-Explaining Artifact Template
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.metamodel.core
    - axp.methodology.lifecycle
  relations:
    - type: generated-from
      target: axp.metamodel.core
  human_outcome: A user can create an artifact while understanding why every section exists.
  machine_outcome: Generated artifacts begin with metadata compatible with the core schema.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# Self-Explaining Artifact Template

## How to use this template

Do not copy sections mechanically. Each section exists to reduce a specific uncertainty. If a section is not applicable, write `Not applicable` and explain why. Do not delete required sections merely to make the document look complete.

The future CLI will instantiate this template with a unique ID, artifact kind, lifecycle stage, and conformance profile.

## Copyable template

````markdown
---
axiopra:
  schema_version: "0.1.0"
  id: <namespace>.<area>.<artifact-name>
  kind: <registered-artifact-kind>
  title: <human-readable title>
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: false
  owner: <person or accountable role>
  language: en
  summary: <one paragraph describing the artifact>
  tags: []
  depends_on: []
  relations: []
  claims: []
  assumptions: []
  constraints: []
  human_outcome: <what the reader will understand after this artifact>
  machine_outcome: <what deterministic tools can now discover or check>
  verification:
    structural: required
    semantic: required
    human_review: required
    domain_review: optional
    empirical: optional
    formal: not-required
    notes: <why this verification profile is appropriate>
  review:
    cadence_days: 90
    required_roles: []
    expiry_behavior: warn
  supersedes: []
  external_references: []
---

# <Artifact title>

## 1. Why this artifact exists

Explain the problem this artifact solves. Name the uncertainty that would remain without it.

## 2. Main question

> Write the single most important question this artifact must answer.

## 3. Scope

### Included

- ...

### Excluded

- ...

## 4. Inputs and dependencies

For each input, state:

- artifact ID or external source;
- why it is needed;
- version or access date;
- whether it is accepted fact, assumption, or working hypothesis.

## 5. Questions to answer

1. ...
2. ...
3. ...

## 6. Working content

Write the actual domain, product, specification, contract, decision, evidence, or reflection content here.

Use stable local IDs for material claims, rules, scenarios, and decisions.

## 7. Claims, assumptions, and constraints

### Claims

- `C-001` — ...

### Assumptions

- `A-001` — ...

### Constraints

- `K-001` — ...

Keep the narrative synchronized with frontmatter metadata. Material claims should have evidence paths.

## 8. Decisions and alternatives

For each decision:

- selected option;
- alternatives considered;
- reason;
- consequence;
- reversibility;
- affected artifacts;
- uncertainty remaining.

## 9. Verification plan and evidence

State separately:

- deterministic structural checks;
- semantic/LLM review;
- domain expert review;
- tests, experiments, or measurements;
- formal proof, if selected;
- limitations of every check.

Do not write “verified” without naming the property and evidence.

## 10. Visible result

What can the user now open, inspect, run, compare, or visualize?

## 11. Cognitive result

What can the user now explain or decide that was unclear before?

Complete this sentence:

> Before this artifact I was uncertain about ____. Now I understand ____. The remaining uncertainty is ____.

## 12. Typical mistakes and anti-patterns

- ...

## 13. Definition of Done

- [ ] The main question is answered within the declared scope.
- [ ] Required metadata is valid.
- [ ] Dependencies and relations resolve.
- [ ] Claims, assumptions, and constraints are distinguishable.
- [ ] Contradictions are resolved or explicitly represented.
- [ ] The verification plan matches the risk profile.
- [ ] The visible result exists.
- [ ] The cognitive result can be stated by the user.
- [ ] Remaining uncertainty is explicit.
- [ ] The handoff to downstream artifacts is defined.

## 14. Handoff

State:

- what this artifact enables;
- which downstream artifact types should use it;
- which changes would invalidate downstream work;
- the next meaningful step.

## 15. Reflection

Answer after review or use:

1. What became clearer?
2. What remained ambiguous?
3. What assumption changed?
4. What information was unnecessary?
5. Where did the user lose the thread?
6. Which check caught a real issue?
7. Which check produced noise or false confidence?
8. What would make this artifact easier for a beginner?
9. What would make it more precise for an expert?
10. Does this experience justify only an observation, a hypothesis, or an RFC?
````

## Template design principles

- **Questions precede answers.** The artifact teaches the user what must be understood.
- **Visible and cognitive outcomes are separate.** A file is not evidence of understanding.
- **Prose and metadata coexist.** Humans receive meaning; machines receive explicit structure.
- **Completion is scoped.** A document can be complete for its purpose while the project remains uncertain.
- **Verification is typed.** Structural validation, semantic review, tests, domain approval, and proof are never collapsed into one word.
- **Handoffs are explicit.** Every completed artifact declares what it enables and what it may invalidate.
