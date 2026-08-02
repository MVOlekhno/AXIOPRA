---
axiopra:
  schema_version: "0.1.0"
  id: axp.platform
  kind: vision
  title: AXIOPRA Project Identity
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  owner: MVOlekhno
  language: en
  summary: Canonical identity, mission boundary, scope, and current lifecycle state of the AXIOPRA platform.
  tags:
    - foundation
    - project-identity
  depends_on: []
  relations:
    - type: motivates
      target: axp.foundation.manifesto
    - type: organizes
      target: axp.foundation.index
  claims:
    - id: C-001
      statement: AXIOPRA is intended to transform uncertain intent into traceable and verifiable engineering knowledge while preserving human understanding.
      evidence_class: hypothesis
      confidence: specified
      evidence:
        - Foundation Baseline Revision 1
  assumptions:
    - id: A-001
      statement: Explicit artifact graphs and independent verification layers can improve engineering continuity in human-AI workflows.
      scope: Initial hypothesis to be tested through verifier implementation and reference projects.
      status: active
  constraints:
    - id: K-001
      statement: The canonical knowledge model must remain independent of one LLM vendor.
      status: active
    - id: K-002
      statement: Rust is the default production language for core tooling unless governance accepts a justified exception.
      status: active
  human_outcome: The reader can identify what AXIOPRA is, its present status, and the boundary between vision and demonstrated capability.
  machine_outcome: The project has a resolvable root artifact from which canonical foundation artifacts can be discovered.
  verification:
    structural: required
    semantic: required
    human_review: required
    domain_review: not-required
    empirical: recommended
    formal: not-required
    notes: The vision is a governed hypothesis until reference projects and user studies provide evidence.
  review:
    cadence_days: 90
    required_roles:
      - maintainer
      - human-experience-reviewer
    expiry_behavior: warn
  supersedes: []
  external_references: []
---

# AXIOPRA Project Identity

## Name

**AXIOPRA**

The name combines the ideas of **axiom** and **praxis**: a disciplined movement from explicit foundations to working practice.

## Mission

Enable people and AI agents to turn uncertain intent into coherent, traceable, testable, and responsibly verified engineering systems without allowing the human operator to lose understanding or control.

## Product category

AXIOPRA is planned as an open engineering-thought operating system consisting of:

- a methodology and self-explaining artifact library;
- a versioned knowledge-graph metamodel;
- a deterministic compiler/verifier implemented primarily in Rust;
- guided beginner and expert workflows;
- a vendor-neutral SDK and protocol;
- adapters for AI coding and review environments;
- research and optional logic/proof layers;
- reference projects that test the methodology in practice.

## Current status

- Release status: **pre-alpha**.
- Current phase: **Foundation bootstrap**.
- Foundation maturity: **hypothesis frozen for the first implementation cycle**.
- Production readiness: **none**.
- Public compatibility commitment: **not yet declared**.

## Primary users

Initial user groups:

1. a first-time builder who has an idea but no software-engineering process;
2. an experienced developer using long-running AI agents who needs traceability and cognitive continuity;
3. a domain engineer translating professional knowledge into software;
4. an engineering team that needs reviewable links from intent to evidence;
5. a researcher exploring typed knowledge graphs, logic rules, or formal verification.

## Promise

AXIOPRA should make the next engineering question visible, explain why it matters, produce an inspectable result at every stage, maintain a context compass, and report exactly which properties have and have not been checked.

## Boundary of the promise

AXIOPRA does not make an inexperienced person a qualified domain expert, does not prove all documentation or code correct, and does not remove accountability. It makes missing knowledge, assumptions, contradictions, dependencies, evidence, and required expertise visible earlier.

## First validation targets

1. The repository can describe and validate its own canonical artifacts.
2. A beginner can develop a minimal graphical-editor concept without losing the purpose of each stage.
3. A practicing civil engineer can apply the lifecycle to RoadCore Drainage Validator.
4. Two different AI environments can consume the same graph without owning its meaning.
5. Selected structural and domain properties can be checked by deterministic and formal tools without overstating assurance.
