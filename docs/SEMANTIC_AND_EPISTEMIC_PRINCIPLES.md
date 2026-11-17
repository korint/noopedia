# Noopedia — Semantic and Epistemic Principles

**Document role:** guiding semantic and epistemic requirements.  
**Relationship to implementation:** constraints on the existing architecture; not a mandate for new database tables, ontologies, or services.

## 1. Semantic content

Noopedia distinguishes the original linguistic expression, its contextualized semantic content, referents, and the relationships between them.

Semantic equivalence cannot be established solely by matching words or by the identity of entities.

Atomization must preserve semantic roles, conditions, operator scope, modality, attribution, and uncertainty.

## 2. A universal semantic engine

Noopedia uses a shared semantic core based on the existing **SAS/CIN/SPP** representations.

Different source genres and functions may require different ways of interpreting content, but this does not imply separate atomization engines by default.

A **source profile** provides an interpretive context; it is not a basis for certifying truth.

Specialization is permissible only when its necessity has been demonstrated, taking into account both the initial implementation cost and the future cost of maintenance.

## 3. Types of content

A source may contain factual assertions, observations, hypotheses, instructions or prescriptions, questions, evaluations, quotations, reports of other people's beliefs, and other semantic constructions.

The system must not automatically turn an instruction into an event that occurred, a hypothesis into an established result, a source's statement into an objective fact, or ambiguity into definite knowledge.

The existing `modality`, `stance`, `qualifiers`, `statuses`, and `provenance` mechanisms must be used to preserve these distinctions.

## 4. Epistemic justification

Three different questions must be distinguished:

- **Semantic fidelity:** Has the intended semantic content been represented correctly?
- **Source support:** Is the specific assertion supported by the specific source?
- **Epistemic warrant:** What grounds exist for accepting the assertion as knowledge about the world?

A source can demonstrably contain a false statement. Complete source traceability does not establish the truth of its content.

No local source-admission decision may automatically become world verification.

## 5. Preservation of history and uncertainty

Noopedia preserves provenance, argumentation, contradictions, changes, and the boundaries of what is known.

Historically false statements, contested hypotheses, and uncertain information may have research value in their own right.

Preserving that material does not mean publishing it as established encyclopedic fact.

## 6. Reverse assembly

Every representation of knowledge—whether an encyclopedic article, Noo-View, Noo Atlas, or another output—must preserve the material semantic and epistemic constraints of the originating atoms.

Reverse assembly must not silently strengthen modality, change referents, drop conditions, remove attribution, or conceal material uncertainty.

**Reverse assembly is not the verbatim recovery of an original work.** Source expression, authorship, original order, and version-specific evidence must remain independently inspectable where permitted. An output may choose a different narrative sequence, but only while respecting meaningful temporal, logical, argumentative, or narrative dependencies. See [Original Sources, Atomization, and Narrative Assembly](SOURCES_ATOMIZATION_AND_NARRATIVE_ASSEMBLY.md).

## 7. Engineering principle

These principles establish invariants for the existing architecture; they do not, by themselves, require new tables, permanent record types, an ontology, or separate engines.

Any change to the schema or a mandatory admission path requires concrete counterexamples, a measured benefit, and independent regression verification.

---

**Implementation boundary:** These principles describe intended behavior; they do not establish that every behavior has been implemented. See [Documentation Scope](DOCUMENTATION_SCOPE.md).

## Atom structure and empirical verification

The [initial knowledge-atom model](KNOWLEDGE_ATOMS_AND_STRUCTURAL_MODEL.md) consolidates the semantic roles already required by these principles without creating new storage contracts. [TS001](RESEARCH_TESTS_AND_RESULTS.md) is the named, currently **unexecuted** research program for testing whether an unordered, multi-source set of such atoms can form coherent, traceable narratives. Any observations, including failure, must be reflected in the main `/docs/` evidence registry.
