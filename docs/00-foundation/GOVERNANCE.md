---
axiopra:
  schema_version: "0.1.0"
  id: axp.foundation.governance
  kind: governance
  title: Governance and Controlled Evolution
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.foundation.manifesto
    - axp.foundation.constitution
  relations:
    - type: governs
      target: axp.foundation.manifesto
    - type: governs
      target: axp.foundation.constitution
    - type: governs
      target: axp.metamodel.core
  human_outcome: The reader can explain how an idea becomes canon and who is accountable for the decision.
  machine_outcome: Canon changes have a typed lifecycle that future tooling can enforce.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# Governance and Controlled Evolution

## 1. Purpose

AXIOPRA is designed to improve recursively: projects produce experience, experience produces hypotheses, and validated hypotheses may improve the methodology. This loop must remain visible, evidence-bearing, and human-governed.

The platform must be capable of learning without being allowed to rewrite itself impulsively.

## 2. Change classes

Every change is classified before implementation.

| Class | Meaning | Minimum process |
|---|---|---|
| Editorial | Meaning is unchanged: spelling, formatting, navigation. | Direct review. |
| Clarification | Makes existing intent more explicit without changing obligations. | Review plus semantic consistency check. |
| Compatible extension | Adds optional types, relations, templates, or guidance without breaking accepted consumers. | Proposal or lightweight RFC, tests, compatibility review. |
| Behavioral change | Alters methodology behavior, validation, defaults, or user-visible outcomes. | Full RFC, prototype, reference validation. |
| Structural change | Alters core metamodel, identifiers, lifecycle, schemas, or protocol boundaries. | Full RFC, migration design, compatibility plan, multiple reviews. |
| Constitutional change | Alters mission, values, MUST-level rules, governance, or trust boundaries. | Full RFC, explicit amendment, broad review, delayed acceptance. |

If classification is disputed, use the more demanding class until the dispute is resolved.

## 3. Evolution pipeline

A potential improvement follows this path:

```text
Observation
  -> Reflection
  -> Hypothesis
  -> RFC
  -> Prototype
  -> Reference-project trial
  -> Evidence review
  -> Decision
  -> Canon or rejection
  -> Compatibility and migration
  -> Post-adoption review
```

Skipping a step requires a recorded justification. Urgency may shorten review windows but does not erase traceability.

## 4. Required RFC contents

A canonical RFC must include:

1. stable RFC identifier and authorship;
2. change class and affected specification versions;
3. problem statement and observed evidence;
4. intended users and use cases;
5. proposed semantics, not only proposed syntax;
6. assumptions and scope limits;
7. alternatives considered, including doing nothing;
8. effects on the artifact graph and verifier;
9. human cognitive and UX consequences;
10. compatibility, migration, deprecation, and rollback plan;
11. security, privacy, accessibility, localization, and operational considerations;
12. prototype or experiment plan;
13. reference-project validation plan;
14. falsification criteria — evidence that would show the proposal is wrong;
15. unresolved questions;
16. decision and rationale after review.

An RFC is a decision instrument, not promotional material. It must make rejection possible.

## 5. RFC states

```text
draft -> discussion -> accepted -> implemented -> validated -> canonical
                   \-> rejected
                   \-> withdrawn
accepted/implemented/validated/canonical -> deprecated -> superseded
```

- **Draft** — incomplete proposal, open to major change.
- **Discussion** — sufficiently formed for critique.
- **Accepted** — approved for implementation or controlled experiment, not yet canon.
- **Implemented** — working implementation exists.
- **Validated** — stated evidence and reference-project criteria passed.
- **Canonical** — incorporated into a named AXIOPRA specification release.
- **Rejected** — not accepted; reasons and reconsideration conditions remain recorded.
- **Withdrawn** — author or sponsor ended the proposal.
- **Deprecated** — still understood for compatibility but no longer recommended.
- **Superseded** — replaced by an explicit successor.

Acceptance is not canonization. Implementation is not validation.

## 6. Decision criteria

Reviewers evaluate an RFC against:

- alignment with mission and Constitution;
- clarity of semantics and scope;
- measurable uncertainty reduction;
- benefits to beginner and expert workflows;
- effects on human cognitive synchronization;
- deterministic verifiability;
- semantic auditability;
- operational complexity and maintenance burden;
- ecosystem compatibility;
- evidence quality and transferability;
- reversibility and migration cost;
- simpler alternatives;
- risks of misuse or false assurance.

A clever design with no clear operational role should remain research, not canon.

## 7. Roles

Early in the project, one person may hold several roles, but reviews must still identify the role being exercised.

- **Author** — prepares the proposal and responds to findings.
- **Sponsor** — accepts responsibility for moving the proposal through the process.
- **Domain reviewer** — evaluates subject-matter truth and consequences.
- **Metamodel reviewer** — evaluates graph semantics and compatibility.
- **Verifier reviewer** — evaluates deterministic checkability and diagnostics.
- **Human-experience reviewer** — evaluates cognitive load, beginner guidance, and accessibility.
- **Security/privacy reviewer** — evaluates misuse and data risks where relevant.
- **Maintainer** — records the decision and manages release integration.

LLMs may assist every role but may not be the sole accountable approver of a canonical change.

## 8. Evidence and transfer

A lesson from one project is not automatically universal. Promotion toward canon must state:

- project context and risk level;
- sample size and duration;
- observed benefit and negative effects;
- plausible alternative explanations;
- counterexamples;
- assumptions required for transfer;
- domains where the lesson should not apply;
- confidence and unresolved uncertainty.

Research sources, industry cases, failures, and critiques must remain traceable to dates and sources. Citation count is not evidence quality.

## 9. Versioning and compatibility

AXIOPRA specifications use semantic versioning once public compatibility contracts are declared.

- **Patch** — editorial fixes and compatible clarifications.
- **Minor** — backward-compatible extensions.
- **Major** — incompatible semantic, schema, protocol, or lifecycle changes.

Before the first stable release, breaking changes are allowed but must still include migration notes because early adopters and tools may depend on them.

Stable artifact IDs must not be reused for unrelated meanings. Supersession must be explicit.

## 10. Controlled recursive improvement

At the end of a project stage or release, the system may create a reflection artifact containing:

- what was expected;
- what happened;
- where the user lost understanding;
- what checks found or missed;
- what produced unnecessary ceremony;
- what reusable lesson is hypothesized;
- what evidence would validate that lesson.

A reflection may automatically open a draft proposal. It may not automatically change canonical rules.

## 11. Emergency changes

A critical security, data-loss, or severe correctness issue may justify immediate mitigation before full RFC completion. The change must still record:

- incident and affected versions;
- emergency authority;
- temporary action;
- known side effects;
- verification performed;
- rollback plan;
- deadline for retrospective RFC and permanent resolution.

Emergency process is not a shortcut for ordinary product pressure.

## 12. Foundation freeze

Foundation Baseline Revision 1 is frozen for the first implementation cycle. During that cycle:

- contradictions and defects may be documented immediately;
- editorial repairs may be merged;
- behavioral or constitutional changes remain RFC proposals until tested against the metamodel, verifier MVP, and first reference project;
- the freeze ends through an explicit review, not by elapsed time alone.

The purpose of the freeze is not to claim perfection. It is to stop abstract expansion long enough to obtain evidence from working software and real users.
