# Noopedia@home — Distributed Knowledge Processing and Independent Verification

**Document role:** project-level technical concept and research proposal.  
**Status:** PROPOSED — NOT IMPLEMENTED OR APPROVED FOR PRODUCTION.  
**Scope:** volunteer-funded AI requests, independently executed Python workers, reference calibration, redundant candidate generation, and independent source-grounded verification.  
**Architecture boundary:** this adds a possible execution-and-verification layer around Noopedia's existing SAS/CIN/SPP and admission path. It does **not** introduce a second knowledge model or grant volunteers authority to publish facts.

## 1. Vision: SETI@home for evidence-linked knowledge

Noopedia may eventually need to process a huge amount of source material. Extraction, contextual interpretation, alignment, comparison, and verification may require many AI calls and substantial computing resources. Those costs need not be paid entirely by a single operator.

**Noopedia@home** is a proposed voluntary network inspired by SETI@home: participants contribute either (a) access to paid AI computation or (b) actual processing performed on machines they operate. The server partitions approved, versioned source material into bounded tasks, dispatches them, records results, and performs controlled validation. The analogy concerns collaborative distributed computing only; it implies no affiliation with SETI or SETI@home.

**The key principle is a separation of resources from authority.** Many people can pay for or execute computations; none of those computations automatically becomes canonical knowledge. Admission remains governed by source evidence, semantic fidelity, provenance, and the project's existing controlled paths.

## 2. Two first-class contribution modes

The following modes are **equally legitimate parts of the proposed system**, not a preferred design plus a distant optional alternative.

### Mode A — Donate API capacity to Noopedia

A volunteer opts in to let the Noopedia coordinator issue calls using an API credential or equivalent provider-granted authorization allocated to this purpose. The coordinator chooses and runs permitted tasks against supported AI providers on the volunteer's behalf. The contributed capacity can fund:

- the **first** candidate processing run;
- the **independent second** processing run;
- **final server-controlled source-grounded verification** or adjudication;
- calibration, regression, or randomized audit cases, within the contributor's declared policy.

No Python client is required for this mode. The coordinator keeps the volunteer's credential isolated from other volunteers and workers. A donated key is a **funding and execution resource**, not a vote or a guarantee of independent reasoning. Different donors may be using the same model behind the same provider.

This mode needs an explicit security and consent mechanism before implementation: purpose-bound opt-in; provider and model allowlists; spend/token/concurrency ceilings where enforceable; visible estimated and actual usage; immediate suspension and credential revocation; secret storage isolated from logs and results; a verifiable audit trail; and provider-terms compliance. Prefer revocable, restricted, project-specific credentials over a donor's general-purpose key. **A server-side application cannot guarantee a hard spending cap if the provider does not enforce one**; software-side controls and alerts reduce, but do not eliminate, financial exposure. Never imply that sending a plain API key to a server is risk-free or request secrets in issue trackers or public forms.

### Mode B — Run a local Python worker

A volunteer installs a small open-source Python worker and keeps any API credential **only on their own machine**, or uses a locally hosted model. The worker contacts the Noopedia coordinator via authenticated HTTPS, negotiates its protocol and capability versions, requests eligible tasks, executes them, and submits structured output with source references and execution metadata.

The coordinator never needs the user's private API key for this mode. The worker may run manually, periodically, or continuously, subject to contributor-defined limits. No task should require running untrusted executable code from the server: tasks are **data and versioned processing specifications**, not arbitrary scripts.

For later research, institutional installations may operate dedicated workers or inference services under the same candidate-submission and evidence rules. These do not need a separate epistemic architecture.

### Hybrid operation

All roles can be mixed per task. For example, Worker A may be a remote Python volunteer, Worker B a server-side call funded by a donated key, and the final reviewer another server-side call funded by a different volunteer or by Noopedia itself. Alternatively, both candidates may be produced through centrally managed contributed API keys, or both by local workers. The server selects the combination under its independence, rights, availability, and cost policies.

## 3. Reference first: a frozen one-key baseline and a reviewed gold set

A production-sized volunteer network should not begin by processing arbitrary material. First create a **small, frozen, rights-cleared benchmark** whose source revisions and interpretation requirements are known.

**Step 1 — One-key reference run.** Use one Noopedia-controlled API key to execute the current agreed pipeline on that benchmark with fixed prompts, model identifier, settings, schema, and source versions. Record exact input and output identifiers, latency, errors, token usage, model metadata, and approximate cost. This creates a reproducible **reference behavior and cost baseline**, not an objective truth standard.

