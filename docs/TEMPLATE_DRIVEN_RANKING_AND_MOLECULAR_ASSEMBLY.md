# Noopedia — Context-Dependent Knowledge Ranking and Molecular Assembly

**Document role:** guiding requirements for contextual selection, grouping, prioritization, and ordering.  
**Implementation status:** a design principle and evaluation target, not proof of a deployed end-to-end ranking mechanism.

## 1. Core principle

**Atomic knowledge in Noopedia does not have one universal, permanent importance rank.**

An atom's relative importance is determined by the purpose for which it is used, its semantic context, the selected representation template, and its relationships with other knowledge.

The same set of atoms may be used to construct an encyclopedic article, a scientific review, a chronology, a spatial Noo Atlas representation, a Noo-View semantic graph, or other forms.

The original content, provenance, epistemic status, modality, qualifiers, and material semantic relations must be preserved.

**Ranking is a property of contextual assembly, not a property of the atom itself.**

## 2. Automatic formation of molecules

The transition from atoms to molecules should be predominantly automatic.

A **molecule** is a meaningful composition of interrelated atoms brought together in a particular context.

Molecule formation involves:

1. Identifying atoms relevant to the task.
2. Identifying semantic and structural relationships among those atoms.
3. Grouping atoms by events, objects, processes, time, causal relations, and other relationships.
4. Preserving material restrictions, dependencies, conditions, and epistemic characteristics.
5. Determining the relative importance of the resulting groups and their constituent atoms.
6. Ordering molecules according to the requirements of the representation.

Selection, grouping, and ranking can influence one another; they do not have to occur strictly once in a fixed sequence.

However, semantic compatibility and the evidential validity of relationships must not be determined by relevance or importance scores alone.

## 3. The role of templates

A **template** specifies the purpose and organizing principles of a knowledge representation.

It may define:

- output type: article, chronology, map, graph, or comparative review;
- target audience and required level of detail;
- preferred kinds of semantic relationships;
- rules for forming sections and groups;
- relevance and relative-importance criteria;
- length restrictions;
- rules for chronological, causal, thematic, or spatial ordering;
- requirements for displaying uncertainties, contradictions, and sources.

A template must not contain a preselected sequence of specific atoms for every object.

Instead, it defines a general policy that can be applied automatically to different knowledge sets.

The same atom may receive different ranks depending on the template, task, and context.

## 4. Multi-level ranking

At least three operations must be distinguished.

### 4.1. Atom relevance

This indicates how necessary or useful an atom is in a specific context.

Relevant signals may include:

- its relationship to the principal subject or question;
- semantic proximity to the topic;
- participation in important events and relationships;
- necessity for understanding other atoms;
- uniqueness and informational novelty;
- spatial and temporal relevance.

**Relevance is not truth.**

### 4.2. Molecule importance

This indicates the role of a meaningful group in the overall representation.

A molecule may be central, introductory, explanatory, qualifying, comparative, evidential, or supporting.

Its importance depends on the relationships among its atoms, not merely the properties of the atoms in isolation.

Molecule importance must not automatically be calculated as a simple sum of its atoms' ranks.

### 4.3. Presentation order

After determining relevance, the system must establish an order for written exposition or visual presentation.

Ordering may depend on chronology, causal dependencies, explanatory logic, spatial relationships, and template structure.

A high rank alone does not imply that an element should be presented first.

For example, a necessary premise may need to precede a more important conclusion.

**No atom inherits a globally mandatory position from the order in which its source happens to narrate it.** The original's paragraph/chapter order must remain recoverable as source information, while chronology, logical dependency, causality, and disclosure order remain available as semantic constraints when they matter. The output template chooses a purposeful arrangement without erasing those distinctions. [Original Sources, Atomization, and Narrative Assembly](SOURCES_ATOMIZATION_AND_NARRATIVE_ASSEMBLY.md) develops this principle and explains why template-driven prose is not verbatim reconstruction.

## 5. Constraints on automatic ranking

The ranking algorithm must not:

