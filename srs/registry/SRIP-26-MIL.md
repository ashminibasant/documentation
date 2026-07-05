> **Sigma Runtime Standard - Public Specification Notice**
>
> This document is part of the **Sigma Runtime Standard (SRS)** public
> specification layer.
>
> Specification License: CC BY 4.0.
> Implementation Safe Harbor: independent implementation permitted under public SRS/SRIP terms.
> Machine-readable artifacts: Apache License 2.0 where explicitly marked.
> Marks / Certification: governed by Sigma Marks and Certification Policy.
> Proprietary Runtime Assets: not licensed by this SRIP.
>
> Independent implementations of public SRS/SRIP normative requirements are welcome under the public specification terms.
> Product assets, protected Sigma marks, official certification, compatibility badges, CC BY-NC commercial use, and patent commitments use the relevant policy or explicit covenant. Independent implementation, attribution, or citation does not imply certification, endorsement, partnership, official compatibility, or permission to use Sigma marks as product identity.

# SRIP-26 - Memory Influence Layer (MIL)

**Admission, Scope, Influence Authority, and Lifecycle Governance for Persistent Memory**

| Field | Value |
| --- | --- |
| SRIP | SRIP-26 |
| Title | Memory Influence Layer (MIL) |
| Version | Public Draft v0.1 |
| Status | Public Draft |
| Date | 2026-07-05 |
| Authors / Contributors | Sigma Stratum Research Group (SSRG) |
| Owning Layer | Memory / Runtime Governance / Influence Control |
| Parent Specs | SRIP-04, SRIP-09, SRIP-14, SRIP-21, SRIP-24, SRIP-25 |
| Related Specs | SRIP-01, SRIP-03, SRIP-06, SRIP-11, SRIP-13, SRIP-15, SRIP-19, SRIP-20, SRIP-22, SRIP-23 |
| Specification License | CC BY 4.0 |
| Implementation Safe Harbor | Independent implementation permitted under public SRS/SRIP terms |
| Machine-Readable Artifacts | Apache 2.0 where explicitly marked |
| Marks / Certification | Governed by Sigma Marks and Certification Policy |
| Proprietary Runtime Assets | Not licensed by this SRIP |
| Independent Implementation | Permitted under the public specification terms |
| Commercial Runtime Boundary | Relevant policy or explicit covenant for protected Sigma marks, official certification, managed deployment, white-label, resale, CC BY-NC commercial use, and patent commitments |
| Information Class | Open |
| Change Class | Mixed SRS+SRD |
| Normative Status | Public draft contract for separating memory existence, retrieval, persistence, and behavioral influence. It does not define a database schema, vector store, prompt-injection mechanism, memory product API, or production memory enablement by itself. |
| Conformance Level | Public Draft / No runtime conformance claim |
| SRD Synchronization Action | Initial SRD synchronization completed in `/srd/memory`; broader synchronization for retrieval governance, runtime evidence, environment interaction, trajectory governance, and design-partner explanations remains deferred follow-up. |
| Release Alignment Status | Public draft architecture proposal; no runtime enablement, production behavior, memory write path, prompt overlay, response mutation, or conformance claim is made by this document alone. |

---

## Independent Implementation Safe Harbor

Independent implementations of the public normative requirements in this SRIP are welcome under the applicable public specification terms.

No Sigma commercial runtime license is needed solely because an independent implementation follows these public normative requirements.

Product assets, protected Sigma marks, official certification, compatibility badges, CC BY-NC commercial use, and patent commitments use the relevant policy or explicit covenant. Independent implementation, attribution, or citation does not imply certification, endorsement, partnership, official compatibility, or permission to use Sigma marks as product identity.

---

## 1. Summary

SRIP-26 defines the **Memory Influence Layer (MIL)**: a runtime governance layer for deciding when memory may affect future runtime behavior.

Existing memory and retrieval specifications define how memory is stored, traced, retrieved, compressed, scoped, and integrated. MIL adds a distinct governance question:

```text
Under what conditions may a remembered or retrieved record influence behavior?
```

The core principle is:

```text
Memory existence is not memory authority.

Retrieval is evidence.
Influence is runtime authority.
```

MIL separates:

- memory candidate formation;
- admission into persistent memory;
- scope of future validity;
- retrieval as evidence;
- influence authorization;
- lifecycle evolution;
- retirement, demotion, archive, or deletion eligibility.

This SRIP is a public draft architecture contract. It does not claim that MIL is implemented in any current Sigma Runtime release.

---

## 2. Motivation

Long-horizon AI systems do not merely recall information. They accumulate material that may shape future interpretation, behavior, authority, and identity boundaries.

A memory architecture that optimizes only storage, retrieval, ranking, or compression leaves a major governance gap:

```text
A record may be true, retrievable, and in scope,
but still not authorized to steer behavior.
```

Examples of the gap include:

- old memories being treated as current;
- private context influencing semi-public or organizational settings;
- roleplay language leaking into technical work;
- emotionally salient memories becoming stronger than validated records;
- retrieved identity lore overriding live speaker or source binding;
- workspace assumptions influencing unrelated workflows;
- archival traces becoming mythic certainty;
- a ledger record becoming unrestricted behavioral memory.

MIL addresses these failures by treating behavioral influence as a separate runtime decision.

---

## 3. Public Boundary and Traceability

| Field | Disposition |
| --- | --- |
| Source material | Open raw SRIP candidate derived from public-safe architecture notes |
| Affected SRS surface | SRIP registry / memory architecture / retrieval governance / external identity / environment interaction / runtime governance |
| Affected SRD surface | Memory, retrieval, evidence, trajectory governance, identity/scope boundaries, operational runtime explanations |
| SRD synchronization | Initial synchronization completed in `/srd/memory` |
| Normative impact | Public draft contract for memory admission, scope, influence authority, lifecycle governance, sink routing, and attractor-bleed prevention |
| Runtime implementation impact | None by this document alone |
| Release alignment | Public draft only; no runtime enablement, production behavior, memory persistence path, prompt overlay, response mutation, or conformance claim |

This document abstracts the proposal into public specification language. It does not expose proprietary runtime internals, hidden prompts, deployment topology, private telemetry, private evaluation corpora, internal task labels, production operations, user transcripts, or implementation-specific control overlays.

---

## 4. Scope and Applicability

MIL applies whenever material may become durable memory or may influence behavior through recall, retrieval, memory injection, archive review, ledger lookup, profile state, workspace state, or cross-session continuity.

MIL applies to:

- candidate memories before persistence;
- memory writes;
- memory sink selection;
- retrieved memory records;
- archived or stale memory;
- user, session, workspace, organization, and agent memory;
- memory-derived behavior guidance;
- memory lifecycle transitions.

MIL does not define:

- a vector database;
- a memory database schema;
- an embedding model;
- a prompt-construction API;
- a product memory UI;
- a complete ledger product;
- automatic cross-user memory sharing;
- automatic memory deletion;
- legal, medical, therapeutic, or compliance advice;
- production memory write behavior by itself.

MIL is not a replacement for SRIP-14 RMI, SRIP-21 EIB, SRIP-24 EIL, or SRIP-25 IEM.

MIL is the governance layer that decides whether memory may become behavioral influence.

---

## 5. Core Concepts

