---
axiopra:
  schema_version: "0.1.0"
  id: axp.metamodel.core
  kind: metamodel
  title: AXIOPRA Core Metamodel
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.foundation.manifesto
    - axp.foundation.constitution
    - axp.foundation.governance
  relations:
    - type: enables
      target: axp.methodology.lifecycle
    - type: enables
      target: axp.verification.trust-model
    - type: specified-by
      target: axp.schema.artifact-v0-1
  human_outcome: The reader can explain how engineering knowledge becomes typed nodes, relations, constraints, and lifecycle states.
  machine_outcome: Parsers, validators, graph tools, SDKs, and agents share one minimal semantic model.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# AXIOPRA Core Metamodel

## 1. Purpose

The metamodel defines the smallest common language through which humans, deterministic tools, LLMs, rule engines, and proof systems can refer to the same engineering knowledge.

It is not a universal ontology of all engineering. It is a stable kernel that domains can extend without redefining core semantics.

## 2. Linguistic model

AXIOPRA deliberately separates linguistic roles:

- **Nouns become artifact nodes** — user, problem, requirement, domain concept, contract, decision, test, proof, reflection.
- **Verbs become typed relations** — depends on, refines, satisfies, constrains, implements, verifies, contradicts, supersedes.
- **Adjectives become metadata** — draft, critical, accepted, deprecated, confidential, high-risk.
- **Modal statements and quantities become constraints** — must, may, exactly one, at least one, never, before, after.
- **Evidence becomes a first-class artifact or relation annotation** — source, test result, review, measurement, formal proof.

Free prose remains essential for meaning, but basic graph structure must not depend on an LLM inferring grammar from prose.

## 3. Mathematical shape

At a given repository revision, the normalized project model is a typed directed multigraph:

```text
G = (V, E, Tᵥ, Tₑ, M, C)
```

where:

- `V` is the set of artifact nodes;
- `E` is the set of directed relation edges;
- `Tᵥ` maps each node to an artifact kind;
- `Tₑ` maps each edge to a relation type;
- `M` is versioned metadata attached to nodes and edges;
- `C` is the set of constraints and validation rules.

It is a **multigraph** because two artifacts may have several distinct relations, each with separate meaning and evidence.

This mathematical representation establishes structure only. It does not claim that every narrative meaning is completely formalized.

## 4. Artifact model

A normalized artifact contains at least:

```text
Artifact {
  id
  kind
  title
  version
  status
  maturity
  canonical
  owner
  language
  summary
  dependencies
  relations
  claims
  assumptions
  constraints
  human_outcome
  machine_outcome
  verification_plan
  review_policy
  source_location
}
```

### 4.1 Stable identity

An artifact ID identifies meaning, not a file path.

Recommended format:

```text
<namespace>.<domain>.<concept-or-role>
```

Examples:

```text
axp.foundation.manifesto
axp.methodology.lifecycle
roadcore.requirement.no-trapped-low-point
roadcore.contract.profile-station-order
roadcore.proof.flow-monotonicity
```

Rules:

- lowercase ASCII letters, digits, hyphens, underscores, and dots only;
- at least two dot-separated segments;
- IDs are never reused for unrelated meaning;
- file moves do not change identity;
- semantic replacement uses `supersedes` rather than identity reuse.

### 4.2 Artifact kind

The core registry starts with broad semantic families. Profiles may define narrower kinds.

**Foundation and guidance**

- `guide`
- `principle-set`
- `policy`
- `governance`
- `glossary`

**Product intent**

- `vision`
- `press-release`
- `faq`
- `persona`
- `problem`
- `outcome`
- `requirement`

**Domain knowledge**

- `bounded-context`
- `domain-concept`
- `entity`
- `value-object`
- `domain-event`
- `domain-invariant`

**Behavior and design**

- `specification`
- `scenario`
- `acceptance-criterion`
- `contract`
- `type-model`
- `interface`
- `architecture`
- `decision`

**Implementation and operation**

- `implementation`
- `configuration`
- `migration`
- `deployment`
- `runbook`

**Evidence and assurance**

- `test`
- `property-test`
- `audit`
- `review`
- `benchmark`
- `formal-statement`
- `proof`

**Research and evolution**

- `source`
- `case-study`
- `observation`
- `reflection`
- `hypothesis`
- `rfc`
- `experiment`
- `deprecation`

A new kind requires a definition, intended use, required fields, allowed relations, and compatibility classification.

### 4.3 Status and maturity are separate

`status` describes governance state:

```text
draft | proposed | accepted | rejected | deprecated | superseded | archived
```

`maturity` describes evidence state:

```text
hypothesis | exploratory | validated | canonical
```

Examples:

- an RFC may be `accepted` but still `exploratory`;
- a long-used practice may be `validated` but not `canonical`;
- a canonical rule may later become `deprecated` while retaining historical maturity evidence.

Tools must not infer one dimension from the other.

### 4.4 Claims, assumptions, and constraints

A narrative artifact may contain several checkable statements.

- A **claim** states what is believed or asserted.
- An **assumption** declares a condition taken as given within scope.
- A **constraint** restricts valid states, behavior, or process.

Material claims should have local IDs so evidence can address individual statements rather than vaguely “supporting the document”.

Example:

```yaml
claims:
  - id: C-001
    statement: Every accepted requirement has at least one verification path.
    evidence_class: structural-rule
    confidence: specified
```

Confidence labels are descriptive unless a calibrated numerical model exists.

## 5. Relation model

A normalized relation contains:

```text
Relation {
  source
  type
  target
  statement
  evidence
  status
  attributes
}
```

Direction is semantic and must be read literally from source to target.

### 5.1 Core relation registry

| Relation | Meaning of `source -> target` | Typical cycle policy |
|---|---|---|
| `depends-on` | source requires target to be meaningful or usable | forbidden within one dependency layer unless explicitly modeled |
| `derives-from` | source was reasoned or transformed from target | normally acyclic |
| `refines` | source adds detail to target without intending contradiction | normally acyclic |
| `motivates` | source provides the reason for target | cycles discouraged |
| `constrains` | source limits valid interpretations or states of target | cycles require review |
| `governs` | source defines process or authority for target | cycles forbidden in authority chain |
| `organizes` | source groups or navigates target | cycles allowed if harmless |
| `specifies` | source states required behavior or structure of target | cycles discouraged |
| `implements` | source realizes target in executable or operational form | cycles forbidden |
| `satisfies` | source fulfills an obligation stated by target | cycles forbidden |
| `tests` | source exercises target under stated cases or generators | cycles forbidden |
| `verifies` | source provides evidence about a stated property of target | cycles forbidden |
| `proves` | source formally proves a proposition represented by target | cycles forbidden |
| `observes` | source records evidence or experience concerning target | cycles allowed only through separate events |
| `challenges` | source presents evidence or reasoning against target | cycles allowed |
| `contradicts` | source and target cannot both be accepted under the same scope | symmetric semantic pair |
| `supersedes` | source replaces target for a declared scope/version | acyclic |
| `generated-from` | source is mechanically produced from target | normally acyclic |
| `equivalent-to` | source and target are declared semantically equivalent within scope | symmetric; equivalence consistency required |
| `references` | source cites target without stronger semantic commitment | cycles allowed |

Aliases must normalize to canonical relation names before validation.

### 5.2 Relation typing

Profiles may define allowed source and target kinds. For example:

```text
implementation --implements--> specification
property-test --verifies--> domain-invariant
proof --proves--> formal-statement
rfc --supersedes--> policy
```

The core must reject obviously meaningless relations, such as a proof claiming to `proves` an unformalized marketing paragraph without a linked formal statement.

### 5.3 Contradictions

A `contradicts` edge is a valid graph object and an invalid acceptance condition only when both ends are simultaneously active in the same scope.

This allows the repository to preserve competing hypotheses or historical decisions while preventing downstream acceptance from silently combining them.

## 6. Lifecycle transitions

The default status transitions are:

```text
draft -> proposed -> accepted
                  \-> rejected
accepted -> deprecated -> superseded -> archived
accepted -> superseded
rejected -> draft       # only with new evidence or changed proposal
```

A profile may require extra gates. Transition events must record actor, date, reason, and applicable evidence.

Content change after acceptance requires either:

- a compatible version increment and review; or
- a new artifact version with an explicit replacement relation.

## 7. Core invariants

A conforming normalized graph must satisfy at least:

1. **Unique identity** — no two active artifacts share an ID and version.
2. **Resolvable relations** — every non-external target resolves or is explicitly declared external.
3. **Known semantics** — every kind, relation, status, and maturity value belongs to a versioned registry.
4. **Schema validity** — machine metadata conforms to its declared schema version.
5. **Canonical uniqueness** — one active canonical artifact exists per canonical role and scope.
6. **Legal transitions** — lifecycle changes follow allowed transition rules.
7. **Typed relations** — source and target kinds are compatible with relation semantics.
8. **Dependency integrity** — forbidden dependency cycles do not exist.
9. **Contradiction visibility** — simultaneously active contradictions block affected acceptance paths.
10. **Evidence scope** — verification claims identify the property and scope actually checked.
11. **Proof linkage** — every proof links to an exact formal statement and assumptions.
12. **Dual outcomes** — required stages declare human and machine outcomes.
13. **Review freshness** — time-sensitive accepted knowledge is not past its review policy without being marked stale.
14. **No silent supersession** — replacements explicitly name what they replace and in which scope.
15. **No orphaned obligations** — conformance profiles define which accepted obligations require downstream satisfaction and evidence paths.