**Step 2 — Independently reviewed gold set.** Check source passages and expected interpretations separately. Reviewers should verify semantic roles, attribution, negation, modality, temporal scope, qualifiers, provenance, source support, and expected HOLD/REVIEW outcomes. Include counterexamples and cases known to fool models. The result is a versioned **golden evaluation set**, including negative controls and held-out tasks. A first model answer becomes gold **only where separately justified by source evidence and the evaluation contract**.

**Step 3 — Qualify executors and validators.** Before trusting a new worker version or provider/model route, test it against public calibration cases and separately withheld cases. Record failures as well as successes. Changes in model, provider behavior, prompts, source-anchoring, schema, or worker version may require requalification.

The purpose is not to demand exact string equality with a single model. Two semantically equivalent valid representations may differ in formatting; a superficially matching answer may still be wrong.

## 4. The proposed normal task lifecycle

Every task must identify an **approved source and exact revision**, and must be eligible for whichever third-party processing and redistribution are planned. The default initial policy is **two blind independent candidate executions, followed by a distinct server-controlled verification step**.

```text
    Approved source + revision + legal eligibility
                        |
        Immutable task / schema / prompt versions
                        |
       +----------------+----------------+
       |                                 |
  Candidate run A                   Candidate run B
  donated API key                   local Python worker
  or local worker                   or donated API key
       |                                 |
       +----------------+----------------+
                        |
             Server contract checks
      (source IDs, spans, hashes, schema, qualifiers,
       identity, provenance, versions, duplicate/replay)
                        |
       Independent result comparison
   (meaning, scope, modality, citations, omissions)
                        |
             agree? / disagree?
               /              \
       agree                  disagree/uncertain
         |                           |
  Server-controlled            HOLD; alternate worker,
  independent review           independent adjudication,
  against original source      or human review
         |                           |
    reviewed candidate       no automatic acceptance
         |
  Existing Noopedia admission / review / publication gates
         |
   Canonical SAS / CIN / SPP and allowed downstream views
```

The modes shown for A/B are illustrative; assignment is flexible. If A and B disagree on a material assertion, the result must be held. A tie-breaker may use a third independent execution, but **2-out-of-3 majority voting must never substitute for verifying claims against the source**.

If A and B agree, the coordinator invokes a **separate verification role**, which may use an project-operated key, a **donated API key managed by the server**, or a qualified local validator where policy allows. This reviewer sees the source passage and evidence anchors; it must check the proposed assertions rather than rubber-stamp the fact that two runs agreed. Depending on risk, verification may combine deterministic checks, a distinct model family or prompt, source-based counterexample probes, human review, or a stronger pre-existing admission gate.

The outcome is a reviewed *candidate* for the current admission system. Even an agreed, source-supported proposition is not automatically an independently verified fact about the world.

## 5. What constitutes independent work?

**Different API keys do not necessarily produce independent evidence.** Keys can belong to different owners but call the same provider, model, snapshot, prompt, or shared upstream service. Likewise, two Python workers can copy one another's outputs, and two different model families can share systematic errors.

To make redundancy meaningful, track at least:

- distinct execution IDs and independent task leases, with no prior candidate disclosed before the second submission;
- contributor/worker identity or trust domain, without exposing unnecessary personal data;
- provider, model family, exact model identifier or reported revision, processing route, prompt and schema versions;
- output and evidence hashes, task/shard version, timestamps, retry lineage, and validator identity;
- whether a validation run was **separate from generation**, and whether the reviewer used independent source context and instructions.

For valuable or high-risk tasks, prefer diversity across models/providers and validator roles. Where only one provider is accessible, classify two runs as **redundant but correlated**; do not label them strongly independent. Keep the quality threshold tied to demonstrated error rates on the reviewed golden set and ongoing audits.

**Agreement is a trigger for deeper verification, not proof.** If a source says “the newspaper alleged that X happened,” and two models report “X happened,” they agree with each other but both erase attribution. Both must be rejected or held. The same applies to lost qualifiers, inverted negation, changed referents, unsourced dates, invented causality, or unsupported citizenship inferences.

## 6. A small Python worker and versioned protocol

A minimal open-source Python client is sufficient to pilot Mode B. It need not know how to alter Noopedia's internal database. Its responsibility is to **execute permitted task kinds and return auditable candidate outputs**.

Conceptual message flow (endpoint names are illustrative, **not existing APIs**):