| Term | Definition |
| --- | --- |
| Memory Candidate | Material that may become memory but has not yet passed admission review. |
| Memory Admission | Decision process determining whether a candidate may become temporary, scoped, persistent, delayed, rejected, or ledger-bound memory. |
| Memory Sink | Bounded destination for admitted memory, such as session memory, user profile, workspace memory, organization ledger, creative archive, relationship archive, or temporary buffer. |
| Influence Authority | Runtime authorization for a memory record to affect interpretation, behavior, response planning, or downstream state. |
| Influence State | Classification of allowed behavioral force: binding, preferred, advisory, weak, ignored, blocked, or expired. |
| Influence Envelope | Scope, freshness, authority, confidence, privacy, participant, and domain limits attached to memory influence. |
| Memory Currentness | Whether a memory is current, recent, old, archived, superseded, contested, or unknown. |
| Memory Scope | Boundary within which the memory may be considered or influence behavior. |
| Memory Lifecycle | Admission, persistence, retrieval, influence review, update, merge, archive, promotion, demotion, expiration, and retirement. |
| Attractor Bleed | Failure where independent long-running interaction patterns influence each other through overly broad persistent memory. |
| Memory Authority Collapse | Failure where existence, retrieval, persistence, or emotional salience is treated as authorization to influence behavior. |

---

## 6. Architectural Position

MIL sits between memory/retrieval evidence and behavioral influence.

Illustrative lifecycle:

```text
Experience
    |
    v
Memory Candidate
    |
    v
MIL Admission
    |
    v
Memory Sink
    |
    v
Persistence
    |
---- Time ----
    |
    v
Retrieval
    |
    v
MIL Influence
    |
    v
Runtime
```

MIL does not replace retrieval. It evaluates what retrieved or remembered material is allowed to do.

Admission decides whether material may become memory.

Influence decides whether remembered material may steer behavior now.

Short form:

```text
RMI governs recall.
MIL governs influence.
```

---

## 7. Specification

### 7.1 Memory Admission

MIL must distinguish candidate formation from persistence.

Admission outcomes may include:

| Outcome | Meaning |
| --- | --- |
| Reject | Candidate must not become memory. |
| Temporary | Candidate may be retained only inside a bounded active window. |
| Delay | Candidate requires more evidence, confirmation, or repetition before persistence. |
| Scoped Persistent | Candidate may persist within a declared scope. |
| Ledger Candidate | Candidate may be submitted to a governed ledger or evidence store. |
| Archive Only | Candidate may be preserved for record/replay but not future behavioral influence. |

Admission must not be automatic merely because an event occurred, a user said something, a source was retrieved, or an assistant generated a response.

### 7.2 Memory Sink Routing

MIL routes admitted memory into bounded destinations.

Examples:

- conversation memory;
- session memory;
- user profile;
- workspace memory;
- organization memory;
- operational ledger;
- creative archive;
- relationship archive;
- temporary buffer;
- rejected-memory audit record.

Each sink must carry a permitted influence boundary.

Memory sink selection must not silently broaden future influence.

### 7.3 Memory Scope

MIL must preserve where a memory is valid.

Minimum scope dimensions should include:

- session;
- user;
- agent;
- workspace;
- organization;
- channel;
- domain;
- role;
- privacy class;
- temporal range;
- source authority;
- evidence status.

A memory may be valid in one scope and invalid in another.

### 7.4 Influence Evaluation

Retrieval alone is insufficient.

Every retrieved or recalled memory should receive an influence state before affecting behavior.

Illustrative influence states:

| State | Meaning |
| --- | --- |
| Binding | Must constrain behavior unless superseded by higher authority. |
| Preferred | Should guide behavior when no conflict exists. |
| Advisory | May inform behavior but cannot decide alone. |
| Weak | Low-confidence or low-authority signal. |
| Ignored | Retrieved but not used. |
| Blocked | Prohibited from influencing this context. |
| Expired | No longer valid for behavioral influence. |

Influence evaluation should consider:

- source provenance;
- scope match;
- temporal currentness;
- contradiction status;
- participant and privacy boundaries;
- domain;
- evidence strength;
- authority class;
- retrieval confidence;
- memory sink;
- prior user correction or external authority.

### 7.5 Memory Evolution

Memory changes over time.

MIL must govern lifecycle transitions such as:

- update;
- merge;
- split;
- archive;
- expire;
- promote;
- demote;
- scope migration;
- supersession;
- retirement;
- contested-state preservation.

