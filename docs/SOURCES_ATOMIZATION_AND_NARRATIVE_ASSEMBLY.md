# Noopedia — Original Sources, Atomization, and Narrative Assembly

**Document role:** conceptual and architectural foundations for separating source expression, reusable knowledge, and newly composed representations. This document states principles, design boundaries, and research questions; it does not claim that the whole workflow has been implemented or validated.

## 1. The central principle

> **Knowledge must not inherit the source's order of exposition as an obligatory property of its own structure. Its representation should be formed according to purpose, context, and semantic relationships, while preserving those sequences and dependencies that are part of the meaning itself.**

Noopedia investigates a knowledge space in which the original document is neither discarded nor treated as the permanent container and ordering system for everything it expresses. A source can be examined for reusable meaning; that meaning can be linked to other evidence; and many new presentations can be constructed for different questions and audiences.

This is not a promise that arbitrary prose can be perfectly decomposed or regenerated. **Disassembly is an interpretive, potentially lossy operation; assembly is a new, evidence-constrained act of composition, not the inverse operation that reconstructs the original work.**

The resulting design must preserve two things at once:

1. **Independence of knowledge from any one exposition.** A construction date, a quoted belief, a causal explanation, or an observed relationship should not acquire a permanent paragraph number merely because its first source expressed it in paragraph three.
2. **Integrity of the original work.** Wording, authorship, argument, composition, rhetoric, genre, language, and the sequence in which an author presents information may themselves matter and must remain accessible as properties of the source, within applicable rights and access limits.

The research question is not simply whether a model can write an article. It is whether Noopedia can produce **different, meaningful, traceable representations from an evolving body of knowledge without confusing those representations with their sources or introducing unsupported meaning**.

## 2. Four distinct layers

| Layer | What it preserves | What it is *not* |
| --- | --- | --- |
| **Original source** | An authored or observed artifact: exact edition or revision, words or other media, structure, context, bibliographic identity, and permitted evidence access. | A permanently true account of the world merely because it was published. |
| **Semantic and evidential knowledge** | Source-grounded assertions, interpretations, normalized propositions, qualifiers, time, relationships, provenance, and epistemic status. | A copy of the source's entire literary or rhetorical form, or a collection of verified facts by default. |
| **Composition plan** | A task-specific selection of eligible knowledge, semantic groupings (“molecules”), dependencies, ordering choices, and explanations of omissions. | An intrinsic canonical order or importance rank imposed on atoms. |
| **Presentation** | A readable article, analytical narrative, timeline, comparison, FAQ, map, graph, audio script, or another output. | A replacement for the source, independent evidence, or necessarily a faithful reproduction of the source text. |

These are conceptual distinctions, not instructions to create four databases, services, record types, or separate engines. They should be implemented, where feasible, using existing source and semantic contracts and current article-selection/compilation machinery.

## 3. The originals remain indispensable

### 3.1. The original is an artifact in its own right

Noopedia should preserve the distinction between **a source as an object of study** and **the knowledge claimed by that source**. A book, speech, research paper, official record, website, photograph, recording, or dataset may carry information that cannot be captured as a simple list of propositions:

- exact wording, terminology, idiom, translation choices, ambiguity, and register;
- narrative pacing, framing, omissions, composition, and the sequence of disclosure;
- the structure of an argument, a proof, an experiment, an interview, or a report;
- genre, intended audience, social and historical context, speaker, and audience;
- figures, typography, tables, audiovisual context, annotations, and other medium-specific evidence;
- revisions, corrections, censorship, editorial intervention, or changes between editions.

A source may also become the *subject* of knowledge: Noopedia can represent who authored it, when it circulated, how it was translated, cited, criticized, or interpreted. That does not mean its text is reducible to these facts.

### 3.2. Record identity, not merely a URL

For every eligible source, the intended provenance should distinguish, as applicable:

