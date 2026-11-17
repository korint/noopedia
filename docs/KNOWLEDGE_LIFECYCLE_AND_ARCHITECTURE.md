# Noopedia — Knowledge Lifecycle and Architecture

**Document role:** current conceptual architecture map, consolidating concepts from the supplied sources. This is **not** a tested inventory of running services or a replacement for frozen machine contracts.

**Project-wide identity:** Noopedia investigates a different organization of human knowledge, not merely an alternative encyclopedia or a fixed atomization technology. Its architecture is experimental; the guiding question and the principles of unity, continuity, and commonality come first. See [Project Description and Philosophy](PROJECT_DESCRIPTION_AND_PHILOSOPHY.md) and [About](ABOUT.md).

## 1. A reusable knowledge substrate

This is a **current technical architecture in service of a wider philosophical mission**, not the definition of Noopedia. The project aims to develop a common human scientific apparatus, inspired by Vernadsky's account of scientific thought and the noosphere. **Unity, continuity, and commonality of knowledge** are the foundational principles; SAS/CIN/SPP and later mechanisms can evolve. See [Vernadsky and the Noosphere](VERNADSKY_NOOSPHERE_AND_SCIENTIFIC_APPARATUS.md).

Noopedia's intended unit of reuse is evidence-grounded meaning, not the document page. A source may mention many subjects and may establish different claims with different time, scope, modality, and attribution. The same accepted knowledge may contribute to an article, timeline, comparative review, Noo-View graph, or Noo Atlas display without reclassifying that claim as a new independent source.

```text
SOURCE PLANE
  permitted source → original bytes + capture/version + licensing metadata
  → exact passage / evidence anchor

SEMANTIC / KNOWLEDGE PLANE
  source assertion (SAS)
  → bounded contextual interpretation (CIN)
  → normalized proposition (SPP, when justified)
  → referents, relations, provenance, source-dependence,
    eligibility/admission and epistemic constraints

COMPOSITION PLANE
  output request + selected template/version + scope
  → eligible-knowledge selection + gap/coverage requirements
  → context-specific atom grouping and molecule ranking
  → dependency-aware presentation order / structured plan

PRESENTATION PLANE
  explanatory text / article / timeline / comparative view
  / semantic Noo-View / spatial Noo Atlas / other projection
  → evidence and semantic-integrity checks
  → separate review/publication decision where applicable
```

These are **conceptual separations**, not necessarily process, microservice, table, or queue boundaries. The exact implementation must be checked against source code and authoritative frozen contracts.

The source-grounded reusable meaning in the semantic plane is described in the [initial logical atom model](KNOWLEDGE_ATOMS_AND_STRUCTURAL_MODEL.md). Research into whether that model can support unsequenced multi-source narrative composition is registered as [TS001](RESEARCH_TESTS_AND_RESULTS.md), currently **not run**. Nothing in this conceptual separation introduces mandatory storage tables.

## 2. Information that must not be collapsed

| Distinction | Why it matters |
| --- | --- |
| Source expression vs. semantic content | Identical words can convey different meanings in different contexts; one meaning may have different linguistic expressions. |
| Source composition vs. semantic dependency vs. output order | Preserve original sequence and meaningful temporal/logical/narrative constraints without making a source's exposition order the permanent order of reusable knowledge. |
| Source identity/link vs. authenticated version and evidence | A URL or a reported citation is not proof that a specific original version or passage was inspected; retain verified anchors and access limitations. |
| Assertion (SAS) vs. interpretation (CIN) vs. proposition (SPP) | Contextual resolution and normalization must not erase what was actually written. |
| Source support vs. world truth | A perfectly cited statement may still be false, mistaken, or contested. |
| Claim vs. quotation vs. hypothesis vs. prescription | The type of speech act, modality, stance, conditions, and operator scope change its interpretation. |
| Identity vs. content equivalence | Two references to an entity do not establish that two claims have the same meaning. |
| Source repetition vs. independent corroboration | Multiple reprints or derivatives can reflect the same origin rather than independent evidence. |
| Knowledge vs. question | An expected value absent from the evidence is a question, not a stored zero-valued fact. |
| Eligibility vs. contextual priority | Knowledge admissible in a representation need not be important in that particular representation. |
| Atom rank vs. molecule importance vs. presentation order | These are context-dependent operations with different meanings and constraints. |
| Perspective projection (MPOV) vs. competing truth claims | Different institutional, cultural, or historical views may emphasize different aspects of the same subject without disagreeing on verified facts. A lens changes presentation, not underlying evidence or canonical claim meaning. |
| Subject history vs. history of understanding vs. source/record history | An event chronology or change log cannot substitute for how attributed interpretations of a subject changed across periods. |
| Research experiment vs. production capability | A successful fixture is not proof of full-product readiness. |

