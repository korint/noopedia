# Noopedia — Evolution of Understanding in Encyclopedic Articles

**Document role:** enduring project requirement for article composition and the history of ideas.  
**Status:** intended editorial and semantic behavior; **not** evidence that the current article compiler or user interface implements it.

## 1. Central requirement

**A Noopedia article should describe not only its subject, but—where relevant, materially important, and supported by identifiable sources—how human understanding, beliefs, interpretations, and scientific explanations of that subject have developed and changed over time.**

This is a distinguishing goal of Noopedia, alongside deep semantic atomization, evidence-sensitive **MPOV** (multiple points of view), and spatial, temporal, and semantic visualization, including exploratory spherical Noo-View representations.

The history of understanding is **part of the subject's encyclopedia article**, not merely an optional log of page edits, an external timeline, or a separate visualization. Different article lengths and audiences may present it as a section, a short synthesis, or links to a deeper account. Do not invent a historical progression where reliable evidence or relevance is insufficient.

The aim is to represent **how humanity has thought about, explained, debated, and reinterpreted the world**, as well as what can be established about the world itself. Historical beliefs and rejected theories remain meaningful objects of knowledge, but their historical existence is not proof of their correctness.

## 2. Four distinct kinds of history

A system must not substitute one of these histories for another:

| Kind | Question answered | Example |
| --- | --- | --- |
| **History of the subject** | What happened to the object, event, institution, or phenomenon? | A planet's missions and observations; a city's changes in boundaries. |
| **History of understanding** | What did particular people, disciplines, societies, or communities believe or explain about it at different times, and how did that change? | Successive astronomical interpretations of Mars, with attribution and dates. |
| **History of sources** | What was stated in a particular document or source revision, and when? | A new edition of a paper revises an earlier conclusion. |
| **History of Noopedia records** | When did the system extract, review, correct, admit, withdraw, or republish a representation? | A corrected atom or regenerated article version. |

An article can relate all four, but **knowledge-base edit history is not the history of human thought**, and an event timeline is not automatically a history of scientific or social interpretation.

## 3. Relationship to MPOV

**MPOV and the evolution of understanding are complementary, not interchangeable.**

- **MPOV is a perspective-specific projection of shared knowledge**, not a catalog of conspiracy theories or alternative truth claims. It can compare different emphases and interpretations even when the underlying factual account is compatible. For example, USSR and US accounts of a Cold War or space-race episode can foreground different institutions, questions, and concerns while sharing evidence-linked event anchors.
- The evolution of understanding follows changes over time: the emergence of ideas, competing explanations, reinterpretations, revisions, shifts in evidence, and positions that became obsolete or remained disputed.
- The two dimensions intersect: multiple perspectives may coexist in one period; an older position may persist after a newer explanation appears; and views may vary by community or tradition rather than moving along one universal trajectory.

MPOV is described in [MPOV — Multiple Perspectives on Shared Knowledge](MPOV_MULTIPLE_PERSPECTIVES.md). Do not present intellectual history as an inevitable linear march toward consensus. A claim that one idea caused another to be abandoned requires its own evidence; chronological succession alone does not establish causation.

## 4. Evidence and representation rules

Historical assertions about understanding must preserve, as applicable:

1. **Who held or expressed the view:** person, author, school, institution, community, or a carefully qualified collective; do not infer universal belief from a single source.
2. **What was understood or argued:** the proposition, interpretation, hypothesis, explanation, or recorded belief, rather than an unqualified statement about the world.
3. **When and where it applied:** relevant interval, publication date, time of the described view, social or geographical context, and any uncertainty in dating.
4. **Why a change is asserted:** evidence for a new observation, experiment, criticism, conceptual framework, or transmission of ideas, when the sources establish the relationship.
5. **Its epistemic status:** distinguish a historical claim about a belief from whether that belief was or remains supported, disputed, superseded, or invalidated.
6. **Its provenance:** source passages, versions, dependence between sources, the context of quotation/attribution, and any review and publication restrictions.

Representations should reuse Noopedia's existing source assertion, contextual interpretation, normalized proposition, provenance, temporal qualifiers, and perspective mechanisms (**SAS/CIN/SPP and the applicable accepted contracts**). This requirement **does not itself authorize new persistent tables, record kinds, or a separate history-of-ideas engine**. Any concrete storage extension requires a demonstrated gap and independent validation.

## 5. Article assembly requirements