- **Work / document identity:** title, creator(s), publisher or custodian, language, identifiers (for example DOI, ISBN, archival catalogue identifier), and the kind of artifact.
- **Edition / source version:** publication, edition or revision identifier, date, language or translation, and relationship to earlier or later versions.
- **Acquisition / observation:** when and from where the content was obtained, acquisition conditions, format, and evidence of its integrity when a lawful capture exists.
- **Evidence position:** the exact supported passage, page or section, timestamp, table cell, media region, segment and offsets where meaningful; the normalization rules behind those offsets.
- **Access and rights:** source license, retention permissions, permitted display and quotation, visibility restrictions, and relevant takedown or privacy conditions.
- **Links:** publisher or custodian's original location, canonical identifiers, observed URLs and their history, and legally permissible archive or mirror locations.

A URL is a locator, **not proof of an exact edition**. A content checksum identifies captured bytes, **not the truth of the contents**. A working hyperlink is helpful, **not a substitute for the evidence version and passage used during processing**.

The historic source-registry proposals distinguish document, version, capture, segment, assertion, and citation references. Those distinctions are useful design references, but their presence in documentation does not establish that a particular storage schema, archive, or resolver currently exists.

### 3.3. Original content, a link, and an archive are different things

The system must not assume that an original can always be downloaded, retained, publicly displayed, or redistributed. Depending on permissions and availability, a source may be represented by:

| Situation | Appropriate behavior |
| --- | --- |
| Lawfully retained, verifiable full capture | Preserve integrity and version identity; expose the permitted original or passage and its source metadata. |
| Original accessible through its publisher or archive, but not locally retained | Link to the exact source where possible; describe which version and evidence were inspected; do not imply a local copy exists. |
| Access-restricted or licensed source | Respect access scope; expose permitted metadata, links, and limited evidence or citations only under applicable terms. |
| Only a secondary source reports or quotes an original | Preserve the secondary source and its literal citation; mark the primary original uninspected until independently obtained and checked. |
| Source moved, changed, or disappeared | Keep bibliographic identity, previously verified evidence lineage where lawful, and broken-link/availability status; seek a permitted stable locator without fabricating an archived source. |
| Source cannot legally or ethically be processed or retained | Do not ingest or redistribute the protected content; record permitted metadata or a reason for exclusion where appropriate. |

**Source preservation is not equivalent to unrestricted public republication.** Public access to a source, authorization to analyze it, permission to cache it, and permission to quote or redistribute it are different questions. The relevant policy must be reviewed under the applicable laws and licenses; this document does not decide those legal questions.

### 3.4. Citations between originals form a separate graph

A source may **cite, quote, summarize, reprint, correct, or dispute** another source. These links are important even when the claims discussed are not accepted as facts. They should remain distinguishable from `SUPPORTS`, `CONTRADICTS`, or `UPDATES` relations at the claim level.

If source B cites an inaccessible source A, Noopedia knows that **B cites A**. It does not thereby know that A was inspected, that B quoted A correctly, that A supports the claim, or that A and B constitute independent corroboration. A citation match, when later verified, establishes an attribution relationship; it still does not establish the truth of the attributed claim.

This prevents both false provenance and the multiplication of one origin into seemingly independent sources.

## 4. What atomization can and cannot preserve

### 4.1. Extract meaning, not paragraph-shaped fragments

Atomization seeks reusable content grounded in a specified source scope. The existing **SAS / CIN / SPP** distinction is important:

- **SAS — source assertion:** what an exact source version asserts, with a recoverable evidential anchor.
- **CIN — contextual interpretation:** what the assertion means in context, with cautiously resolved referents and semantic operators.
- **SPP — normalized proposition:** a form suitable for comparison and reuse, without silently removing relevant conditions or attribution.

Useful extraction is not limited to isolated subject–predicate–object triples. It may require relations expressed by verbs, subordinate clauses, negation, time, conditional statements, uncertainty, agency, scope, speaker and quoted speech. A source's main topic must not become an excuse to discard independently supported information about other subjects.

