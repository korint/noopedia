# Noopedia — MPOV: Multiple Perspectives on Shared Knowledge

**Document role:** enduring conceptual and editorial description of MPOV (*Multiple Points of View*).  
**Status:** target behavior and validation criteria; does not imply a production-ready perspective engine or authorize new persistent structures.

## 1. What MPOV means

**MPOV is the ability to examine the same subject through different, explicitly identified perspectives or projections of a shared knowledge structure.** It is a central distinction of Noopedia, alongside knowledge atomization, the history of changing understanding, and semantic/spatial visualization.

A perspective can be associated with a state, society, culture, institution, school of thought, disciplinary tradition, geographic position, or historical period. It can shape **which parts of the subject are emphasized, which questions are asked, which interpretations are presented, and how an account is organized**. It need not imply that the perspectives are mutually exclusive or that there is any dispute at all.

**MPOV is not a catalog of conspiracy theories, fringe claims, or mutually incompatible “alternative facts.”** Such materials may occasionally be relevant as attributed historical objects of study, but they do not define the idea. The ordinary, important case is that competent observers or participants approach a common subject from different positions and interests.

## 2. An illustrative comparison: the USSR and the United States

Consider an article about a historical episode of the space race or the Cold War:

- A **Soviet perspective** may foreground the goals, institutions, public language, scientific achievements, and political context of the USSR, as evidenced by identified sources from that setting.
- A **US perspective** may foreground corresponding American institutions, strategic concerns, political debates, scientific priorities, and contemporary interpretations, again supported by identified sources.
- A **comparative projection** may place these emphases alongside each other, identify shared empirical anchors, and explain meaningful differences of attention, framing, and interpretation.

These are **illustrative ways to organize evidence**, not permission to assume that all people in a country shared a single belief, to attribute a statement to a state without a source, or to insert stereotyped narratives. The relevant actor, organization, author, date, audience, and kind of source must be specified where possible.

Crucially, the underlying event identity, chronology, measurements, citations, and provenance do not become separate incompatible databases when the reader switches perspectives. Where the historical record itself is contested, the disagreement remains visible and evidence-linked across projections.

## 3. Projection, not a parallel truth store

Noopedia should seek to reuse **one interrelated knowledge substrate** for different MPOV projections. A projection is an explicit **selection, filtering, contextual grouping, ordering, and presentation policy**, not a license to rewrite the canonical meaning of knowledge atoms.

A perspective should be inspectable:

- **Whose view?** The actor, publication, institution, school, or carefully delimited group, with its temporal and geographic context.
- **Which sources?** Exact source passages, provenance, versions, and possible source dependencies.
- **What changes?** The emphasis, subset, terminology in attributable quotations, interpretive grouping, and presentation sequence.
- **What is common?** Shared empirical reference points and claims supported across relevant sources.
- **What is disputed?** Genuine interpretive or factual conflicts, not invented disagreements arising merely from a different presentation order.
- **What is unknown?** Missing or uncertain evidence, limitations of corpus coverage, and unresolved attribution.

Different projections may legitimately emphasize different features without contradicting one another. They may also contain competing interpretations that require explicit epistemic comparison. No projection should silently turn an attributed viewpoint into an independently established fact.

## 4. Relationship to interpretation and verification

MPOV represents **how subjects are seen and explained by situated observers**, not a voting procedure for deciding truth. The existence of two narratives does not mean they deserve identical evidential weight. Likewise, a shared factual core does not erase differences in values, aims, methods, experiences, or interpretations.

Preserve at least the distinctions between:

1. **A source's wording and stance** — what a particular actor actually said or emphasized.
2. **An evidence-grounded account of the subject** — what is supportable in the checked material.
3. **A reader-selected projection** — what the user chooses to focus on and how the relevant content is arranged.
4. **A contested or false historical claim** — a possible object of historical research, not automatically a true assertion about the world.

Source provenance and epistemic review apply to every projection. In particular, labels such as “Soviet,” “American,” or “Western” must not be inferred solely from language, geographic origin, or a single quotation. Source-school classification itself may be disputed and should remain reviewable.

## 5. MPOV and the history of understanding

MPOV and intellectual history are **distinct complementary dimensions**:

- **MPOV:** how different actors, traditions, or communities approach the subject, including at the *same* time.
- **Evolution of understanding:** how those views appeared, changed, interacted, were challenged, or acquired or lost evidential support over time.

For example, a reader could compare Soviet and US perspectives on one period, then move forward in time to study how each perspective evolved. A Noopedia article should be capable of explaining historically significant changes of understanding **without making the reader switch to a separate MPOV view**. See [Evolution of Understanding in Encyclopedic Articles](EVOLUTION_OF_UNDERSTANDING_IN_ARTICLES.md).

## 6. MPOV in articles and visualizations

A Noopedia encyclopedia article might offer a balanced subject overview *and* inspectable perspective projections: contrasting passages, parallel timelines, thematic filters, comparative tables, source lists, or selected sections. The use of different perspectives is **not limited to controversial subjects**. Every rendering must continue to distinguish source claims, interpretations, and warranted facts.

The same perspective definitions could inform Noo-View's graph, radial, spherical, and temporal modes and geographically grounded Noo Atlas views. These views present relations, positions, and contrasts: their appearance is not itself evidence of a factual connection.

An earlier design explored **Western / Soviet / Local / Consensus** lenses as read-time projections over source-attributed knowledge. These examples illustrate the perspective mechanism, not proof of implementation or a requirement to preserve any particular database model.

## 7. Evaluation requirements

A functional MPOV implementation should pass independent cases in which:

1. **Two perspectives differ mainly in emphasis**, not in claims of fact. Both must produce meaningfully distinct, source-supported presentations.
2. **Perspectives disagree on an interpretation.** The disagreement, author, supporting reasons, and uncertainty remain visible.
3. **A source perspective is uncertain or misclassified.** The system avoids fabricated national or institutional attribution and supports correction.
4. **A user changes projection.** Canonical claims, source versions, evidence anchors, and epistemic statuses remain stable; the explanatory selection may change.
5. **The comparison spans several periods.** A chosen perspective and the development of that perspective over time can be shown separately and together.
6. **Source coverage is asymmetric.** The system identifies missing coverage rather than implying that a missing perspective is empty or that one side's record has been disproved.

No new table, independent narrative engine, mandatory source-school taxonomy, or runtime change follows automatically from this document. Use existing **SAS/CIN/SPP**, provenance, perspective, template, and view components where they can support the intended behavior. New mechanisms require concrete counterexamples and tests.

See also [Project Philosophy](PROJECT_DESCRIPTION_AND_PHILOSOPHY.md) and [Vernadsky and the Common Scientific Apparatus](VERNADSKY_NOOSPHERE_AND_SCIENTIFIC_APPARATUS.md).
