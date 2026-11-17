# Noopedia — Technical Foundations

The technical work explores possible mechanisms for a wider philosophical aim: making the accumulated knowledge of humanity more interconnected, revisable, inspectable, and useful for further inquiry. This document describes **research and design foundations**, not a declaration that a complete end-to-end system is operating.

## Sources, interpretations, and propositions

A source can be a publication, observation record, archival document, or other material lawfully available for processing. The system must preserve the identity and specific revision of the source, the relevant evidence, and the circumstances needed to interpret its statements.

The shared semantic chain is expressed as **SAS / CIN / SPP**:

- **SAS (source assertion)** identifies what a specific source actually states and where the evidence is located.
- **CIN (contextual interpretation)** represents the meaning of a claim in context, including reference resolution, attribution, modality, negation, time, and uncertainty.
- **SPP (normalized proposition)** represents a source-grounded proposition in a form suitable for comparison and reuse, while retaining the distinctions and limits inherited from SAS and CIN.

A statement can be faithfully recorded while remaining untrue or unverified. The software should not collapse semantic fidelity, source support, and independent justification into one positive result.

The [initial atom model](KNOWLEDGE_ATOMS_AND_STRUCTURAL_MODEL.md) consolidates semantic roles, referents, qualifiers, provenance, attribution, temporal scope, evidence/support boundaries and typed relations. It is a **conceptual structure**, not a specification for a new atom table or evidence of an already implemented storage envelope. Technical implementation must be verified against actual schemas and code before modifying contracts.

## Conceptual knowledge flow

```text
Permitted sources + evidence
          ↓
Source assertions and contextual interpretation
          ↓
Candidate atomic knowledge + provenance
          ↓
Independent checks / review / controlled admission
          ↓
Interconnected knowledge and revision history
          ↓
Contextual selection + molecular grouping
          ↓
Articles · MPOV · Noo-View · Noo Atlas · other presentations
          ↖  Questions, criticism, corrections, new research
```

Each stage is conceptual. A historical experiment or accepted local component does not prove that the whole flow is implemented or production-ready.

## Atomization and assembly

Atomization aims to preserve reusable units of meaning without erasing the original source wording or its semantic conditions. These units should be useful across many topics and presentations, not extracted solely to reproduce the section structure of one article.

**Molecules** are task-dependent compositions of related atoms. Their grouping, selection, and priority depend on the research or presentation goal; there is no required permanent global rank for each atom. Both the inclusion and exclusion of important material should be explainable. See [Semantic and Epistemic Principles](SEMANTIC_AND_EPISTEMIC_PRINCIPLES.md) and [Template-Driven Assembly](TEMPLATE_DRIVEN_RANKING_AND_MOLECULAR_ASSEMBLY.md).

An **entity template** describes applicable fields or questions for a class of objects. An **output template** describes how knowledge is selected, grouped, and presented. They must not be conflated.

**Knowledge has no mandatory source-derived exposition order.** Source sequence should remain attached to the original; material event order, causal structure, argumentative dependencies, attribution, and narrative disclosure should be retained when meaningful. A generated description is a **new, evidence-grounded presentation**, not a verbatim restoration of its source. Its claims should resolve back to original source versions and exact evidence, with appropriate source links and rights controls. See [Original Sources, Atomization, and Narrative Assembly](SOURCES_ATOMIZATION_AND_NARRATIVE_ASSEMBLY.md).

The experimental feasibility of cross-source, order-independent recomposition is not established by a pipeline diagram. [TS001](RESEARCH_TESTS_AND_RESULTS.md) defines ten tests and requires measured results, including negative findings and evidence links, to be published in `/docs/`. **Current TS001 status: `NOT_RUN`.**

## Views and historical context

- **MPOV** makes differently situated, source-grounded perspectives available as projections over shared knowledge; different emphases do not necessarily amount to incompatible facts.
- **Evolution of understanding** makes it possible for articles to describe how interpretations and explanations changed over time, separately from the history of the subject itself or the database's audit trail.
- **Noo-View** and **Noo Atlas** explore semantic, temporal, geographic, and planetary presentations, with no implication that the rendering technology or present interaction model is final.

These presentations must not silently strengthen the epistemic status of the knowledge they show.

## Processing, verification, and change

Proposed execution methods include centrally operated tools and voluntary distributed processing. Multiple independently executed candidates can be compared, but their agreement alone is not proof of correctness; support against exact source passages and controlled review remain essential.

A correction or source update should preserve prior context and allow affected representations to be reconsidered. Changes to schemas, storage, review requirements, or services should be justified by concrete counterexamples and independently checked regressions, with attention to future maintenance costs.

## Safety and engineering limits

Source permissions, licensing, privacy, credential custody, untrusted clients, prompt injection, and data provenance require explicit boundaries. Contributed computation must not grant automatic publication authority. The project's intent to support collective inquiry does not nullify the rights of source creators or the need for reliable validation.

For a fuller conceptual processing map, see [Knowledge Lifecycle and Architecture](KNOWLEDGE_LIFECYCLE_AND_ARCHITECTURE.md).
