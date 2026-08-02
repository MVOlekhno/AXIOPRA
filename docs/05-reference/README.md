---
axiopra:
  id: AXP-REF-GUIDE
  kind: reference.guide
  version: 0.1.0
  status: active
  stage: AXP-STAGE-10
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Policy and entry point for reference projects that validate AXIOPRA in practice.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-MTH-STAGES, AXP-VER-MODEL]
    produces: [AXP-REF-ROADCORE]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003]
    semantic: [AXP-SEM-003, AXP-SEM-005, AXP-SEM-008]
  learning:
    external: A repeatable contract for turning methodology claims into worked evidence.
    internal: The reader can distinguish a decorative example from a reference project that can challenge the canon.
---

# Reference Projects

Reference projects are executable arguments about the usefulness and limits of AXIOPRA. They must expose the complete path from intent to evidence, include mistakes and revisions, and be capable of falsifying methodology claims.

A reference project must:

1. represent a real or credible domain problem;
2. stay small enough for end-to-end traceability;
3. use canonical artifact metadata;
4. record visible and learning results at every stage;
5. include positive, negative, boundary, and uncertainty cases;
6. exercise the deterministic verifier and LLM audit;
7. use formal proof only for a justified proposition;
8. publish lessons and proposed RFCs without silently changing the canon.

The first reference project is [`roadcore-drainage-validator/README.md`](roadcore-drainage-validator/README.md).
