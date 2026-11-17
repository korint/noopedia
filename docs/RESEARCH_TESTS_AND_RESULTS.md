# Noopedia — Research Tests and Recorded Results

## Purpose

Noopedia proposes that evidence-grounded knowledge can be stored independently of the exposition order of individual source texts and recomposed into different meaningful presentations. This is a **research claim to test**, not a demonstrated universal capability. This document is the **canonical, user-readable registry of research-test plans and observed outcomes**. Conclusions, including failed and inconclusive outcomes, must be recorded **here in `/docs/`** and supported by traceable run evidence.

## TS001 — Cross-Source Knowledge-to-Narrative Assembly

**Question:** Can Noopedia generate coherent, substantively accurate, traceable texts from unordered, differently sourced knowledge atoms, without reconstructing an original article, hiding contradictions, or introducing unsupported meaning?

**Scope:** Initial controlled study of atom-based multi-source assembly for encyclopedia descriptions, historical narratives, and histories of understanding. It tests the [knowledge-atom conceptual model](KNOWLEDGE_ATOMS_AND_STRUCTURAL_MODEL.md) and the [original-sources / narrative-assembly principles](SOURCES_ATOMIZATION_AND_NARRATIVE_ASSEMBLY.md); it does not automatically establish production readiness.

**Current status: `NOT_RUN`** — a protocol and result-recording contract have been prepared, but no TS001 trial results are represented by this documentation package.

| Subtest | Short name | Primary question | Result |
| --- | --- | --- | --- |
| **TS001.01** | Corpus and input integrity | Are source versions, atom candidates, semantic gold and source independence recorded and verifiable? | `NOT_RUN` |
| **TS001.02** | Order independence | Does shuffling atoms change factual content or only acceptable composition? | `NOT_RUN` |
| **TS001.03** | Template sensitivity | Can the same atom pool yield distinct, valid narrative forms and coverage choices? | `NOT_RUN` |
| **TS001.04** | Cross-source assembly | Can a synthesis use relevant claims from different sources without relying on a pre-existing article? | `NOT_RUN` |
| **TS001.05** | Provenance and citation | Are generated claims actually supported by exact, independently inspectable source evidence? | `NOT_RUN` |
| **TS001.06** | Semantic-constraint preservation | Are negation, modality, time, causality, attribution, conditions and referents preserved? | `NOT_RUN` |
| **TS001.07** | MPOV and changing understanding | Can different perspectives and historical changes be represented without flattening disagreements? | `NOT_RUN` |
| **TS001.08** | Blind comparison | How does atom-based writing compare with a source-direct baseline under independent evaluation? | `NOT_RUN` |
| **TS001.09** | Updates and reproducibility | Does a changed source affect the right outputs without losing earlier evidence and conclusions? | `NOT_RUN` |
| **TS001.10** | Negative and adversarial controls | Does the system reject misleading combinations, missing evidence and false causal or temporal connections? | `NOT_RUN` |

### What counts as a result

For each execution, report **both** claim-level correctness and narrative usefulness, not a single opaque score. At minimum record:

1. Source/corpus manifest, license and access conditions, source/version identifiers, origin families, input atom inventory, unresolved/held candidates and a frozen review set.
2. Execution manifest: code commit if available, models, prompts and parameters, templates, shuffle seeds, exact input hashes, environment and cost/latency when measurable.
3. Atom-level source-support and coverage denominators; generated factual claims with claim→atom→SAS/CIN/SPP→source version/evidence trace, including unsupported claims.
4. Fidelity errors (referent swaps, polarity, modality, condition, time, causation, attribution), omissions, contradictions and citation failures.
5. At least two separately assessed outputs for each required template, blinded evaluators, disagreements and adjudication records, and comparison with the declared baseline.
6. Result for **each** TS001 subtest: `PASS_SCOPED`, `PARTIAL`, `FAIL`, `INCONCLUSIVE`, or `NOT_RUN`; separately state the global disposition and what remains untested.

The test program requires documented case selection, controls, review instructions, acceptance criteria, and a traceable result record for each run. A defined protocol is **not a test result**.

### Mandatory publication and revision rule

**Every concluded TS001 run, including a failed, partial, or inconclusive run, must be recorded in the published documentation:**

1. **`docs/RESEARCH_TESTS_AND_RESULTS.md` (this file):** set the global status, populate every subtest's result, summarize measured denominators, failure modes, limitations and evidence links; record exact run IDs and the assessed source/code/model scope.
2. **`docs/SOURCES_ATOMIZATION_AND_NARRATIVE_ASSEMBLY.md`:** update the TS001 evidence section with what the run establishes or fails to establish about unordered, cross-source narrative assembly. Do not describe a hypothesis as proven.
3. **`docs/KNOWLEDGE_ATOMS_AND_STRUCTURAL_MODEL.md`:** record any demonstrated implications for logical atom structure or unresolved representation gaps. Do not turn a small pilot into an unreviewed permanent-schema change.
4. **`docs/TECHNICAL_FOUNDATIONS.md`:** update the tested implementation boundary and constraints, if the run actually tested them.
5. **Evidence retention:** retain complete test inputs, independently reviewed outputs, negative controls, and exact run manifests so the published summary can be audited.

The summary must distinguish **source fidelity, source support, epistemic warrant, narrative coherence and product readiness**. A passing presentation test cannot automatically authorize world-fact verification, schema modification or production release. Do not delete negative controls or replace the baseline after viewing results without documenting an explicitly new run.

### Result summary — pending experiment

| Measure | Observed | Interpretation |
| --- | --- | --- |
| Tested real source cohorts | Not run | No real corpus evaluated under TS001. |
| Evaluated generated outputs | Not run | No blinded comparison measured. |
| Claim-level source support | Not measured | Cannot infer factual accuracy. |
| Evidence/citation integrity | Not measured | Cannot infer traceability in generation. |
| Semantic constraint violations | Not measured | Cannot infer safe reconstruction. |
| Essential content coverage | Not measured | Cannot infer completeness. |
| Independent narrative-quality scores | Not measured | Cannot infer coherence. |
| Global TS001 conclusion | **`NOT_RUN`** | Protocol prepared; empirical conclusion pending. |

See also [documentation evidence boundaries](DOCUMENTATION_SCOPE.md): implementation status, experimental success and philosophical ambition are distinct categories.
