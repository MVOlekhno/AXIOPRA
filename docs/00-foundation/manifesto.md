---
axiopra:
  id: AXP-FND-MANIFESTO
  kind: foundation.manifesto
  version: 0.1.0
  status: active
  stage: AXP-STAGE-00
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: The purpose, promise, and boundaries of AXIOPRA.
  relations:
    depends_on: [AXP-FND-README]
    produces: [AXP-FND-CONSTITUTION, AXP-MM-ARTIFACT]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-001, AXP-SEM-006, AXP-SEM-008]
  learning:
    external: A concise public statement of the platform's purpose.
    internal: The reader can distinguish AXIOPRA from a code generator or document workflow.
---

# AXIOPRA Manifesto

## Mission

AXIOPRA helps a person turn an uncertain intention into a coherent, traceable, verifiable, and evolvable engineering system without surrendering understanding to tools or AI agents.

## Vision

A beginner should be able to state, “I want to create a small graphic editor,” enter AXIOPRA, and see a comprehensible path from vague desire to user value, domain model, specifications, contracts, types, architecture, implementation, tests, proofs where justified, release, and learning.

The platform succeeds when the user does not merely obtain files and code, but acquires the mental structure needed to explain and govern the system.

## Theses

### 1. Understanding precedes implementation

Code is a compiled consequence of engineering knowledge, not the origin of that knowledge.

### 2. A project is a knowledge graph

Requirements, terms, decisions, constraints, contracts, tests, proofs, code, evidence, and lessons are typed nodes connected by explicit relations.

### 3. Every artifact serves humans and machines

Narrative explains meaning. Structured metadata enables deterministic inspection. Neither layer may silently contradict the other.

### 4. Every stage must be visible

The user must always see the current objective, position, change, reason, verification state, uncertainty, and next meaningful step.

### 5. Every stage changes both project and person

A completed stage creates an external artifact and an internal increase in understanding. More files with less understanding is failure.

### 6. Trust is plural

Structural verification, semantic audit, formal proof, empirical testing, and human judgment cover different failure modes. No single technique is universal.

### 7. Rigor follows risk

Small experiments should remain light. Safety-critical claims demand stronger contracts, evidence, tests, and selective proof. Traceability and honesty are never optional.

### 8. Evolution is recursive but controlled

Projects produce experience; experience may improve the methodology. Canon changes only through evidence, an RFC, reference validation, review, and versioned adoption.

### 9. The platform is vendor-neutral

Essential knowledge must remain portable across ChatGPT, Claude Code, Codex, future agents, and non-AI tools.

### 10. The platform must reproduce its way of thinking

An unfamiliar user should be able to download it, follow it, understand each step, and obtain a reproducible result without access to its original authors.

## What AXIOPRA does not promise

It does not promise automatic truth, universal formal proof, replacement of domain experts, perfect requirements, or effortless software. It promises a disciplined way to expose uncertainty, connect decisions, verify what can be verified, and keep the human in command.
