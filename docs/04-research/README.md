---
axiopra:
  id: AXP-RSH-GUIDE
  kind: research.guide
  version: 0.1.0
  status: active
  stage: AXP-STAGE-10
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Evidence and industry-case policy for every AXIOPRA methodology stage.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-MTH-STAGES]
    informs: [AXP-FND-MANIFESTO]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002]
    semantic: [AXP-SEM-003, AXP-SEM-005]
  learning:
    external: A repeatable structure for histories, cases, benefits, failures, critiques, and adoption decisions.
    internal: The reader can distinguish evidence-backed practice from attractive but untested opinion.
---

# Research and Evidence Layer

Every methodology stage must eventually have an evidence dossier. AXIOPRA will not copy industry practices merely because they are famous.

Each dossier must cover:

1. origin and historical problem;
2. primary sources and important later developments;
3. real organizations or projects that used the approach;
4. reported benefits and the evidence quality behind them;
5. reported limitations, failures, and criticism;
6. common misuse and anti-patterns;
7. how practitioners corrected or mitigated problems;
8. alternatives and contexts where another approach is better;
9. what AXIOPRA adopts, adapts, rejects, or leaves experimental;
10. date of last review and triggers for reassessment.

## Epistemic labels

- **Established:** supported by strong primary evidence or broad reproducible practice.
- **Supported:** credible evidence exists but scope is limited.
- **Informed judgment:** reasoned engineering choice with incomplete evidence.
- **Hypothesis:** proposed for testing in reference projects.
- **Unknown:** insufficient information; no confident claim permitted.

## Source policy

Prefer primary papers, official technical reports, standards, repositories, and direct postmortems. Secondary summaries may orient the reader but may not carry a critical claim alone. Record publication date, access date, claim supported, and known conflict of interest.

## Integrity rule

A case study must not claim causation from correlation, hide negative outcomes, or present marketing material as independent evidence. When reliable sources disagree, represent the disagreement.

The reusable dossier template is [`../../templates/stage-evidence.md`](../../templates/stage-evidence.md).