## 3. Evidence, time, and revisions

The intended source trail links an output back through selected propositions and original assertions to a specific source version, evidence passage, and capture. Revisions, invalidation, and history must be handled without silently replacing older evidence or attributing new information to the old source.

A source can reliably support that **a person made a statement** without supporting that **the statement is true**. Derived articles and presentation views do not acquire independent-source status merely by repeating a proposition. This constraint is essential for both publication and scoring.

The **history of understanding** is distinct from source revision and canonical-record history: it represents attributed, time-situated beliefs, explanations, disagreements, and changes in interpretation. Time of a view, time of the event it concerns, publication/capture time, and Noopedia revision time can differ and must not silently be collapsed.

## 4. Topic-independent disassembly

A source's apparent main topic is not a filter that licenses dropping other independently supported content. Atomization must find semantic roles and relations expressed by verbs, clauses, conditions, modifiers, and attribution while avoiding spurious facts. Genre profiles may change interpretation needs, but the shared semantic foundation remains the default.

The research exploration of knowledge gaps can derive applicable questions from object or relation types. Those questions belong in a **separate query or presentation layer**, not in the canonical store as fictitious answered atoms. Absence is explicitly scoped to the checked materials.

## 5. Template-based assembly

The selection template defines purpose, audience, output type, coverage requirements, relevant semantic relations, and ordering policy. Automatic assembly may combine grouping, relevance ranking, molecule-level weighting, and presentation planning iteratively. The result must be auditable against its template version and original knowledge scope.

**The source's exposition order is not an intrinsic order of the knowledge atoms.** Original wording and composition remain linked to source versions; chronology, causality, logical prerequisites and narrative-disclosure relationships remain meaningful constraints when supported. The plan chooses a new order for the audience, whereas exact originals and citations remain independently inspectable under source rights and access policies. See [Original Sources, Atomization, and Narrative Assembly](SOURCES_ATOMIZATION_AND_NARRATIVE_ASSEMBLY.md).

A template **cannot** justify inventing evidence, erasing contradictions, or strengthening claims. A brief summary may be shorter, but it must not become misleadingly certain. A higher priority score is **not** an epistemic confidence score.

**Encyclopedia-article coverage includes the evolution of human understanding of the subject** when relevant and supported: material historical interpretations, their attribution, coexistence, revision, and evidential context should be selected and assembled alongside an account of the subject itself. Do not substitute record history for intellectual history or fill evidence gaps with invented transitions. See [Evolution of Understanding in Encyclopedic Articles](EVOLUTION_OF_UNDERSTANDING_IN_ARTICLES.md).

**Important terminology caveat:** older Noopedia 2.0 documents use “template” for *entity-type schema contracts*. The assembly principles also use “template” for *contextual output/assembly policy*. They should not be conflated. This document uses **entity template** for the former and **output/assembly template** for the latter; actual naming and APIs remain an implementation decision.

## 6. Visual projections

**Noo-View** proposes relationship-driven semantic, temporal, and other knowledge visualizations, with citations and status retained in the interface. **Noo Atlas** provides a geographic/planetary direction for spatial display where the required place identity and coordinate/source evidence exists. Neither visualization should substitute for proof or make unsourced relations appear verified.

**MPOV** is likewise a perspective-specific projection over shared, evidence-linked knowledge. Different institutional or cultural lenses (for example USSR and US) may change focus or interpretation without inventing parallel factual stores or implying fringe views. See [MPOV — Multiple Perspectives on Shared Knowledge](MPOV_MULTIPLE_PERSPECTIVES.md).

Multiple views are different renderings and selections over shared knowledge, not multiple independent bodies of evidence.

## 7. Controlled automation and engineering boundaries

LLMs can propose extraction, interpretation, grouping, ranking, or prose. Existing deterministic and review controls must decide whether source anchors, schema values, trust status, and output publication satisfy their corresponding contracts. New features should reuse the present SAS/CIN/SPP path and existing knowledge/selection/compilation mechanisms where possible.

This document does not propose a new durable atom rank, new `record_kind`, separate article engine, source-specific atomization platform, or a second graph store. Any such change requires evidence of the deficiency in the current architecture and independent tests of both quality and future maintenance cost.

## 8. Technical foundations and source material

- [Technical Foundations](TECHNICAL_FOUNDATIONS.md) — the proposed processing contracts and their evidence boundaries, without historical milestone labels.
- [Documentation Scope](DOCUMENTATION_SCOPE.md) — how to distinguish concept, design, experiments, and verified implementation.