1. **HELLO / capability negotiation.** The client authenticates and reports `worker_version`, `protocol_version`, supported `task_kinds`, `schema_versions`, `prompt_bundle_versions`, `model_provider`, `model_id` or local-model capability, concurrency, and optional resource restrictions. The server responds with accepted versions and eligibility, or rejects an incompatible client with an upgrade instruction.
2. **CLAIM / lease.** The client requests a task; the coordinator assigns only compatible, rights-eligible work and sends `task_id`, `task_revision`, an expiring lease token, exact `source_version` and `source_hash`, bounded source context or a permitted fetch reference, a frozen prompt/configuration identifier, and the output contract. The system must honor contexts too large to be cut without losing semantic scope.
3. **EXECUTE.** The worker runs a local model or provider call using local secrets, with explicit timeouts, provider/model metadata, cost ceilings, and no executable instructions from the source text.
4. **SUBMIT.** The client sends the task ID, lease and run identity, versions, a structured candidate with precise source evidence anchors, declared uncertainty/HOLD signals, model metadata, execution diagnostics, and input/output hashes. **It never submits API secrets**.
5. **ACK / heartbeat / retry.** The coordinator returns a durable acknowledgement or a validation rejection. Expired or failed leases can be reassigned safely; duplicate submissions remain identifiable and idempotent. A heartbeat may extend a lease for long tasks but must not permit indefinite monopolization.

Local worker configuration should include contributor-selected provider or model, max spend/tokens per day, allowed task categories, whether network-derived source data can be processed under the relevant rights, a local pause switch, and an update policy. An automatic software update should never silently execute new code without a trustworthy release process and the participant's consent.

**Minimal coordinator-side functions:** task queue and lease registry, protocol/version policy, worker capability matching, contribution-budget routing, immutable source manifests, result quarantine, run/provenance registry, pairing and independence classifier, verification scheduler, and existing admission bridge. These are *conceptual responsibilities*, not authorization to add durable tables or services prematurely. Evaluate whether current workflow and record structures can host them first.

## 7. Server-side donated-key pool

Mode A needs a **central execution broker** that can issue selected provider requests on Noopedia's behalf without publishing credentials to clients. A user should be able to authorize only specific purposes: e.g., extraction only, independent second pass only, final verification only, or any approved task. Budget policy should also specify a provider/model allowlist, a time window, and per-run limits.

The coordinator chooses eligible contributed capacity for each role but must prevent the same contributor's capacity from being misrepresented as two independent workers simply by rotating keys. It should track effective provider/model diversity and contributor trust domain, and reserve appropriately independent resources for final reviews when possible. The user may revoke authorization immediately for future calls; in-flight provider calls and already incurred costs may not be reversible.

Credential registration and storage are a separate security project. The design must consider leaked secrets, unauthorized spending, excessive billing, impersonation, compromised administrative access, model-provider policy changes, audit and notification, incident response, and data-transfer rights. Use a dedicated secrets mechanism and least privilege; never put raw keys in tasks, candidate records, ordinary logs, or downloadable research archives.

**The project should not collect volunteer credentials before these controls and their residual risks have been reviewed.** This is a genuine architectural prerequisite for Mode A, not a reason to remove it from the overall concept.

## 8. Source-grounded quality controls

The coordinator must reject invalid output **before** invoking a costly semantic reviewer where possible. Examples of deterministic checks include source/version/hash consistency; exact citation spans; input/output schema; nonempty required fields; qualifier types; stable referent and source identities; allowed statuses; prohibited state promotion; and conflicting duplicate/replay claims.

Semantic verification must compare the candidate **to the exact source context**, not merely to a different model's answer. It should preserve distinctions among:

- *semantic fidelity* — did the candidate preserve what the source actually expressed?
- *source support* — can each concrete claim be anchored to that source and version?
- *epistemic warrant* — is there independent justification to treat the claim as world knowledge?

Tasks and outputs that fail rights checks, produce inconsistent spans, lose negation or modality, invent statements, or remain ambiguous must enter HOLD / REVIEW_REQUIRED. No contributor reputation or majority agreement can convert them into accepted facts. Canonical admission, mutation, and publication stay subject to existing Noopedia controls.

## 9. Incentives, throughput, and cost economics

Two candidate runs plus a third independent review cost more computation per task than one unchecked extraction. The point of the voluntary network is that **different contributors can absorb these costs**, allowing Noopedia to scale the amount of *validated* work without concentrating every API bill in one account. There is still real resource usage, and centrally coordinated verification consumes time and budget.

Track **cost per correct, source-grounded admitted assertion**, not only number of tokens or tasks. Measure throughput, error rates, semantic disagreements, false admissions, review escalation, provider diversity, cost distribution, cache reuse, and revocation reliability. Avoid processing unchanged sources again unless new versions or regression evidence justify it.

Contributor dashboards may show resource use, work performed, validation outcomes, and aggregate project progress. Contribution counts must not become evidence-weighting scores or grant authority to set truth. Rewards should not encourage producing large volumes of ungrounded output.