- change the meaning of atoms;
- strengthen modality or epistemic status;
- turn a source-supported assertion into an independently verified fact;
- replace importance with the number of repetitions across sources;
- delete material conditions or constraints to make the text shorter;
- merge incompatible assertions without explicitly representing the contradiction;
- hide uncertainty essential for understanding;
- violate causal or temporal dependencies to satisfy a higher score.

The **admissibility of knowledge for use** and its **relative importance in a particular representation** must remain separate questions.

A low rank does not mean that knowledge is false.

A high rank does not mean that knowledge is true.

Numerous sources do not automatically constitute independent corroboration.

## 6. Coverage and informational diversity

Automatic assembly must account not only for the highest relevance of individual items but also for adequate coverage of the subject.

Several similar or repetitive atoms must not crowd out less frequent but fundamentally important knowledge.

The algorithm should consider:

- coverage of the main aspects of the topic;
- informational redundancy;
- dependencies of later statements on earlier ones;
- contextual information needed for correct interpretation;
- the presence of material contradictions;
- gaps and unknown values relevant to the selected template.

An abbreviated representation may omit secondary details, but it must not create a false impression of certainty or completeness.

## 7. Automation and human involvement

Manually ranking atoms for each separate article is not Noopedia's primary operating model.

By default, the system should independently group, select, rank, and assemble knowledge according to the chosen template.

People may create and modify templates, set presentation goals, select an audience, and, where needed, specify editorial constraints.

These settings must not change the canonical content of the source atoms.

Editorial intervention, where allowed, must be distinguishable from automatic results and must not serve as evidence that the underlying knowledge is factually correct.

## 8. Reproducibility and explainability

For automatic assembly, it must be possible to reconstruct:

- which original atoms and source versions were used;
- which molecules were formed;
- which template and template version were applied;
- why elements were selected, excluded, or assigned a particular relative priority;
- which semantic and structural constraints influenced the final order.

Complete determinism of generated language is not required, but decisions about selection and material ordering must be auditable.

If LLM-based ranking is used, its decisions must remain separate from structural constraints and be tested for regressions, omissions, unjustified strengthening, and instability.

## 9. Architectural principle

Contextual ranking and molecular assembly are functions of Noopedia's existing architecture.

This does **not** require a permanent global atom rank, a separate semantic database, a new article engine, or an additional durable record kind.

Ranking must happen in the context of a particular assembly using existing atoms, relations, metadata, and representation configuration.

The existing **D11 article compiler** should be treated as the first candidate for implementing these principles in encyclopedic articles.

Common grouping and ranking rules should, where possible, be reused by other Noopedia views, without creating parallel incompatible mechanisms.

Any architectural extension requires demonstrated necessity, quality assessment, and consideration of current and future maintenance costs.

## 10. Verification criteria

The quality of automatic molecular assembly should be evaluated on these independent dimensions:

1. **Semantic fidelity** — whether the original atoms' meanings are preserved.
2. **Relevance** — whether selected knowledge matches the purpose of the representation.
3. **Coverage** — whether essential aspects of the subject are included.
4. **Coherence** — whether knowledge is logically grouped and ordered.
5. **Non-redundancy** — whether unjustified repetition is avoided.
6. **Epistemic integrity** — whether sources, restrictions, uncertainties, and contradictions are preserved.
7. **Reproducibility** — whether ranking decisions can be explained and reconstructed.
8. **Template sensitivity** — whether different templates genuinely produce different yet semantically correct results.

**Desired Noopedia property:** one universal corpus of atomic knowledge that automatically forms different meaningful compositions and representations without changing the original knowledge.

---

**Implementation boundary:** These principles are design and evaluation criteria, not evidence that an automatic ranking pipeline already meets them. They do not mandate a new database schema.

## Cross-source narrative feasibility research

Context-dependent grouping and ranking are design principles rather than proven narrative-generation quality. The [TS001 experiment](RESEARCH_TESTS_AND_RESULTS.md) tests whether an unordered cross-source atom pool can be assembled into distinct, faithful texts under different output templates, with independent review and negative controls. **Current evidence status: `NOT_RUN`.**
