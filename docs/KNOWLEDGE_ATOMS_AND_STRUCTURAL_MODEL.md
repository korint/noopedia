# Noopedia — Knowledge Atoms and Their Structural Model

## Scope and status

This document is an **initial conceptual specification** of a knowledge atom and the relationships required to reuse it across sources, times, perspectives, and forms of presentation. It consolidates principles already present in the semantic research and technical reference archive. It is **not** a new database schema, an API contract, a migration instruction, or evidence that all described capabilities work in the current codebase.

This initial model consolidates semantic and technical ideas; it does not claim to be an implemented storage schema. The research test for reusing such atoms to create new narratives is [TS001](RESEARCH_TESTS_AND_RESULTS.md).

## 1. What an atom is

A **knowledge atom** is a semantically distinguishable, source-grounded unit of meaning that can be evaluated, related to other units, and reused independently of the source's particular wording and exposition order. Its meaningful qualifiers are part of its content. An atom may express a claim about an object, relation, event, state, process, attribution, hypothesis, historical interpretation, or other source-supported semantic construction.

The word *atom* describes a **logical granularity of knowledge**; it does not entail that every statement becomes one physical row or that an atom is identical to a grammatical sentence, a word, a named entity, a standalone event, a subject–predicate–object triple, or any single SAS/CIN/SPP record. One sentence can support several atoms; several sentences may jointly establish one contextual interpretation; a single source span may support multiple distinct claims. Not every semantic role needs separate durable storage.

A candidate is suitably atomic when it can be meaningfully checked or disputed, has a distinct predicate/relationship with its arguments and relevant constraints, has recoverable source support, can be selected for a purpose independently of unrelated claims, and does not duplicate the meaning of another accepted candidate. The objective is **semantic completeness without artificial atom proliferation**.

### Non-examples

- A name mentioned near a verb is not automatically evidence that the named object performed the action.
- A template's unanswered question (*Who constructed it?*) is not a fact asserting that the constructor is unknown.
- A source's paragraph number or chronological position is not a permanent property of a world-level atom.
- A generated explanation, molecule, article, or visualization is not independent evidence for the source claims it reuses.
- An LLM's confident guess about a missing argument is not an atom extracted from the inspected source.

## 2. Three distinct semantic roles: SAS, CIN, SPP

| Role | Question it answers | Boundaries |
| --- | --- | --- |
| **SAS — Source Assertion** | What does this exact source version state, and which evidence span supports that reading? | Source-bound report, not world truth. |
| **CIN — Contextual Interpretation** | What does that assertion mean in context, including referents, semantic roles, time, negation, attribution, modality, and uncertainty? | Interpretation must be auditable and may remain unresolved or held. |
| **SPP — Normalized Proposition** | Can the supported meaning be represented comparably across sources, without changing its conditions or origin? | Equivalence and normalization require justification; normalization does not create independent evidence. |

The *atom* is a useful way to talk about an independently reusable piece of meaning that this chain may support. It **does not replace or collapse SAS/CIN/SPP**. A proposed logical atom view may reference one or more interpretations and source attestations. Multiple attestations can support the same normalized meaning; their common source lineage and possible dependence must still be retained. Some valid source assertions cannot yet become a safely resolved SPP; they remain candidates, not discarded or silently asserted as fact.

**Separate three evaluations:** semantic fidelity to the expression; entailment/support by the inspected source; and epistemic warrant for treating a proposition as knowledge about the world. Passing one does not imply passing the others.

## 3. Logical anatomy

The following is a **conceptual field inventory**, not a mandatory flat record and not a set of new database columns. Fields may be represented by existing identity, relation, attribute, qualifier, version, review, and evidence mechanisms. “As applicable” means an omitted field must not cause a semantic loss when the source expresses that distinction.