For an encyclopedia article where substantial source-supported history of understanding is available:

- Include a reader-visible account of **the main historical interpretations and meaningful changes of understanding** alongside the description of the subject itself.
- Distinguish historical belief, present evidence-based assessment, current uncertainty, and perspectives that remain contested.
- Select and group dated, attributed claims across relevant periods and sources; do not derive the history of understanding solely from changes in the subject's physical state or from article-version logs.
- Show major disagreements and enduring alternatives when they matter; avoid false balance and do not equate repeated dependent reports with corroboration.
- Where a shift or replacement is described, specify the supporting evidence or preserve uncertainty about the reason.
- Keep the assembled text traceable to the underlying atoms, their source passages, and the article's selected output template and versions.

This is a **default editorial coverage requirement**, not a fixed heading that every brief entry must mechanically contain. A short article can summarize the trajectory concisely or point to a detailed treatment. If checked sources do not support such a history, record that as a **scoped coverage gap** rather than fabricate consensus, dates, or discarded theories. Do not imply that the wider world lacks evidence merely because the current corpus lacks it.

The article template should consider the history of understanding an **explicit coverage dimension** during selection, molecule formation, and ranking. A period with fewer repeated sources may still be indispensable to the subject's intellectual history.

## 6. Illustrative example: Mars

An article on **Mars** might connect several kinds of evidence-backed content:

- What Mars is and what has been observed or measured about it.
- How particular ancient societies represented it; such claims require specific cultural and textual attribution.
- How 19th- and early 20th-century observers proposed and debated interpretations of apparent surface markings, including the historical idea of Martian canals.
- How subsequent observations and spacecraft exploration changed the evidence and scientific accounts, without implying that every earlier observer shared the same theory.
- Which questions remain scientifically unsettled, and why they remain open.

That is an **illustration of the intended article structure**, not a claim that these particular historical source records are presently available, validated, or automatically assembled in Noopedia.

## 7. Relationship to visualization

The same evidence-linked understanding history can be explored through:

- a prose article with sections or compact historical notes;
- a timeline of **views and their evidential contexts** (distinct from a timeline of real-world events);
- an MPOV comparison filtered by epoch, source, or perspective, including different societal or institutional projections over the same subject;
- a Noo-View graph or semantic sphere showing attributed views, supporting evidence, contradictions, and changes;
- a Geo-View/Noo Atlas projection where the historical positions have justified geographical anchors.

Visualization adds ways to navigate the same traceable knowledge; it does not replace the article-level requirement or turn spatial proximity into a semantic fact.

## 8. Verification criteria

Evaluate this article capability separately from ordinary article fluency and from version-history functionality:

1. **Distinction:** Does the article include genuine changes in *understanding*, not merely changes in the subject or the database?
2. **Temporal and actor fidelity:** Are periods, communities, authors, and viewpoints accurately attributed without anachronism?
3. **Semantic and epistemic fidelity:** Does it distinguish a belief's historical existence from the truth of its content, preserve modality and contestation, and avoid false equivalence?
4. **Coverage:** Are material turning points and meaningful coexisting or minority perspectives included at an appropriate level of detail?
5. **Support:** Are statements about changed interpretations, transitions, and causes traceable to permissible source evidence?
6. **Reproducibility:** Can one reconstruct which atoms, sources, template, and review decisions produced the account?
7. **Honest limits:** Are unsupported transitions withheld rather than filled in by model background knowledge?

For a pilot, compare at least one subject with well-documented changes of interpretation, one with competing views in the same period, and one with insufficient evidence. Test the resulting article content as well as any optional visual presentation. Passing a UI timeline or a source-revision test alone is **not** proof that this requirement is met.

## 9. Scope and implementation status

This is a **project-level requirement** for future encyclopedia article assembly. It is not a claim that Noopedia currently generates such sections. Implementation should first reuse existing atomization, provenance, temporal, selection, and article compiler paths. Any architectural change must be justified by concrete counterexamples and measured improvements, with attention to maintenance costs.

See [Project Description and Philosophy](PROJECT_DESCRIPTION_AND_PHILOSOPHY.md), [Knowledge Lifecycle and Architecture](KNOWLEDGE_LIFECYCLE_AND_ARCHITECTURE.md), and [Template-Driven Ranking and Molecular Assembly](TEMPLATE_DRIVEN_RANKING_AND_MOLECULAR_ASSEMBLY.md).
