---
axiopra:
  schema_version: "0.1.0"
  id: axp.auditor.llm
  kind: architecture
  title: AXIOPRA Semantic LLM Auditor
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  owner: AXIOPRA maintainers
  language: en
  summary: Vendor-neutral semantic audit role for ambiguity, contradictions, omissions, reasoning gaps, and cognitive synchronization.
  tags:
    - llm
    - semantic-audit
    - agents
  depends_on:
    - axp.metamodel.core
    - axp.verification.trust-model
    - axp.verifier.rust-core
  relations:
    - type: references
      target: axp.agents.guide
    - type: constrained-by
      target: axp.verification.trust-model
    - type: uses
      target: axp.metamodel.core
  claims: []
  assumptions:
    - id: A-001
      statement: LLMs can provide useful semantic critique when supplied with a relevant, versioned artifact subgraph and required to cite evidence.
      status: active
  constraints:
    - id: K-001
      statement: LLM findings are review candidates and must not be labeled mathematical proof.
      status: active
    - id: K-002
      statement: Provider adapters must not own canonical project meaning.
      status: active
  human_outcome: The reader understands the auditor's role, required evidence, write boundaries, and probabilistic limitations.
  machine_outcome: Agent adapters have a common semantic-audit contract independent of provider prompts.
  verification:
    structural: required
    semantic: required
    human_review: required
    empirical: required
    formal: not-required
    notes: Auditor quality must be evaluated with seeded contradictions, omissions, and independent human review.
  review:
    cadence_days: 60
    required_roles:
      - semantic-audit-reviewer
      - human-experience-reviewer
      - security-reviewer
    expiry_behavior: warn
  supersedes: []
  external_references: []
---

# AXIOPRA Semantic LLM Auditor

## Purpose

The LLM auditor examines meaning that deterministic schemas and graph algorithms cannot fully capture. It searches for candidate ambiguity, omissions, incompatible claims, terminology drift, unsupported conclusions, and breaks in the user's mental continuity.

It is an independent critic, not an oracle and not the owner of project intent.

## Required input package

The auditor should receive a bounded, versioned package containing:

- repository revision;
- conformance and risk profile;
- current objective and lifecycle stage;
- relevant artifact subgraph;
- authoritative definitions;
- claims, assumptions, constraints, and evidence;
- recent accepted decisions;
- deterministic diagnostics;
- explicit audit questions;
- context-window omissions and retrieval limits.

The system should retrieve the smallest coherent subgraph rather than dump an uncontrolled repository into a prompt.

## Required finding format

```yaml
finding_id: <stable review-local id>
category: ambiguity | omission | contradiction | unsupported-claim | terminology-drift | traceability-gap | cognitive-desync
severity: info | warning | error | critical
artifacts: []
source_locations: []
observed_evidence: <what the repository actually says>
inference: <why this may be a problem>
consequence: <what downstream decision or artifact may be affected>
confidence: low | medium | high
questions: []
remediation_options: []
verification_needed: []
```

Confidence is the model's qualitative self-report, not calibrated probability unless a separate evaluation establishes calibration.

## Audit modes

- **Stage audit** — checks whether one stage answers its declared questions and gate.
- **Cross-stage audit** — follows promises, requirements, models, contracts, implementation, and evidence.
- **Terminology audit** — detects duplicate, conflicting, or drifting definitions.
- **Decision audit** — checks whether alternatives, consequences, and supersession are represented.
- **Assurance audit** — checks whether evidence claims exceed scope.
- **Cognitive audit** — checks whether the context compass and visible results still let the user explain the project.
- **Change-impact audit** — examines downstream artifacts after a proposed change.
- **Independent re-audit** — uses a different model, prompt family, or reviewer to reduce correlated failure.

## Write boundary

By default, the auditor is read-only. It may propose:

- a finding artifact;
- questions for the human;
- a patch or change set;
- new or corrected relations;
- a test, experiment, or review request;
- an RFC draft.

Accepted or canonical artifacts change only through an explicit, reviewable write action. The auditor must not silently “fix” intent to remove a contradiction.

## Provider neutrality

ChatGPT, Claude Code, Codex, local models, and future systems should interact through a shared AXIOPRA package and result contract.

Provider-specific adapters may optimize retrieval, tool calls, caching, or user interface. They must preserve:

- artifact IDs and versions;
- provenance;
- exact repository revision;
- permissions;
- diagnostic semantics;
- human approval boundaries;
- model and adapter identity;
- uncertainty and incomplete-context disclosure.

## Evaluation plan

The auditor will be evaluated with repositories containing intentionally seeded:

- direct contradictions;
- subtle unit and scope conflicts;
- missing acceptance paths;
- unsupported confidence claims;
- terminology drift;
- circular reasoning;
- stale artifacts;
- false positives caused by legitimate scoped alternatives;
- sessions where the technical output advances while the human context compass becomes stale.

Metrics must include precision, recall within the seeded set, explanation usefulness, false-alarm burden, provenance accuracy, and human-review agreement. No metric alone establishes semantic completeness.