The three checks **semantic fidelity**, **source support**, and **epistemic warrant** remain separate. A faithful representation of what an author believed is not proof that the belief was correct.

### 4.2. Not every piece of meaningful material is a factual proposition

An original may contain questions, commands, wishes, metaphors, dialogue, speculation, a fictional narrator's voice, irony, persuasive devices, or an author's choice to delay an explanation. A universal semantic approach must recognize these forms without converting them into statements about the real world.

For example, “the minister said the project was safe” supports an attributed statement; it does not, without other evidence, support the proposition that the project was safe. In fiction, a character's claim can be represented as **an assertion within the fictional world**, not automatically a claim about reality.

Some features should remain source-level annotations or interpretive descriptions rather than forced into a new atomic record class. Proposals for persistent new representations require examples showing why existing source spans, relations, qualifiers, and metadata are insufficient.

### 4.3. Atomization is not lossless compression

The following generally cannot be recovered exactly from semantic atoms alone: original wording, stylistic rhythm, authorial voice, rhetorical force, formatting, dramatic timing, and every implication created by the work's complete arrangement.

Reversibility therefore has at least three distinct meanings:

1. **Evidence reversibility:** from a generated assertion, recover the source(s), version(s), and specific evidence supporting it. This is an essential design goal.
2. **Semantic re-expression:** from selected, grounded knowledge, produce an alternative explanation with equivalent material meaning and clearly marked qualifications. This is an experimental goal that can be evaluated.
3. **Verbatim reconstruction:** reproduce the exact original document. This is **not** something semantic atomization promises. Where an exact original is needed and rights permit, retrieve or display the authenticated original; do not fabricate it by generation.

## 5. Source order, semantic dependencies, and presentation order

**No universal linear order belongs to the knowledge corpus.** Yet some kinds of order are themselves meaningful and must survive extraction.

| Ordering or dependency | Example | Preservation rule |
| --- | --- | --- |
| **Source sequence** | An author introduces a concept in chapter one and criticizes it in chapter five. | Preserve chapter/section/span order as a property of the source; do not impose it on all derived articles. |
| **Historical or event order** | Event B occurred after event A. | Preserve the temporal relationship and uncertainty; a presentation may recount events in another order if readers are not misled. |
| **Causal dependency** | One process is claimed or shown to cause another. | Preserve causality, attribution, conditions, and whether the claim is supported, disputed, or merely proposed. |
| **Logical or argumentative dependency** | A conclusion relies on premises, assumptions, or a definition. | Retain the inferential relationship and scope. A derived explanation may introduce the conclusion first but must restore the support needed to interpret it. |
| **Narrative disclosure** | A novel reveals a character's motive late. | Preserve the source's disclosure sequence when analyzing its narrative form; a plot synopsis may use chronology, with an explicit spoiler policy where relevant. |
| **Presentation order** | A beginner's explanation defines terms before discussing exceptions. | Choose for the output task, audience, medium, and template; never confuse this choice with an intrinsic rank or source order. |

Ordering decisions must not reverse the meaning of temporal, conditional, logical, or discourse relationships. **“Not fixed” does not mean “arbitrary.”**

The system should be able to identify the *reason* for an order: temporal necessity, conceptual prerequisite, centrality, explanatory convenience, rhetorical structure, or selected presentation policy. Some orders are constraints; others are editorial choices.

## 6. Templates as policies for making representations

An **output or assembly template** specifies a *general policy*: what question an output answers, whom it serves, which material it needs, how it groups evidence, and what kind of progression will help a reader understand it. It is **not** a fixed sequence of specific atomic IDs or a replacement for verification.

A template may define:

- output profile (encyclopedia entry, overview, timeline, technical explanation, comparison, historical evolution, question-led inquiry, audio narration, educational introduction);
- intended audience, language, format, accessibility, density, length, and level of prior knowledge;
- evidence threshold, eligibility, temporal cutoff, perspective and attribution rules;
- required topics and applicable questions, including how to reveal gaps or insufficient coverage;
- preferred relations and molecule-building criteria: identity, part–whole, event, causation, comparison, method, chronology, debate;
- section functions and dependencies (overview, prerequisites, explanation, evidence, limitations, open questions), without prescribing a fact-by-fact universal order;
- contradiction handling, coverage and diversity targets, source/citation presentation, and sensitivity to reader expectations;
- restrictions on claims, tone, creative variation, faithful quotation, and use of protected text.

**Entity templates** are different: they identify applicable fields or questions for a *kind of object*. An entity template can suggest what is worth asking about a bridge, planet, scientific hypothesis, or historical event; it does not by itself decide the article's rhetoric or prove an answer exists.

An output template may use entity-template questions to assess coverage. A missing answer is recorded as a **scoped gap or question**, not invented as a fact or interpreted as proof of absence.

## 7. Molecular assembly and the making of a narrative

### 7.1. Select knowledge for the question

A request identifies the topic, intended audience, relevant time frame, perspective, evidence threshold, and desired representation. The system selects eligible, evidence-linked knowledge across sources and retains the reasons for selecting, withholding, or omitting material. **Priority in an output is not epistemic confidence; frequency of repetition is not independent corroboration.**

### 7.2. Form context-dependent molecules

Related atoms can be grouped around an event, mechanism, period, explanation, shared subject, argument, or disagreement. A molecule may supply introductory context, a central explanation, a caveat, or historical background. A single atom can participate in different molecules for different outputs. The molecule's weight must not be inferred only from the sum of atom scores.

Molecules are **compositions for a task**, not mandatory new permanent knowledge objects. Their formation should reuse the existing knowledge selection and article-planning paths wherever possible.

### 7.3. Construct an explanatory plan before prose

A practical conceptual flow is:

```text
Source identities, exact versions, permitted evidence
                   ↓
SAS → CIN → SPP, qualifiers and provenance
                   ↓
Question / audience / output profile / template
                   ↓
Eligible knowledge selection + coverage obligations + gap checks
                   ↓
Molecule formation + dependency-aware relevance and ordering
                   ↓
Structured presentation plan (sections, blocks, claim obligations)
                   ↓
New prose or visual representation with citations
                   ↓
Semantic, evidential, coverage, rights and publication checks
```

In historical technical descriptions, **knowledge selection**, **article obligations**, **fact bundles**, and an **article plan** are already candidate parts of the synthesis flow. This document does not mandate a new planner or an additional synthesis engine. The existing article compiler should be evaluated first.

### 7.4. Produce new language without producing new unsupported facts

A language model or human writer may transform a plan into coherent prose, add transitions, explain why a section matters, or vary the level of detail. Such writing is allowed only insofar as it does **not** silently introduce:

- invented names, dates, events, causal links, motivations, estimates, or conclusions;
- unwarranted certainty, altered referents, removed conditions, or lost negation;
- apparent consensus from copied sources or apparent independent verification from generated material;
- a misleading order that suggests causation, priority, or inevitability not supported by the evidence;
- false quotations, reconstructed passages presented as originals, or unlicensed close paraphrases.

Where explanation requires genuinely new inference, distinguish it from source-stated information, supply its inputs and reasoning where justified, and keep it subject to an explicit verification or interpretation policy. A stylistically elegant paragraph does not certify any of its claims.

## 8. One knowledge space, many distinct narratives

A common body of evidence can support fundamentally different outputs. Consider an **illustrative, fictional** source passage:

> The Aster footbridge opened in 1958. A municipal report of that year called it a temporary crossing. Later reports discussed a replacement, but no replacement date was stated in the material examined.

A careful extraction might preserve: an attributed opening event and year; the fact that a municipal report used the description “temporary”; the existence of reported replacement discussions; and the **bounded absence** of a replacement date in the inspected material. The second claim is not automatically a verified engineering classification, and the last is not proof that no replacement ever occurred.