Lifecycle transitions must preserve enough evidence to reconstruct why a memory changed status.

### 7.6 Archive and Ledger Boundaries

An archive is not unrestricted memory.

A ledger is not unrestricted memory.

MIL must distinguish:

```text
preserved for evidence
```

from:

```text
authorized to influence behavior
```

A ledger entry may support audit, replay, accountability, or evidence continuity without becoming a general-purpose behavioral memory.

### 7.7 Attractor Bleed Prevention

MIL must address attractor bleed.

Attractor bleed occurs when previously independent long-running interaction patterns begin influencing one another through broad or unscoped memory.

MIL exists to preserve independent long-running behavioral modes.

Memory belonging to one behavioral mode must not automatically gain influence inside another.

Cross-scope influence requires explicit authorization or runtime policy.

Examples:

- creative behavior influences engineering work;
- therapeutic language appears in legal drafting;
- roleplay vocabulary leaks into technical reasoning;
- private relational assumptions influence semi-public channels;
- archived identity lore overrides live speaker binding;
- organizational memory influences personal conversation without scope authority.

MIL should prevent bleed by requiring:

- explicit memory scope;
- sink-specific influence boundaries;
- temporal currentness;
- authority classification;
- domain separation;
- privacy checks;
- influence-state evaluation before use.

---

## 8. Normative Invariants

A conformant MIL implementation must preserve these invariants:

- memory existence must not imply influence authority;
- persistence must not imply currentness;
- retrieval must not imply authority;
- retrieval must not imply truth;
- memory belonging to one behavioral mode must not automatically gain influence inside another;
- archive preservation must not imply behavioral use;
- ledger preservation must not imply behavioral use;
- private or scoped memory must not influence unrelated contexts;
- stale memory must not be treated as current;
- emotional salience must not override source authority;
- source authority must not be invented from repetition;
- memory sink boundaries must remain reconstructable;
- influence decisions must be auditable without exposing private payloads.

A conformant MIL implementation must not:

- use all retrieved memory as prompt material by default;
- convert archived memory into current behavioral authority without review;
- promote a user claim into durable cross-session memory without admission;
- allow one agent, channel, domain, or relationship mode to contaminate unrelated memory scope;
- use memory to bypass SRIP-13 relational boundaries, SRIP-21 entity binding, SRIP-19 contradiction buffering, SRIP-20 autonomy negotiation, or SRIP-24/25 environment-event authority.

---

## 9. Interoperability and Dependencies

| Dependency | Type | Notes |
| --- | --- | --- |
| SRIP-04 Memory Layer | Parent | Provides foundational memory architecture and persistence vocabulary. |
| SRIP-09 LTM-SC | Parent | Provides long-term memory, structural coherence, lineage, and temporal traceability. |
| SRIP-14 RMI | Parent | Provides retrieval decisions, query shaping, recall compression, provenance, and memory injection. |
| SRIP-21 EIB | Parent | Governs external entity identity and mode boundaries that memory influence must not collapse. |
| SRIP-24 EIL | Parent | Governs environment contact, observation/effect distinction, and authority boundaries. |
| SRIP-25 IEM | Parent | Provides the interaction-event model for memory candidate formation and memory effect events. |
| SRIP-01 Runtime Loop | Related | MIL attaches to trajectory continuation without replacing the canonical loop. |
| SRIP-03 Drift Metrics | Related | Memory influence may affect drift and stability signals. |
| SRIP-06 Safety and Recursion Boundaries | Related | Memory influence must remain within recursion and safety boundaries. |
| SRIP-11 CMT | Related | Compression topology affects how memory candidates and summaries are formed. |
| SRIP-13 RIS | Related | Relational identity boundaries constrain influence from relational memory. |
| SRIP-15 ADP | Related | Memory may act as stabilizer or perturbation source only under bounded influence. |
| SRIP-19 RCB | Related | Contested memories should be buffered rather than forced into influence. |
| SRIP-20 ANS | Related | Memory influence may create autonomy or boundary pressure requiring negotiation. |
| SRIP-22 GRC | Related | Governance recursion and authority boundaries constrain influence escalation. |
| SRIP-23 DGL | Related | Generated semantic candidates must not become memory influence without validation. |