| Group | Conceptual contents | Required interpretive rule |
| --- | --- | --- |
| **Identity and referents** | Logical claim ID or candidate ID; subject and other arguments; referent identity, aliases, unresolved identity alternatives | Do not turn identical strings into identical entities; unresolved references remain unresolved. |
| **Predicate and semantic roles** | Relation/property/event/state; typed participants (agent, patient, instrument, recipient, location, occasion, etc.) | Predicate and direction are integral to meaning; not every verb creates an event node. |
| **Object or value** | Another referent, literal, measurement with unit, structured event, or bounded expression | Preserve type, unit, precision, and reference. |
| **Temporal and spatial scope** | Event time, validity interval, observation time, location and jurisdiction where meaningful | Publication and capture times are separate from when a claim is said to hold. |
| **Logical scope** | Polarity, quantifiers, conditions, exceptions, modality, uncertainty, negation scope | Never convert “may”, “if”, “not all”, or “before” into stronger or different claims. |
| **Attribution and perspective** | Speaker/author/institution, reported belief or interpretation, claim stance, historical or institutional lens | “A stated P” is not necessarily “P”. MPOV presentation does not change source truth. |
| **Source and evidence** | Document identity, exact version, permitted capture/representation, evidence spans, quoted text where allowed, SAS/CIN/SPP lineage | URL alone is not authenticated evidence; evidence links support traceability, not automatic truth. |
| **Origin and dependency** | Independent-origin family where supportable, quotation/derivation links, support/contradiction/supersession edges | Several citations can have the same source origin; derivatives get no new independence credit. |
| **Review and eligibility** | Semantic support disposition, confidence or unresolved cause where applicable, acceptance/rejection/hold, publication eligibility | Do not use one all-purpose `verified` flag; scope each decision to its test and authority. |
| **Revision history** | Logical version/supersession, affected outputs, corrections, review decisions and evidence used | Do not overwrite previously supported historical states; updates trigger impacted output review. |

No universal permanent importance/rank or article position belongs in this anatomy. **Relevance, molecule grouping, and order are context-dependent assembly decisions.**

## 4. A non-normative logical example

The following fictional input is **invented test material**, not a claim about an existing organization. Imagine that a captured report says:

> “On 12 May 2040, the council announced that the library might reopen in June.”

One grounded interpretation is that *the council announced a possible reopening*. The source does **not** establish that the library reopened, nor an exact reopening date.

```yaml
# Illustrative TS001 fixture envelope — NOT a live Noopedia schema
fixture_atom_id: ATOM-001
meaning:
  subject: {ref: synthetic:council}
  predicate: announced_possible_event
  object:
    event: reopen
    patient: {ref: synthetic:library}
    possible_period: 2040-06
  time:
    statement_date: 2040-05-12
  polarity: positive
  modality: possible_reopening
  attribution: {ref: synthetic:council}
  unresolved: []
provenance:
  document_ref: SYNTH-DOC-1
  version_ref: SYNTH-VER-1
  evidence_refs: [SYNTH-SPAN-1]
  sas_refs: [SYNTH-SAS-1]
  cin_refs: [SYNTH-CIN-1]
  spp_refs: [] # none until safe normalized comparison is established
assessment:
  source_support: not_yet_reviewed
  world_warrant: not_assessed
  admission: candidate
```

These keys are *illustrations of logical information that must be accounted for*, not recommendations to instantiate them literally. In particular, possible future events may be represented as structured values, qualified propositions, or existing relations, depending on supported contracts. The `fixture_atom_id` is local to a test and does not establish canonical object identity.

If a second independent source later states that the library actually reopened on a specific date, that is **a new source-bound claim with different modality, time, and support**, not an automatic overwrite of the earlier report. A new explanatory article may describe both the announcement and the later outcome, if both are supported.

## 5. Atomization: boundary and stopping rule

Source-independent topic coverage means the extractor should identify **all distinct claims supported within the declared source scope**, including claims about secondary entities and relationships, rather than extracting only the article's title subject or available template slots. Discovery and admission are different operations; candidates blocked by unresolved identity, schema incompatibility, or weak evidence must be recorded as such instead of being silently dropped or misattributed.

A proposed atom passes the minimum semantic boundary only if reviewers can answer:

1. **What precisely is claimed?** Identify referents, predicate, arguments, polarity, modality, conditions, temporal scope, and attribution when relevant.
2. **Where does it come from?** Identify exact source version and genuine evidence, or explicitly mark what is unavailable.
3. **Does it follow from that source?** Test contextual entailment; a direct quotation match is insufficient if an interpretation changes the claim.
4. **Is it distinguishable and reusable?** Could it be checked or selected without an unrelated clause, and does an existing proposition already have the same full meaning?
5. **What remains unresolved?** Do not fill missing participants, references, or values from model memory.

Useful research labels **E0** (directly expressed) and **E1** (strictly entailed with anchored context) are analytical distinctions, not new DB states; plausible but unsupported hypotheses (**E2**) and external model knowledge (**E3**) are not source-extracted facts. Deepening extraction does not mean repeatedly generating variants until a desired quantity is reached.

## 6. Relations among atoms

A reusable corpus needs typed relationships, with clear distinctions between:

- **Semantic/world relations:** attributed event participation, before/after, necessary precondition, causation, containment, part–whole, and other relations *only where the evidence supports the claimed strength*.
- **Evidence relations:** supported by, reports, quotes, contradicts, updates, supersedes, overlaps, same-origin/derived-from. A contradiction requires comparable subject, scope, qualifiers, and time; mere disagreement in wording is insufficient.
- **Interpretive relations:** competing hypotheses, alternative interpretations, uncertainty, referent resolution candidates, historical intellectual influence, reported belief, and viewpoint applicability.
- **Composition-only relations:** selected for section, prerequisite for explanation, grouped in molecule, narrative transition, chosen output order. These are *not* permanent facts about the world.

Each derived relationship needs its own evidence or explicitly marked inference, assumptions and dependencies. Coincidence or adjacency in text does not justify a causal relation. The same atom can belong to different molecules without changing the atom or multiplying evidence.

## 7. Time, history and changing understanding

At minimum distinguish, when the material requires it: event/valid time; time a source reports or a person believes something; time of publication; acquisition/capture time; and Noopedia's assessment/revision time. These can differ. A historically influential false belief can be recorded as an **attributed historical belief**, not accepted as present world truth. History of a subject, history of understanding the subject, and editing history of a knowledge database are separate representational needs.

## 8. Original documents and citation linkage

The original is a separate authored artifact. It retains text order, literary form, attribution, rhetorical structure and edition history. Atomization does not guarantee lossless reconstruction. Preserve its stable identity, specific version, legitimate citation, evidence coordinates and, where rights permit, inspectable exact source. Do not fabricate missing captures, use a URL as proof of reading, or treat a citation of an unavailable original as independent evidence from that original.

A compiled sentence must be explainable as a selection or safe synthesis of eligible claims with links to the source version(s) that support its substance. If a statement relies on multiple propositions, record those dependencies; a generated article is not another independent source for them. See [Original Sources, Atomization, and Narrative Assembly](SOURCES_ATOMIZATION_AND_NARRATIVE_ASSEMBLY.md).

## 9. Missing knowledge and open questions

An applicable but unanswered question belongs to a scoped investigation or output view, **not to the world-fact layer as a fake negative or null-valued atom**. Distinguish: missing in a checked passage, missing in a defined corpus snapshot, contested, not applicable, and not assessed. A gap must identify its scope and why the question is applicable. Derived quantities require their formulas and source dependencies; they are not new independent attestations.

## 10. Atom-to-text composition

An output plan should be formed in this order, conceptually:

`request → output profile → eligible knowledge selection → coverage obligations → molecular grouping → dependency-aware narrative plan → prose → claim/evidence audit`.

An output template determines **what is relevant and how to present it**, not a permanent position property of an atom. It may require contrasting accounts or the history of understanding. Original source exposition order is not inherited; material temporal/logical/causal constraints remain. The selection plan and the prose must be separately auditable.

> **Knowledge must not inherit the source's order of exposition as an obligatory property of its own structure. Its representation should be formed according to purpose, context, and semantic relationships, while preserving those sequences and dependencies that are part of the meaning itself.**

## 11. Open structural questions to test before implementation

- Where exactly do qualifiers such as negation scope, nested reported speech, conditions, event participants and uncertainty live in the *current* source-facing and durable contracts? The conceptual fields above do not establish a frozen runtime schema.
- Can one stable logical proposition be compared across multiple source versions without merging distinct time/attribution/modality claims?
- Which event constructions warrant a separate referent and which can remain a relation/qualified proposition?
- Can candidate atoms about secondary referents survive extraction and later be selected in unrelated topics?
- How are source identity, exact spans, derivatives and independent origins replayed after revision?
- Can structured atoms support coherent, accurate multi-source narrative assembly without access to original prose at generation time?

These questions should be examined with the existing contracts and source code first. **Do not introduce a universal atom table, a separate semantic engine, new required durable record kinds, or new enums solely because this conceptual description has sections or YAML keys.** An extension needs a concrete failing case, a measured improvement, a migration/replay plan, and independent regression review.

## 12. Verification program

[**TS001 — Cross-Source Knowledge-to-Narrative Assembly**](RESEARCH_TESTS_AND_RESULTS.md) tests how evidence-grounded, unsequenced atoms can produce several different texts while preserving semantic, temporal, epistemic and provenance constraints. The program defines subtests, negative controls, score dimensions, and an obligation to publish the conclusions. **TS001 status: `NOT_RUN`.** The present atom model is **initial and unvalidated as an integrated implementation contract**; TS001 results must be reflected in the main documentation whether they confirm, qualify, or refute it.