Using the same supported information, different output templates can produce:

| Output | Possible composition |
| --- | --- |
| **Encyclopedic description** | What the bridge is → recorded opening → source-attested intended status → documented later discussion → what remains unknown. |
| **Historical timeline** | Dated opening → contemporaneous report → later discussions, with uncertain dates clearly labeled. |
| **Infrastructure analysis** | Purpose and temporary status *as reported* → evidence about replacement planning → limitations of the checked sources. |
| **Public-facing short answer** | Opening year and a concise, attributed explanation; omit extra detail only if the omission is not misleading. |
| **Questions for research** | Which replacement proposals were made? What primary documents could date them? These are questions, not new assertions. |

The example demonstrates **presentation flexibility**, not a license to embellish sparse evidence into a rich history. New evidence from additional sources may later supply further supported answers without requiring the first text's sequence to govern every subsequent output.

## 9. Different genres require different fidelity decisions

### 9.1. Descriptive and encyclopedic writing

Descriptions often benefit from reusable section functions: identification, characteristics, parts, history, relationships, significance, disputes, and unanswered questions. These are template options, not a universal checklist. Output requirements must adapt to the evidence, object class, and audience. Where relevant, encyclopedia articles should include **the changing human understanding of the subject**, not merely its physical chronology or Noopedia's edit history.

### 9.2. Scientific and technical writing

A research paper is not simply a bag of results. Methods, assumptions, population, measurement uncertainty, conditions, definitions, and the order of reasoning may determine what a conclusion actually means. A synthesized review may reorganize papers by question, method, or competing interpretation; it must keep the premises and limitations with the conclusions they qualify. Methods and inferences cannot be upgraded into independently verified facts by recomposition.

### 9.3. History, debate, and MPOV

Historical narratives must separate events from later descriptions of them, the period of a belief from the period described by the belief, and contemporary interpretation from retrospective interpretation. **MPOV** can compare situated cultural, institutional, political, or scholarly lenses over a common evidence-linked substrate—for example, Soviet and US accounts of the same event—without equating perspective with conspiracy or treating every account as equally substantiated.

The **history of understanding** is another distinct axis: how human views emerged, coexisted, were challenged, changed, or disappeared. Different projections and historical periods may produce different valid narrative arrangements over related evidence.

### 9.4. Literature, memoirs, interviews, and expressive works

Atoms may describe characters, events, narrative claims, recurring motifs, locations, or relationships. They can support a synopsis, a chronology, a character study, or a comparison between interpretations. They do **not** reproduce the original literary experience, voice, suspense, humor, rhythm, or exact narration. Even a detailed plot outline is not a substitute for the book.

Narration can be unreliable; dialogue may carry a character's belief rather than an authorial assertion; memoir and testimony may require explicit attribution. A translation is a separately identifiable expression, not proof that a quoted phrase occurs verbatim in every edition. If an exact passage matters, refer to or show the authorized original rather than generating a near-copy.

### 9.5. Nontextual and mixed sources

Images, maps, audiovisual works, datasets, charts, and interactive artifacts have spatial, temporal, graphical, or computational structures. They may require region or timestamp anchors, transformation metadata, coordinate systems, or a data/query snapshot. Text summaries cannot silently replace these features. Reuse the same principles of source identity, evidence scope, rights, and traceability across media while researching the appropriate representation for each genre.

## 10. Linking every output back to originals

A generated presentation should support two complementary reader needs:

1. **Understand the content:** readable inline citations, bibliographic references, or attribution appropriate to the output profile.
2. **Inspect the evidence:** where rights and access permit, follow a claim to the specific original source version and passage that supports it, and see whether the claim is a quotation, a report, an interpretation, or an independently corroborated assertion.

The intended trace is:

```text
Output clause or displayed relation
 → selection / obligation / interpretation, as applicable
 → SPP and its support links
 → CIN → SAS
 → source version → exact evidence segment / anchor
 → verified capture (if one exists) and original bibliographic identity
 → publisher/custodian link, archived locator, or access-status explanation
```

If the evidence only supports a claim that one source *reported* another, the chain must stop at what was inspected. **Never jump from a secondary quotation to an unverified primary original.**

Reader-facing citations may show title, creator, publication, edition, date, stable identifier, URL, language, and access date as applicable. Where useful, provide a small authorized excerpt and a jump to the exact passage; if the original is inaccessible, state the access limitation rather than offering a broken or invented passage link. A preview excerpt must not quietly replace the full context needed for interpretation.

A generated article can cite many source versions. Conversely, an original source can support many atoms, molecules, and outputs. Both directions should be inspectable. The source bibliography and citation graph remain part of the knowledge environment, not decorative footnotes at the bottom of an article.

**Noopedia's generated output is derived from its evidence.** Registering it as a document for history or version control must not make it a new independent witness for the same claims. A subsequent system that ingests that output should retain or reconstruct its derivation, not treat it as fresh external corroboration.

## 11. Revisions, new evidence, and living descriptions

The same topic can acquire new sources, corrections, retractions, and interpretations. The original source version must remain identifiable; an updated web page cannot retroactively rewrite what an earlier version said. Corrections to extraction or interpretation should be tracked without silently changing an original capture.

When a claim or its source changes, the system should assess effects on selected knowledge, molecular groupings, dependencies, and derived outputs. New facts can change **which material is important and how it is best explained**, not merely replace a number in an otherwise frozen article.

The goal is **selective impact analysis and controlled recompilation**, using existing dependency and review mechanisms. A new article should record which source/knowledge snapshot, template policy, major ordering decisions, and verification results produced it. Older outputs may need visible stale/withdrawn status but should remain historically auditable where policy allows.

This is consistent with Noopedia's principle of continuity: revisions do not erase the existence of earlier interpretations or their historical significance.

## 12. Rights, authorship, and ethical constraints

Noopedia distinguishes **using knowledge** from **reproducing a protected expression**. The fact that an atom refers to a publicly accessible book does not establish a right to copy that book, publish its text, retain an unrestricted local archive, or recreate a near-verbatim translation. The status of facts, compilations, quotations, transformations, database rights, moral rights, and text/data-mining exceptions can depend on jurisdiction, license, source type, and manner of use.

Therefore:

- retain and process source content only when the relevant permission or lawful basis has been established;
- preserve source authorship, edition, citation, and attribution obligations independently of whether the generated text looks different;
- respect limits on verbatim quotations, closely imitative paraphrases, translation, protected media, and substantial extraction or reuse of protected compilations;
- separate source licenses and permission conditions from the project's own output license, which must be determined by a defensible source-by-source and output-specific policy;
- distinguish open bibliographic metadata from a restricted full-text capture; neither should be misrepresented as the other;
- account for private, confidential, sensitive, or personal information, including deletion or restricted-access obligations, rather than making every extracted item public;
- record disputes, corrections, and takedown outcomes with the minimum retained data that policy and law permit.

Historical source-and-licensing documents contain specific project proposals. This conceptual document **does not silently adopt every earlier licensing assertion as a settled legal rule**; actual source ingestion and publication should be checked against current policy and applicable rights.

## 13. Verification and evaluation

Noopedia should test more than whether generated text reads naturally. Different objectives require independent measures:

| Dimension | What must be tested |
| --- | --- |
| **Extraction coverage** | Did the system capture the relevant supported content without ignoring secondary subjects, relations, modality, or discourse context? |
| **Semantic fidelity** | Were referents, attribution, negation, time, conditions, operator scope, and limitations preserved? |
| **Evidence and citation integrity** | Can every material claim trace to the actual inspected source/version/passage? Are unavailable originals clearly flagged? |
| **Epistemic restraint** | Were unsupported conclusions, circular corroboration, modality inflation, and false consensus avoided? |
| **Molecular grouping** | Are explanatory groups coherent, useful, and faithful to relationships in the evidence? |
| **Template sensitivity** | Do different tasks and audiences produce genuinely different useful compositions from substantially shared knowledge? |
| **Coverage and diversity** | Are critical topics, contrary views, edge cases, and scoped gaps visible where required? |
| **Narrative coherence** | Are sections, prerequisites, transitions, chronology, and causal explanations understandable without fabricating relationships? |
| **Original-expression boundaries** | Does the output avoid passing off generated prose as a source quote and respect source-expression reuse limits? |
| **Reproducibility and updates** | Can a selected output be traced to its inputs and recalculated when relevant sources or policies change? |

Useful experiments include: (a) two output templates over one frozen source cohort; (b) two different genres with comparable epistemic checks; (c) changing one source and measuring affected outputs; (d) a citation to an unavailable primary source; (e) a source with essential argumentative dependencies; (f) an expressive work where a factual synopsis must be distinguished from the original text; and (g) an adversarial example in which two paraphrases of one source are falsely presented as independent confirmation.

A good baseline is a **source-reviewed reference set**, with explicit intended claims and material omissions. The first model's output must not become the reference truth simply because it is the first output. Independent checks can identify some errors, but agreement between models alone is not proof of fidelity or truth.

## 14. Open research questions

The following questions intentionally remain open:

1. **What is the smallest meaningfully reusable unit?** When do relations, qualifiers, discourse structure, or source-level annotation carry information that a simple atom misses?
2. **How can narrative and argument dependencies be represented with minimal machinery?** Which are already expressible by existing SAS/CIN/SPP, source anchors, and relations?
3. **How should a system detect coverage gaps?** Which questions follow from entity types or explanations without being mistaken for stored facts or global ignorance?
4. **How can molecule formation be evaluated?** Can topic-specific relevance, explanatory importance, and coherence be measured independently of factual correctness?
5. **What is the right degree of templating?** How can templates provide structure without making every article formulaic or forcing unsupported sections?
6. **How can prose generation remain source-faithful?** What pre-generation plans and post-generation checks reduce invented transitions and causal stories?
7. **How should authorial order be respected?** What is lost when a literary or scientific argument is represented as a flat set of claims?
8. **What level of source access is enough for verification?** How should unavailable editions, changed pages, citations to uninspected originals, and rights-restricted evidence be handled?
9. **How should multiple languages interact?** How can cross-language semantic identity be tested without suppressing untranslatable concepts and edition-specific differences?
10. **How should updates propagate?** Can relevance discovery and selective recompilation catch newly important material, not only invalidate already known dependencies?
11. **What constitutes a successful representation?** Beyond grammatical prose, how should understanding, coverage, explanation, and reader ability to inspect evidence be assessed?
12. **Where does the model of atoms and molecules stop being adequate?** Which counterexamples justify changing it rather than endlessly adding special cases?

No single experiment answers all of these questions. The preferred method is to formulate bounded examples, freeze their sources and evaluation criteria, compare alternatives, and retain negative as well as positive results.

## 15. Architectural guardrails and future development

This document extends the interpretation of Noopedia's existing disassembly/assembly direction; **it does not authorize a new database, a second semantic engine, a fixed universal article outline, or automatic publication of generated narratives**. Any proposed persistent structures, new admission obligations, or independent article compiler must be justified through concrete counterexamples, regression evidence, and maintenance analysis.

A sensible research progression is:

1. Inventory the ordering and source-link information already retained by the current source registry, SAS/CIN/SPP, citation graph, and compiler planning flow.
2. Construct a small, rights-cleared corpus spanning ordinary descriptions, argument-heavy texts, and expressive material; define source-reviewed reference cases and adversarial controls.
3. Produce two or more substantially different output plans from the same validated knowledge set, without re-extracting it for each output.
4. Inspect source-to-clause traceability, meaningful dependency preservation, coverage, and language quality; quantify misleading omissions and unsupported transitions.
5. Test how a changed or newly added source affects selection, molecule formation, ordering, and older outputs.
6. Consider new technical mechanisms only for failures the existing architecture cannot address economically and safely.

