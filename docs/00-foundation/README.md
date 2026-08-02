---
axiopra:
  schema_version: "0.1.0"
  id: axp.foundation.index
  kind: guide
  title: Foundation Stage Guide
  version: "0.1.0"
  status: draft
  maturity: hypothesis
  canonical: true
  depends_on:
    - axp.platform
  relations:
    - type: organizes
      target: axp.foundation.manifesto
    - type: organizes
      target: axp.foundation.constitution
    - type: organizes
      target: axp.foundation.governance
  human_outcome: The reader can explain what AXIOPRA is, why it exists, and which rules cannot be bypassed silently.
  machine_outcome: The canonical foundation documents and their dependencies are discoverable from one entry point.
  verification:
    structural: required
    semantic: required
    human_review: required
---

# Foundation

## Why this stage exists

The Foundation defines the stable reasoning boundary of AXIOPRA before tools, schemas, user interfaces, or code begin to shape the project accidentally. It prevents the platform from becoming a fashionable collection of techniques without a coherent purpose.

The Foundation is deliberately small. It states what the system exists to accomplish, what it refuses to sacrifice, how knowledge becomes trusted, and how the canon may change.

## Main question

> What must remain true about AXIOPRA even when its implementation, users, AI models, and surrounding technologies change?

## What this stage must answer

1. Who is AXIOPRA for?
2. What uncertainty does it reduce?
3. What is the primary product: code, documents, or shared engineering understanding?
4. What responsibilities remain with the human?
5. What may deterministic software verify?
6. What may an LLM audit, and what may it not claim?
7. When is formal proof justified?
8. How does every stage preserve the user's understanding?
9. How does project experience improve the methodology without allowing uncontrolled self-modification?
10. Which decisions are canonical, and how can they be challenged or replaced?

## Required outputs

| Artifact | Purpose |
|---|---|
| `MANIFESTO.md` | Mission, vision, values, and concise laws of the platform. |
| `CONSTITUTION.md` | Normative MUST/SHOULD/MAY rules and trust boundaries. |
| `GOVERNANCE.md` | RFC process, evidence path, versioning, and controlled evolution. |
| `README.md` | This stage's navigation, questions, outputs, and quality gate. |

## Visible result for the user

After this stage, the user can open one folder and see:

- why the platform exists;
- what it promises;
- what it does not promise;
- how human, deterministic, probabilistic, and formal checks differ;
- how future changes are accepted or rejected.

## Cognitive result for the user

The user should be able to say, in their own words:

> AXIOPRA turns an uncertain idea into a graph of explicit engineering knowledge, keeps me synchronized with the process, and builds confidence through several independent kinds of verification rather than through blind trust in one tool.

## Ten self-reflection questions

Before declaring the Foundation understood, ask yourself:

1. Can I explain AXIOPRA without mentioning Rust, Lean, ChatGPT, or any other implementation tool?
2. Can I distinguish an artifact from an ordinary document?
3. Do I understand why a structurally valid graph may still contain false domain claims?
4. Can I name the knowledge for which a human remains accountable?
5. Can I explain why LLM agreement is not mathematical proof?
6. Can I explain why every stage must produce both a visible artifact and a change in understanding?
7. Do I know how an experiment differs from accepted canon?
8. Do I know what evidence is required before a recurring project lesson changes the methodology?
9. Can I identify a case where less ceremony is correct without abandoning traceability?
10. Can I state what AXIOPRA will refuse to do even when doing it would appear faster?

## Typical mistakes

- Treating the Foundation as marketing language rather than enforceable design constraints.
- Declaring principles “proven” before reference projects and empirical evidence exist.
- Encoding implementation preferences as eternal philosophical truths.
- Requiring maximum ceremony for low-risk experiments.
- Allowing an AI agent to reinterpret canonical terms silently.
- Adding principles indefinitely instead of freezing a testable baseline.

## Definition of Done

The Foundation stage is complete for a baseline revision when:

- all required artifacts exist and have stable IDs;
- terms are used consistently across the artifacts;
- normative rules do not contradict the manifesto;
- governance defines a reviewable path for changing canon;
- non-goals and trust boundaries are explicit;
- the stage passes structural validation when the verifier exists;
- at least one independent human review records unresolved objections;
- the baseline is frozen for implementation and may change only through governance.

## Handoff to the metamodel

The next stage answers:

> What exact kinds of engineering artifacts and relations are needed to express the promises and constraints established by the Foundation?
