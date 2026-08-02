---
axiopra:
  id: AXP-MM-RELATION
  kind: metamodel.relation
  version: 0.1.0
  status: active
  stage: AXP-STAGE-01
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Typed graph edges and integrity rules for AXIOPRA artifacts.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-MM-ARTIFACT]
    constrains: [AXP-MTH-STAGES, AXP-VER-MODEL]
    realizes: [AXP-FND-CONSTITUTION]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003, AXP-RULE-005]
    semantic: [AXP-SEM-002, AXP-SEM-004, AXP-SEM-006]
  learning:
    external: A finite initial vocabulary of graph relations and cycle rules.
    internal: The reader can explain why a file link is weaker than a typed semantic relation.
---

# Relation Model

A relation is a directed, typed statement from one artifact to another. A Markdown hyperlink aids navigation; it is not automatically a semantic relation.

## Canonical relation types v0.1

- `depends_on`: the source cannot be correctly interpreted or completed without the target.
- `derives_from`: the source is justified or calculated from the target.
- `refines`: the source makes the target more precise without changing its intent.
- `constrains`: the source limits valid interpretations or implementations of the target.
- `realizes`: the source implements or operationalizes the target.
- `verifies`: the source checks a declared property of the target.
- `tests`: the source empirically exercises the target.
- `proves`: the source formally establishes a proposition declared by the target, within stated assumptions.
- `informs`: the source provides relevant context but is not required.
- `produces`: completion of the source creates or enables the target.
- `supersedes`: the source replaces the target and must state compatibility or migration.
- `conflicts_with`: the source is knowingly inconsistent with the target and blocks joint activation until resolved.

## Direction rule

The metadata is read as: **this artifact RELATION target**. For example, a test artifact with `tests: [AXP-REQ-017]` states that the test exercises requirement AXP-REQ-017.

## Graph invariants

1. Every internal target ID resolves to exactly one artifact.
2. An active artifact may not `conflicts_with` another active artifact without an open resolution record.
3. `depends_on`, `derives_from`, `refines`, `realizes`, `verifies`, `tests`, and `proves` may not contain a self-loop.
4. Dependency cycles are forbidden unless an RFC defines a legitimate strongly connected model and the verifier has an explicit rule for it.
5. `supersedes` is acyclic and points from newer to older artifacts.
6. `proves` must identify assumptions and the proposition boundary in the proof artifact.
7. `tests` and `verifies` do not imply `proves`.
8. `informs` does not satisfy a required dependency.
9. Removing an artifact is blocked while active incoming required edges exist.
10. Every user promise intended for release must have at least one traversable path to implementation and at least one path to verification, or an explicit waiver with residual risk.

## Traceability paths

The default forward path is:

`user promise → domain concept → specification → contract → type/architecture → implementation → test/evidence → release`

A selective formal path may branch from a contract or proposition:

`contract/proposition → formal model → proof`

Project learning returns through a controlled feedback path:

`observation → lesson → RFC → reference validation → canon change`

Feedback is allowed; silent mutation is not.
