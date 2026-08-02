---
axiopra:
  id: AXP-FND-README
  kind: foundation.guide
  version: 0.1.0
  status: active
  stage: AXP-STAGE-00
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Entry guide to the AXIOPRA Foundation and its quality gate.
  relations:
    depends_on: []
    produces: [AXP-FND-MANIFESTO, AXP-FND-CONSTITUTION]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002]
    semantic: [AXP-SEM-001, AXP-SEM-008]
  learning:
    external: A map of the stable Foundation artifacts.
    internal: The reader can explain why AXIOPRA begins with knowledge rather than code.
---

# Foundation

## Why this stage exists

The Foundation fixes the minimum stable laws from which the metamodel, methodology, verifier, SDK, AI adapters, and reference projects must derive. It prevents the platform from becoming a fashionable collection of unrelated techniques.

## Primary question

**What must remain true while AXIOPRA evolves?**

## What belongs here

- mission, vision, and non-goals;
- constitutional rules;
- definitions of knowledge, artifact, traceability, evidence, and verification;
- governance of canonical change;
- human-centered laws: visible progress, uncertainty reduction, and cognitive synchronization.

Implementation choices and speculative features do not belong in the canon unless they are required by a constitutional rule.

## Required outputs

1. [`manifesto.md`](manifesto.md) — why AXIOPRA exists.
2. [`constitution.md`](constitution.md) — binding rules and amendment process.
3. A machine entry point in [`../../axiopra.yaml`](../../axiopra.yaml).
4. Explicit handoff to the artifact metamodel.

## Questions the reader must ask

1. What human failure does this platform prevent?
2. Why is code not the primary source of truth?
3. What exactly counts as engineering knowledge?
4. Which decisions must remain human-accountable?
5. How does each stage reduce uncertainty?
6. How does the platform prevent an AI agent from outrunning the user's understanding?
7. What is checked deterministically, semantically, formally, and manually?
8. Which rules are universal and which are adjustable by project risk?
9. How can project experience improve the methodology without silently corrupting the canon?
10. What evidence would prove that the Foundation is wrong or incomplete?

## Visible result

A reader can draw the platform layers and explain the reason for every layer without discussing implementation details.

## Definition of done

The stage passes when the manifesto and constitution are mutually consistent, every binding rule has a downstream realization path, unresolved hypotheses are labelled, and changes to the canon require an RFC.

## Handoff

The next question is: **What is the smallest machine-checkable unit of engineering knowledge?** That question is answered by the metamodel.