The long-term goal is not to eliminate original texts or enforce one way of telling a story. It is to let **sources remain sources, knowledge remain inspectable and reusable, and representations remain open to purposeful recomposition and criticism**.

## 16. TS001: unsequenced cross-source narrative assembly (planned test)

The first dedicated experimental program for this idea is **TS001 — Cross-Source Knowledge-to-Narrative Assembly**. It asks whether **unsequenced atoms extracted from different, separately attributed source versions** can be selected, grouped and written into original coherent explanations without copying any source's exposition order and without adding unsupported facts. It is not enough to show that an LLM writes fluent prose from a single summarized article.

The ten registered subtests are `TS001.01` (corpus/input integrity), `TS001.02` (order independence), `TS001.03` (template sensitivity), `TS001.04` (cross-source assembly), `TS001.05` (evidence/citation integrity), `TS001.06` (semantic constraints), `TS001.07` (MPOV/history of understanding), `TS001.08` (blind baseline comparison), `TS001.09` (source updates/replay), and `TS001.10` (negative controls). The [test registry](RESEARCH_TESTS_AND_RESULTS.md) records the subtests, evaluation requirements, and observed outcomes.

**Evidence status: `NOT_RUN`.** Preparing the protocol does not establish that Noopedia can carry out these operations in a working system.

**Mandatory result propagation:** every concluded TS001 run, including `FAIL`, `PARTIAL` or `INCONCLUSIVE`, must update **this main document** with a dated, source-scoped finding and the limits of the claim; update the [canonical results register](RESEARCH_TESTS_AND_RESULTS.md) with all ten dispositions and auditable evidence links; update the [atom model](KNOWLEDGE_ATOMS_AND_STRUCTURAL_MODEL.md) for established lessons and the [technical foundations](TECHNICAL_FOUNDATIONS.md) only for demonstrated runtime behavior. The published findings must remain linked to retained raw evidence and independent reviews; an unverified summary is not sufficient to close TS001.

## Related documentation and source background

- [Knowledge Atoms and Structural Model](KNOWLEDGE_ATOMS_AND_STRUCTURAL_MODEL.md) — preliminary logical anatomy and traceable interpretation model.
- [TS001 — Research Tests and Results](RESEARCH_TESTS_AND_RESULTS.md) — named subtests, publication obligation, and current evidence status.
- [Project Description and Philosophy](PROJECT_DESCRIPTION_AND_PHILOSOPHY.md) — why Noopedia investigates a different organization of human knowledge.
- [Semantic and Epistemic Principles](SEMANTIC_AND_EPISTEMIC_PRINCIPLES.md) — meaning, support, uncertainty, and non-inflation during assembly.
- [Context-Dependent Ranking and Molecular Assembly](TEMPLATE_DRIVEN_RANKING_AND_MOLECULAR_ASSEMBLY.md) — relevance, grouping, output templates, coverage, and ordering.
- [Knowledge Lifecycle and Architecture](KNOWLEDGE_LIFECYCLE_AND_ARCHITECTURE.md) — source, semantic, composition, and presentation layers.
- [Technical Foundations](TECHNICAL_FOUNDATIONS.md) — shared SAS/CIN/SPP concepts and source-aware implementation boundaries.
- [MPOV — Multiple Perspectives](MPOV_MULTIPLE_PERSPECTIVES.md) and [Evolution of Understanding](EVOLUTION_OF_UNDERSTANDING_IN_ARTICLES.md) — situated projections and historical shifts in understanding.

**Research boundary:** These are intended principles and evaluation directions, not a claim of implemented lossless atomization, complete source archiving, universally verified claims, or production-ready narrative generation.