## 10. Threats, privacy, rights, and fair access

Open workers are **untrusted execution nodes**. Risks include copied or fabricated candidates, malicious task clients, replay, collusion, prompt injection in source material, source-version substitution, hidden model upgrades, credential theft, unintended billable calls, and leaking private or licensed inputs.

Only distribute material that may legally and ethically be sent to the chosen model provider or volunteer machine. Data eligible for server-side calls may not be eligible for redistribution to unknown volunteers, and vice versa. Begin with public or clearly redistributable material. Do not forward personal, confidential, or private data merely because someone has volunteered an API key or a computer.

Use authenticated transport, scoped worker identity, server-issued leases, rate limits, result quarantine, selective audits, and signed or independently verifiable worker releases where practical. Never allow a volunteer to issue direct writes into the canonical knowledge store. Never execute arbitrary code delivered as a task manifest. Avoid requiring personally identifying information beyond what is necessary for abuse controls and resource accounting.

## 11. Suggested staged implementation and acceptance experiments

**Stage 0 — One-key baseline and reviewed gold.** Freeze a small rights-cleared corpus, run the existing path with one controlled key, separately review expected results and negative controls, estimate costs, and define stop conditions.

**Stage 1 — Coordinator simulation with two internal executors.** Without changing production admission, prototype task manifests, version negotiation, blind A/B runs, deterministic validators, independent comparisons, and server-controlled final verification. Prove HOLD on disagreements and false agreement cases.

**Stage 2 — Python worker pilot.** Invite a few opt-in local workers, initially on public/redistributable fixtures. Verify lease expiry, retries, client-version mismatch, capability negotiation, reproducibility, secret isolation, malformed data handling, and no unintended canonical writes.

**Stage 3 — Donated-key broker pilot.** Only after a threat review and credential controls are approved, test limited server-side contributed credentials on bounded tasks. Exercise budget policy, revocation, provider failures, billing anomalies, key compromise response, and whether genuinely different model routes reduce correlated errors.

**Stage 4 — Mixed-mode and scaling evaluation.** Pair remote Python and central donated-key runs, perform separate centrally coordinated checks funded by either donated or project capacity, audit agreement and false acceptance, and measure quality-adjusted throughput. Scale only if source rights, semantics, auditability, and operational safety withstand independent evaluation.

**Default pilot acceptance conditions:** every eligible task has two blind separately identified candidate runs; matching submissions are not auto-admitted; review can reject identical but unsupported answers; source/provenance/version integrity survives retries; rights-ineligible tasks never leave the approved boundary; and one compromised, failed, or revoked contributor cannot silently defeat those controls.

## 12. Example end-to-end case

1. Noopedia freezes an approved source passage, task ID `T-042`, and its source/prompt/schema versions.
2. **Run A:** the server uses Contributor 1's authorized provider key to produce candidate assertions.
3. **Run B:** Contributor 2's Python worker independently obtains `T-042` without seeing A and submits a candidate using a locally held key or local model.
4. The coordinator validates both envelopes and compares their normalized meaning, qualifiers, and evidence anchors. If they disagree materially, it holds the task.
5. If they agree, **Run V:** the server requests a separate source-grounded critique, using Contributor 3's authorized API budget or its own key, or performs an approved equivalent independent review.
6. Only a candidate that passes this review proceeds to the existing Noopedia admission machinery. No worker can bypass source support, epistemic limits, review requirements, or publication gates.

This example is an intended control flow, **not a measured reliability claim**. It illustrates how one person contributes API funding, another contributes execution, and a third resource can fund verification.

## 13. Decisions reserved for implementation planning

Before writing a production service, establish the authoritative existing code paths, the exact task/prompt/schema contract, source-rights rules, accepted worker authentication, provider integrations, secure donated-key custody, actual cost ceilings, what qualifies as a separate trust domain, benchmark adjudication ownership, and how review outcomes map to current HOLD/READMITTED/other states. None of these decisions should be hidden inside a “simple” worker script.

A first standalone Python worker plus a small **non-production coordinator adapter** would be a reasonable experiment after repository inspection. Prefer the smallest integration surface and avoid modifying core Pi/workflow or Noopedia components until an independently reviewed need is demonstrated.

## 14. Related documentation

- [Project Description and Philosophy](PROJECT_DESCRIPTION_AND_PHILOSOPHY.md)
- [Semantic and Epistemic Principles](SEMANTIC_AND_EPISTEMIC_PRINCIPLES.md)
- [Knowledge Lifecycle and Architecture](KNOWLEDGE_LIFECYCLE_AND_ARCHITECTURE.md)
- [Documentation Scope](DOCUMENTATION_SCOPE.md)
