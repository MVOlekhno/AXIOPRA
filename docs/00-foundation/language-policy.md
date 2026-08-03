---
axiopra:
  id: AXP-FND-LANGUAGE
  kind: foundation.language-policy
  version: 0.1.0
  status: active
  stage: AXP-STAGE-00
  language: en
  confidence: provisional
  owners: [MVOlekhno]
  summary: Canonical-language, Russian-localization, drift-control, and release rules for AXIOPRA documentation.
  relations:
    depends_on: [AXP-FND-CONSTITUTION, AXP-RFC-0001]
    constrains: [AXP-MTH-STAGES, AXP-VER-MODEL, AXP-RSH-GUIDE]
    realizes: [AXP-FND-CONSTITUTION]
  verification:
    structural: [AXP-RULE-001, AXP-RULE-002, AXP-RULE-003, AXP-RULE-009]
    semantic: [AXP-SEM-002, AXP-SEM-004, AXP-SEM-008]
  learning:
    external: A single-source localization model that gives Russian users a complete path without creating a second canon.
    internal: The reader can explain how AXIOPRA remains bilingual while preventing semantic drift between English and Russian documents.
---

# Language and Russian Localization Policy

## Why this policy exists

AXIOPRA is intended for international use, while its founder and first reference domain work primarily in Russian. A Russian user must be able to understand the full engineering path without translating every document manually. At the same time, two independently editable normative versions would eventually contradict each other.

The platform therefore combines broad language access with one semantic source of truth.

## Primary decision

1. **English is the canonical language of platform artifacts.**
2. **Russian is a required first-class localization for user-facing platform documentation.**
3. A Russian document is a synchronized translation, not an independent canonical artifact.
4. If the two versions disagree, the English canonical artifact governs until the defect is corrected.
5. An ambiguity discovered during translation must be fixed in the canonical source first and then translated again.

This decision does not make English culturally or intellectually superior. It provides one stable semantic authority for a global, machine-readable project.

## File convention

For a canonical file:

```text
docs/path/document.md
```

the Russian translation is:

```text
docs/path/document.ru.md
```

Root entry points may use established names such as `README.md` and `README.ru.md`.

## Translation metadata

Every localized document under `docs/` or `rfcs/` begins with a `translation` YAML block validated by [`../../schemas/translation.schema.json`](../../schemas/translation.schema.json). It declares:

- locale;
- canonical source path;
- canonical source artifact ID;
- canonical source version;
- synchronization status;
- translation method;
- human review evidence when synchronized.

Translation files are excluded from canonical artifact discovery. They do not receive independent artifact IDs and do not create duplicate graph nodes.

## Translation states

- `draft`: incomplete or newly generated translation;
- `review`: complete enough for human linguistic and semantic review;
- `synchronized`: reviewed and aligned with the declared source version;
- `stale`: the canonical source changed or a known divergence exists.

A translation may not claim `synchronized` without an identified human reviewer and review date.

## Required coverage

Russian localization is required for:

- human entry points;
- Foundation, metamodel, methodology, verification, research, governance, and roadmap guides;
- artifact, RFC, evidence, and project templates intended for end users;
- beginner tutorials and reference-project explanations;
- CLI help and diagnostics before the first public alpha intended for Russian users.

Source code identifiers, artifact IDs, file names, commands, JSON/YAML keys, Rust types, Lean propositions, and protocol fields remain unchanged unless an explicit localization layer is defined.

## Same-change rule

When a user-facing canonical document changes, the same pull request must do one of the following:

1. update its Russian translation and declare the matching source version;
2. mark the Russian translation `stale` and create a blocking localization task;
3. document why the artifact is exempt from localization.

Silent drift is forbidden. During the current pre-alpha migration, incomplete historical coverage is tracked explicitly and blocks the first public alpha, not every intermediate commit.

## Semantic fidelity rules

A translation must preserve:

- obligation strength: `must`, `must not`, `should`, `may`;
- scope, assumptions, exceptions, and non-goals;
- evidence and confidence labels;
- distinction between fact, inference, decision, hypothesis, and unknown;
- artifact IDs, relation direction, rule IDs, commands, paths, and code;
- warnings about what a verifier or proof cannot establish.

A translation may improve readability for Russian users, but it may not add a new requirement, promise, exception, or interpretation.

## Agent requirements

An AI agent must:

- read the canonical source before editing a translation;
- update English semantics first when meaning changes;
- produce Russian text in clear professional language rather than literal word substitution;
- preserve technical identifiers exactly;
- declare LLM assistance in translation metadata;
- never mark its own translation synchronized without human review;
- report suspected ambiguity instead of silently choosing a convenient meaning.

## Planned deterministic checks

The Rust verifier will eventually check:

- required translation pair existence;
- translation metadata schema;
- source path and artifact resolution;
- source-version equality;
- stale status after canonical changes;
- release-profile coverage;
- broken links and untranslated placeholders.

These checks establish synchronization metadata and coverage. They do not prove linguistic or semantic quality; that still requires semantic and human review.

## Release gate

The first public alpha intended for Russian users requires:

- complete required RU coverage;
- no required translation in `draft`, `review`, or `stale` state;
- recorded human review;
- successful structural localization checks;
- semantic spot checks of high-risk normative documents.

## Visible result

A Russian-speaking beginner can traverse AXIOPRA from the root README through Foundation, metamodel, lifecycle, verification, roadmap, and examples without losing the canonical trace.

## Quality gate

This policy passes when the repository has one canonical semantic graph, Russian translations point to exact source artifacts and versions, drift is visible, and release cannot present stale localized rules as current truth.
