---
axiopra:
  id: AXP-VER-MODEL
  kind: verification.model
  version: 0.1.0
  status: active
  stage: AXP-STAGE-08
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Independent structural, semantic, formal, empirical, and human verification layers.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-MM-ARTIFACT, AXP-MM-RELATION, AXP-MTH-STAGES]
    verifies: [AXP-FND-CONSTITUTION]
    produces: [AXP-VER-RULESET, AXP-VER-TRUST, AXP-VER-RUST, AXP-VER-LLM]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-002, AXP-SEM-003, AXP-SEM-006]
  learning:
    external: A clear allocation of failure modes to independent checking mechanisms.
    internal: The reader can explain what each verifier can and cannot establish.
---

# Verification Model

AXIOPRA does not collapse trust into one misleading score. It reports a **verification profile** whose dimensions remain separate.

## Detailed contracts

- [`trust-boundaries.md`](trust-boundaries.md) — exact assurance scope, evidence records, contradiction classes, and correlated-failure rules.
- [`rust-verifier.md`](rust-verifier.md) — deterministic compiler/verifier MVP and diagnostics contract.
- [`llm-auditor.md`](llm-auditor.md) — vendor-neutral semantic audit package, finding format, permissions, and evaluation plan.
- [`rules.md`](rules.md) — initial deterministic and semantic rule registry.
- [`../../proofs/README.md`](../../proofs/README.md) — selective Lean proof boundary.

These artifacts refine this overview. They do not create additional trust dimensions or merge independent evidence into one score.

## Layer 1 — Deterministic structural verifier

The core verifier will be written in Rust. Its planned CLI entry point is:

```text
axiopra check
```

The first implementation checks:

- required files and entry points;
- YAML front matter against JSON Schema;
- identifier uniqueness and format;
- relation target resolution;
- forbidden self-loops and cycles;
- lifecycle transitions;
- stage prerequisites;
- unresolved placeholders in active artifacts;
- required visible and learning outcomes;
- traceability from promises to implementation and verification;
- reproducible graph generation.

Planned outputs are human text, JSON, SARIF for code-hosting integration, and Mermaid/JSON graph views.

## Initial structural rule identifiers

- `AXP-RULE-001`: canonical Markdown artifact contains valid AXIOPRA front matter.
- `AXP-RULE-002`: artifact ID is valid and unique.
- `AXP-RULE-003`: every internal relation target resolves exactly once.
- `AXP-RULE-004`: lifecycle state and confidence are valid and independent.
- `AXP-RULE-005`: forbidden graph cycles and self-loops are absent.
- `AXP-RULE-006`: declared stage prerequisites and gates are satisfied.
- `AXP-RULE-007`: active requirements have implementation and verification paths or an explicit waiver.
- `AXP-RULE-008`: active artifacts contain no meaning-changing placeholders.
- `AXP-RULE-009`: referenced paths and schemas exist.
- `AXP-RULE-010`: generated graph and traceability reports are reproducible.
- `AXP-RULE-011`: supersession preserves history and migration.
- `AXP-RULE-012`: every stage artifact declares external and internal outcomes.

## Layer 2 — LLM semantic auditor

The LLM checks meaning that static rules cannot reliably determine: contradiction, ambiguity, unsupported reasoning, terminology drift, missing alternatives, mismatch between promise and specification, and loss of human understanding.

Initial semantic check identifiers:

- `AXP-SEM-001`: one clear primary purpose and question.
- `AXP-SEM-002`: no unresolved contradiction with related active artifacts.
- `AXP-SEM-003`: claims distinguish evidence, inference, assumption, decision, hypothesis, and unknown.
- `AXP-SEM-004`: terminology remains consistent within declared contexts.
- `AXP-SEM-005`: alternatives, consequences, and falsification conditions are honest.
- `AXP-SEM-006`: user value remains traceable through downstream artifacts.
- `AXP-SEM-007`: boundaries and failure modes are explicit.
- `AXP-SEM-008`: the artifact demonstrably reduces uncertainty and increases explainability.

LLM findings are advisory until reviewed. A model must not claim a deterministic pass unless the Rust verifier ran.

## Layer 3 — Empirical verification

Tests, simulations, experiments, reference projects, operational observations, and user outcomes establish behaviour in declared environments. Empirical success does not prove universal correctness.

## Layer 4 — Selective formal verification

Lean is the default proof assistant for critical propositions. Proof scope, assumptions, abstraction gap, and correspondence to Rust implementation must be explicit. Idris, Haskell, Prolog, and other tools may be used as research or plugin layers through RFCs.

## Layer 5 — Human accountability

Humans approve intent, domain truth, ethical boundaries, risk acceptance, trade-offs, and release. Tools provide evidence; they do not inherit accountability.

## Verifier architecture direction

The planned Rust workspace will separate parsing, schema validation, graph construction, rule evaluation, reporting, CLI, and SDK APIs. The same Engineering IR should serve the CLI, agents, visualization, plugins, and future code generation.