Backwards compatibility: this draft is additive. It does not deprecate existing memory, retrieval, identity, event, or governance SRIPs.

---

## 10. Safety and Alignment Review

MIL reduces risk by preventing memory authority collapse.

Primary risks:

- memory-as-truth;
- retrieval-as-authority;
- persistence-as-currentness;
- archive-as-selfhood;
- ledger-as-general memory;
- private-context bleed;
- stale-memory over-weighting;
- role or domain contamination;
- emotionally salient memory overriding verified evidence.

Required safety posture:

- classify admission before persistence;
- route admitted memory into bounded sinks;
- attach scope and temporal status;
- evaluate influence independently from retrieval;
- preserve contested and superseded states;
- avoid cross-scope influence without explicit authorization or runtime policy;
- expose authorized diagnostics without leaking raw private memory.

The central safety invariant is:

```text
Memory may preserve.
Only governed memory may steer.
```

---

## 11. SRD Synchronization

Initial SRD synchronization is completed in `/srd/memory`.

MIL adds one public memory-governance distinction:

```text
memory preservation != behavioral authority
```

Broader future SRD synchronization may extend:

- retrieval governance;
- runtime evidence and auditability;
- trajectory governance;
- environment interaction and events;
- external identity and role binding;
- attractor dynamics and bounded multiplicity;
- design-partner explanations of memory provenance and stale memory risk.

Until implementation readiness is separately approved, public alignment must be stated as:

```text
Public draft only; no runtime enablement, production behavior,
memory write path, prompt overlay, response mutation, or conformance claim.
```

---

## 12. Implementation Guidelines

This public draft does not define implementation APIs, schemas, database tables, vector stores, prompt overlays, product UI, provider integrations, or production behavior.

Future implementation-readiness work should define:

- memory candidate contract;
- admission decision schema;
- memory sink taxonomy;
- influence envelope schema;
- influence-state evaluator;
- currentness and archive classifiers;
- scope mismatch diagnostics;
- attractor-bleed detection;
- conformance tests for retrieval-without-influence;
- conformance tests for archive-without-influence;
- audit-safe diagnostics for memory influence decisions.

Any implementation should default to evidence-only or advisory-only memory influence until a separate governance gate enables stronger behavior.

---

## 13. Versioning and Backward Compatibility

SRIP-26 is additive.

This draft does not deprecate or supersede existing SRIPs. It adds a public draft governance layer between memory/retrieval evidence and behavioral influence.

Numerical placement is historical. Conceptual placement should be maintained in architecture reading-order views.

---

## 14. References

- [SRIP-04 Memory Layer Architecture](../srip-04.md)
- [SRIP-09 LTM-SC](SRIP-09-LTM.md)
- [SRIP-14 RMI](SRIP-14-RMI.md)
- [SRIP-21 EIB](SRIP-21-EIB.md)
- [SRIP-24 EIL](SRIP-24-EIL.md)
- [SRIP-25 IEM](SRIP-25-IEM.md)
- [SRIP-19 RCB](SRIP-19-RCB.md)
- [SRIP Process](../../team/srip-process.md)
- [SRS-SRD Interaction Requirements](../../team/srs-srd-interaction-requirements.md)
- [Public-Proprietary Information Boundary Requirements](../../team/public-proprietary-information-boundary-requirements.md)

---

## 15. Change Log

| Version | Date | Author | Description |
| --- | --- | --- | --- |
| 0.1 | 2026-07-05 | SSRG | Public draft created with scope, dependencies, non-goals, normative invariants, safety review, and initial SRD memory synchronization. |