Not all invariants belong in JSON Schema. Cross-artifact and graph invariants are evaluated after parsing and normalization.

## 8. Two-layer document format

The initial authoring format is Markdown with an `axiopra` YAML frontmatter block.

```markdown
---
axiopra:
  schema_version: "0.1.0"
  id: example.requirement.export-png
  kind: requirement
  title: Export drawing as PNG
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: false
  relations:
    - type: derives-from
      target: example.press-release
  human_outcome: The user understands what export outcome is promised.
  machine_outcome: The requirement can enter traceability analysis.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# Export drawing as PNG

Human-readable narrative follows here.
```

The verifier parses the frontmatter, validates the inner `axiopra` object, and stores the narrative location without pretending to have fully formalized the prose.

Sidecar YAML and API-native representations may be supported later, but they must normalize to the same IR.

## 9. Engineering Intermediate Representation

The future AXIOPRA compiler pipeline is:

```text
Markdown/YAML/API inputs
  -> parse
  -> schema validation
  -> identifier and registry resolution
  -> normalization into Engineering IR
  -> typed relation graph
  -> lifecycle and conformance rules
  -> optional logic rules
  -> diagnostics
  -> human views, diagrams, SDKs, agent context, and generators
```

The Engineering IR is the canonical runtime representation of a repository revision, not a replacement for source artifacts.

Initial IR components:

- artifact symbol table;
- relation table;
- registry versions;
- claims and evidence index;
- lifecycle events;
- diagnostics with stable rule IDs and source spans;
- derived graph views;
- conformance profile and verifier version.

## 10. Graph views

The same graph may be projected into several user-facing views:

- **intent view** — user, problem, promised outcomes;
- **domain view** — concepts, invariants, events, boundaries;
- **traceability view** — promise to requirement to implementation to evidence;
- **decision view** — alternatives, rationale, consequences, supersession;
- **assurance view** — tests, audits, proofs, unresolved risks;
- **change-impact view** — downstream artifacts affected by a proposed change;
- **cognitive path** — what the user has learned and which uncertainty each stage reduced;
- **evolution view** — observations, reflections, hypotheses, RFCs, and canon changes.

A percentage dashboard must be derived from explicit rules and accompanied by the underlying missing or satisfied paths.

## 11. Extensions

Extensions may add domain kinds, relation constraints, validators, templates, or views. An extension must declare:

- unique namespace;
- core compatibility range;
- semantic definitions;
- schemas and rules;
- collision policy;
- migration and deprecation policy;
- security and performance implications.

Extensions must not silently redefine core relations.

## 12. Category theory, logic programming, and proof systems

These are planned research and extension directions, not prerequisites for the core model.

- **Category-theoretic ideas** may help reason about composition, identity, transformations, and lawful pipelines. The core will not claim categorical structure until objects, morphisms, laws, and practical benefits are stated precisely.
- **Datalog or Prolog** may provide a concise rule layer for transitive closure, policy queries, and explainable inference. The canonical semantics must remain specified independently so the engine is replaceable.
- **Lean** may formalize selected metamodel properties or domain algorithms. Formalization must target explicit propositions; it does not automatically prove the correctness of all prose or tooling.
- **Haskell and Idris** may serve as research environments for algebraic and dependent type models. Rust remains the primary production implementation language unless governance accepts a different role split.

The rule is practical: advanced theory enters the platform when it produces clearer semantics, stronger checks, or simpler composition — not merely prestige.

## 13. Open questions for validation

The first implementation cycle must test:

1. whether Markdown frontmatter is sufficiently ergonomic for beginners;
2. which artifact kinds are truly core versus profile-specific;
3. which traceability rules produce signal rather than ceremony;
4. how much relation authoring can be inferred safely and then confirmed by a human;
5. how contradictions should be scoped across versions and alternatives;
6. how to represent quantities, units, tolerances, and equations in engineering profiles;
7. which graph diagnostics are understandable without graph-theory knowledge;
8. whether a separate rule language is justified after the Rust verifier MVP;
9. how to measure cognitive synchronization without pretending to measure thought directly;
10. which parts of this metamodel should eventually receive formal proofs.
