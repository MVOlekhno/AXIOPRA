---
axiopra:
  id: AXP-VER-RUST
  kind: verification.rust-verifier
  version: 0.1.0
  status: review
  stage: AXP-STAGE-06
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Deterministic Rust compiler and verifier boundary, MVP pipeline, crate split, diagnostics, and explicit non-goals.
  relations:
    depends_on: [AXP-MM-ARTIFACT, AXP-MM-RELATION, AXP-VER-MODEL, AXP-VER-TRUST, AXP-VER-RULESET]
    realizes: [AXP-VER-MODEL]
    verifies: [AXP-MM-ARTIFACT, AXP-MM-RELATION]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003, AXP-RULE-005]
    semantic: [AXP-SEM-001, AXP-SEM-005, AXP-SEM-007]
  learning:
    external: An implementable minimum architecture for compiling repository artifacts into Engineering IR and deterministic diagnostics.
    internal: The reader can explain exactly what the first Rust verifier will check and which questions remain outside its authority.
---

# Deterministic Rust Verifier

## Purpose

The Rust verifier is AXIOPRA's cold, repeatable layer. It parses canonical sources, normalizes them into Engineering IR, evaluates versioned structural rules, and reports precise diagnostics.

It must remain useful offline and must not require an LLM, proprietary service, or network connection for core validation.

## MVP pipeline

```text
repository discovery
  -> Markdown and YAML-front-matter parsing
  -> JSON Schema validation
  -> source-span index
  -> artifact symbol table
  -> relation resolution
  -> typed directed multigraph
  -> lifecycle and stage rules
  -> traceability profile rules
  -> diagnostics
  -> JSON IR and generated graph views
```

## Planned crate boundaries

- `axiopra-model` — identifiers, stages, lifecycle, relations, learning outcomes, and Engineering IR types.
- `axiopra-parser` — discovery, Markdown/front-matter parsing, and source spans.
- `axiopra-schema` — JSON Schema loading and local metadata validation.
- `axiopra-graph` — typed graph, traversal, cycles, traceability, and impact analysis.
- `axiopra-rules` — versioned deterministic rules and conformance profiles.
- `axiopra-diagnostics` — stable IDs, severities, explanation, source location, and renderers.
- `axiopra-verifier` — orchestration library.
- `axiopra-cli` — command-line and CI entry point.
- `axiopra-sdk` — public API only after the internal model survives reference-project use.

These names are architectural candidates, not a commitment to publish separate crates immediately.

## Initial CLI surface

```text
axiopra init
axiopra scan
axiopra check
axiopra graph
axiopra status
axiopra explain <diagnostic-id>
```

### `axiopra scan`

Discovers candidate artifacts and reports ignored, malformed, duplicate, or unclassified files without applying the full project profile.

### `axiopra check`

Builds Engineering IR and evaluates the selected schema, rule set, and conformance profile.

### `axiopra graph`

Exports derived JSON and Mermaid views. Generated views are reproducible outputs, never manually edited sources of truth.

### `axiopra status`

Reports stage state, verification profile, unresolved findings, and context-compass inputs without inventing absent facts.

### `axiopra explain`

Shows the governing rule, affected artifacts, actual and expected state, consequences, and safe remediation options.

## MVP checks

1. Repository entry points and declared paths exist.
2. Canonical artifact front matter validates against the declared schema.
3. IDs are valid and unique.
4. Every internal relation target resolves exactly once.
5. Unknown relation keys fail explicitly.
6. Forbidden self-loops and dependency cycles are absent.
7. Status and confidence values are valid and treated as independent dimensions.
8. Declared stage prerequisites are satisfied for active artifacts.
9. Active artifacts have external and internal learning outcomes.
10. Active requirement paths satisfy the selected profile or contain an explicit waiver.
11. Supersession is acyclic and preserves migration information.
12. Generated graph output is reproducible for the same revision and verifier version.

## Diagnostic contract

A diagnostic uses a stable rule ID and includes:

```yaml
rule_id: AXP-RULE-003
severity: error
message: Relation target does not resolve exactly once.
source:
  path: <path>
  line: <line>
  column: <column>
artifacts: []
actual: <observed state>
expected: <required state>
why_it_matters: <engineering consequence>
remediation: []
auto_fix: safe | review-required | unavailable
```

Human text, JSON, and future SARIF output must represent the same underlying diagnostic rather than recomputing different meanings.

## Engineering rules

1. Errors are values; malformed user input must not cause an uncontrolled panic.
2. Equivalent inputs, configuration, and verifier version produce equivalent results.
3. Rule meaning is versioned independently from presentation.
4. Source spans survive normalization so findings remain actionable.
5. The IR remains serializable and inspectable.
6. Core semantics never live only inside a prompt.
7. Automatic repairs are opt-in and produce a reviewable change set.
8. Performance optimization must not erase explanation traces.
9. Unsafe Rust requires an accepted decision, stated invariant, test strategy, and review.
10. Parsing, graph construction, rule evaluation, and rendering remain independently testable.
11. Network access is off by default in deterministic checks.
12. Path handling and output remain portable across supported operating systems.

## Verification of the verifier

The MVP must include:

- valid fixtures accepted by the expected profile;
- invalid fixtures for each rule;
- expected diagnostic IDs and source locations;
- property tests for identifiers, relation resolution, and graph transformations;
- deterministic snapshot tests for normalized IR and reports;
- mutation or fault-seeding experiments where useful;
- checks that the repository validates itself;
- documented limitations and unsupported syntax.

A verifier pass is meaningful only after the verifier itself has executable evidence appropriate to the rule.

## Explicit non-goals

The first verifier does not:

- decide whether a product should exist;
- infer all semantics from prose;
- replace domain review;
- generate a complete production application;
- assign a universal trust score;
- prove the whole repository correct;
- embed Prolog, Datalog, Lean, or one LLM provider;
- silently modify canonical artifacts.

## Evolution toward the Engineering Knowledge Compiler

After the verifier succeeds on AXIOPRA itself and the RoadCore reference project, the same IR may support:

- change-impact reports;
- traceability matrices;
- graph and cognition views;
- test and property-test scaffolds;
- proof obligations;
- agent context packages;
- migration plans;
- typed code scaffolds;
- domain-specific projections or DSLs.

Every generated artifact must retain provenance and remain subordinate to accepted intent.
