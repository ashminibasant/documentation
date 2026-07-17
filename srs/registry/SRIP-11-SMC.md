> **Sigma Runtime Standard - Public Specification Notice**
> This document is part of the **Sigma Runtime Standard (SRS)** public specification layer.
>
> Specification License: CC BY 4.0.
> Implementation Safe Harbor: independent implementation permitted under public SRS/SRIP terms.
> Machine-readable artifacts: Apache License 2.0 where explicitly marked.
> Marks / Certification: governed by Sigma Marks and Certification Policy.
> Proprietary Runtime Assets: not licensed by this SRIP.
>
> Independent implementations of public SRS/SRIP normative requirements are welcome under the public specification terms.
> Product assets, protected Sigma marks, official certification, compatibility badges, CC BY-NC commercial use, and patent commitments use the relevant policy or explicit covenant. Independent implementation, attribution, or citation does not imply certification, endorsement, partnership, official compatibility, or permission to use Sigma marks as product identity.

# SRIP-11: Structural Memory Compression (SMC)

| Field | Value |
| --- | --- |
| SRIP | SRIP-11 |
| Title | Structural Memory Compression (SMC) |
| Version | 1.2 |
| Status | Active |
| Date | 2026-07-17 |
| Authors / Contributors | Sigma Stratum Research Group (SSRG) |
| Owning Layer | Memory / Compression / Topological Recall |
| Parent Specs | SRIP-09, SRIP-10 |
| Related Specs | None declared |
| Specification License | CC BY 4.0 |
| Implementation Safe Harbor | Independent implementation permitted under public SRS/SRIP terms |
| Machine-Readable Artifacts | Apache 2.0 where explicitly marked |
| Marks / Certification | Governed by Sigma Marks and Certification Policy |
| Proprietary Runtime Assets | Not licensed by this SRIP |
| Independent Implementation | Permitted under the public specification terms |
| Commercial Runtime Boundary | Relevant policy or explicit covenant for protected Sigma marks, official certification, managed deployment, white-label, resale, CC BY-NC commercial use, and patent commitments |
| Information Class | Open |
| Change Class | SRS-only |
| Specification Class | Runtime Architecture Specification |
| Legacy Alias | CMT (retired in v1.2 because of prior-art acronym collision) |
| Normative Status | Defines a memory compression and topology contract. It does not mandate a specific vector store, graph store, compression scheduler, or recall product. |
| Conformance Level | Architecture Specification / Profile-Bound Implementation Evidence |
| SRD Synchronization Action | Deferred review |
| Release Alignment Status | aligned with deferred SRD sync |
| Release Alignment Notes | Active specification; public evidence is profile-bound and does not establish full runtime conformance. |

---

## Independent Implementation Safe Harbor

Independent implementations of the public normative requirements in this SRIP are welcome under the applicable public specification terms.

No Sigma commercial runtime license is needed solely because an independent implementation follows those public normative requirements.

Product assets, protected Sigma marks, official certification, compatibility badges, CC BY-NC commercial use, and patent commitments use the relevant policy or explicit covenant. Independent implementation, attribution, or citation does not imply certification, endorsement, partnership, official compatibility, or permission to use Sigma marks as product identity.

## I. Purpose
SRIP-11 defines the architecture of *structural memory compression* and *semantic topology* within Sigma Runtime.
Its goal is to reduce redundancy in long-term storage while preserving continuity of reasoning across extended interaction horizons.
Memory becomes *topological*: a self-organizing lattice of semantic nodes connected by relational weight rather than linear order.

---

## II. Core Concepts

| Term | Description |
|------|--------------|
| **Rib Point** | A profile-bound semantic condensation of a causally bounded source window. |
| **Cluster** | A profile-bound set of Rib Points forming a typed topology region. |
| **Lattice** | Graph of clusters connected by semantic edges (continuity vectors). |
| **Continuity Vector** | A profile-defined representation of direction across causally ordered memory units. |
| **Density Coefficient** | Local measure of information per token (symbolic density). Used for adaptive compression. |
| **Phase Lineage** | Inherited reasoning state (phase → phase) tracked through edges with type `follows` or `transforms`. |
| **Anchor Facts Layer (AFL)** | A priority memory layer for low-similarity but high-importance facts (names, identifiers, constraints). |

---

## II-A. Terminology, Prior Art, And Compatibility

`SMC` is the canonical short name beginning with SRIP-11 v1.2. The earlier
short name `CMT` is retired because it collides with **Compression Memory
Training (CMT)**, a published memory-compression and continual-learning method
for large language models.

The published CMT method trains a compressor and aggregation components to
encode new documents into dense memory representations for later retrieval.
SRIP-11 SMC instead defines a backend-agnostic runtime architecture contract
for structural compression, memory topology, lineage, phase-aware recall, and
anchor facts. SRIP-11 does not claim to define or implement Compression Memory
Training.

The canonical file path is `SRIP-11-SMC.md`. The former `SRIP-11-CMT.md` path
remains as a compatibility redirect so existing public citations do not break.
New prose, metadata, and cross-references must use `SRIP-11 SMC`. Symbol-only
historical `CMT` references should be interpreted as SRIP-11 only when their
SRIP number or document URL establishes that provenance.

The canonical configuration namespace is `smc`. Implementations may continue
to accept the former `cmt` namespace as a deprecated compatibility input, but
must normalize it to `smc` and must not emit both namespaces for one effective
configuration.

Prior-art reference:

- Dongfang Li, Zetian Sun, Xinshuo Hu, Baotian Hu, and Min Zhang (2025),
  "CMT: A Memory Compression Method for Continual Knowledge Learning of Large
  Language Models," *Proceedings of the AAAI Conference on Artificial
  Intelligence*, 39(23), 24413-24421.
  [DOI 10.1609/aaai.v39i23.34619](https://doi.org/10.1609/aaai.v39i23.34619);
  [arXiv:2412.07393](https://arxiv.org/abs/2412.07393).

---

## Implementation Profile Boundary

SRIP-11 is backend-agnostic. Embedding model, vector dimensionality, graph
library, vector store, cycle schedules, and numeric thresholds are not normative
unless a separate implementation profile explicitly binds them.

Historical library, storage, embedding, schedule, and threshold choices have
been moved to the non-normative
[SRIP-11 SMC Reference Implementation Profile](../implementation-profiles/SRIP-11-SMC-reference-profile.md).

## III. System Functions

### 1. Dynamic Compression Loop

At a profile-declared boundary, an implementation:

1. selects a causally bounded source window;
2. derives a compressed representation under a versioned compression profile;
3. records source, profile, validity, and lineage references;
4. stores the result as a Rib Point or an equivalent structural memory unit;
5. connects that unit to its declared predecessors without rewriting source
   history.

```
Source window -> profile-bound compression -> Rib Point -> Cluster
```

The schedule, representation algorithm, embedding model, dimensionality, and
storage products are implementation-profile choices.

### 2. Adaptive Retention

Compression is not uniform:
records with high density and low redundancy are retained longer;
ephemeral ones are merged or pruned.

Any retention score must declare its formula, units, window, missing-value
semantics, calibration profile, and evidence authority. SRIP-11 does not define
a universal retention formula or threshold.

### 3. Topological Retrieval

Recall operates through graph propagation rather than flat similarity:
- Input query → encode vector
- Find nearest rib points → expand through connected edges weighted by phase lineage
- Return contextual subgraph as memory summary.

Equivalent non-vector retrieval is permitted when it preserves typed topology,
source lineage, validity, and bounded recall authority.

### 4. Phase-Aware Recall

Memory is filtered by phase compatibility (`forming`, `stable`, `reflection`, `fragmenting`).
This prevents semantic cross-contamination between developmental stages of reasoning.

The following matrix is a foundational compatibility profile. Implementations
using another phase model must publish that profile rather than silently reuse
these labels.

| Current Phase | Compatible Recall Phases |
|---------------|--------------------------|
| `forming` | forming, stable |
| `stable` | stable, reflection |
| `reflection` | reflection, stable, fragmenting |
| `fragmenting` | fragmenting, reflection |

### 5. Anchor Facts Layer (AFL)
Semantic similarity fails on certain anchor facts (e.g., names, identifiers, fixed constraints).
SRIP-11 defines a priority retrieval path that is domain-agnostic and available
to governed recall independently of ordinary semantic similarity.

**AFL Responsibilities:**
- Preserve low-similarity, high-importance facts (names, IDs, numbers, commitments).
- Make declared anchor facts eligible for governed recall without requiring
  them to appear in every model-visible prompt.
- Operate independently of semantic similarity thresholds.
- Preserve source, scope, validity, and update authority.

**AFL Retrieval Order:**
1. Declared bounded anchor context
2. Known Facts (model-extracted structured facts)
3. Topological recall (Rib Points / Clusters)
4. Semantic similarity fallback

#### 5a. Anchor Buffer Contract

An implementation may preserve a bounded early source window as anchor
authority. The profile must declare the window, retention policy, access scope,
privacy boundary, and whether material is model-visible or metadata-only.
Verbatim retention does not imply unconditional prompt injection.

#### 5b. Model-Driven Fact Extraction (AFL v2)

An implementation may extract structured facts at profile-declared causal
boundaries. Scheduling must be language-independent unless the implementation
explicitly declares a language-specific profile.

The model-driven AFL path uses no lexical extraction patterns; the model decides
what to extract. This claim is scoped to AFL scheduling and extraction. It does
not assert that every legacy compression or topic-extraction implementation is
language-agnostic; language support is implementation-profile-defined.

**Safety:** Candidate facts must originate from governed source material. An
assistant statement must not become a user fact merely because the assistant
generated it. Implementations must preserve source role and confidence and must
not silently promote inferred facts to anchor authority.

#### 5c. Domain Adapter (Optional, Pluggable)

Domain adapters may define additional fact categories, validation rules, or
retention constraints. They must not weaken core provenance, user-source,
validity, privacy, or deletion requirements. Concrete adapter names and
configuration fields belong to implementation profiles.

### 6. Compression Feedback

The **AEP (Adaptive Entropy Protocol)** or an equivalent governing layer may
consume compression ratio, semantic loss, and validity evidence. Corrective
action requires a separately authorized control contract. SRIP-11 does not
define a universal trigger threshold, controller method, or regeneration action.

---

## IV. Structural Contracts

### Rib Point

A Rib Point or equivalent structural memory unit records:

- stable unit ID and schema version;
- causally bounded source-window ref;
- compressed representation ref and profile ref;
- parent lineage;
- phase or state-model ref when phase-aware recall is claimed;
- validity and creation authority;
- content visibility and retention disposition.

### Cluster

A Cluster or equivalent topology unit records:

- stable cluster ID and schema version;
- member unit refs;
- topology or aggregation profile ref;
- lineage and validity;
- optional theme, phase-distribution, or cohesion evidence when supplied by a
  declared profile.

**Storage contract:**
- **Topology Store:** implementation-selected directed topology with typed edges
  (`follows`, `transforms`, `belongs_to`, `continuity`).
- **Retrieval Index:** optional implementation-selected index for compatible
  Rib Point and Cluster representations.

Storage products and identifier encodings are implementation-profile choices,
not public conformance requirements.

---

## V. Compression Policies

| Policy | Description |
|---------|--------------|
| **per_section** | Compress each declared logical or semantic section. |
| **per_cycle** | Compress after a profile-declared interaction window. |
| **hybrid** | Combine profile-declared micro and macro windows. |
| **structural** | Trigger from valid profile-bound density or drift evidence. |

---

## VI. Metrics and Monitoring

| Metric ID | Symbol | Purpose |
|-----------|--------|---------|
| `srip11.compression_ratio.v1` | `CR` | Efficiency under a declared token-count profile |
| `srip11.semantic_loss.v1` | `SL` | Fidelity under a compatible representation profile |
| `srip11.topology_cohesion.v1` | `TC` | Structural stability of a declared cluster |
| `srip11.phase_continuity.v1` | `PC` | Continuity under a declared phase model |
| `srip11.anchor_recall_integrity.v1` | `ARI` | Reliability of declared anchor recall |
| `srip11.fact_extraction_rate.v1` | `FER` | Profile-bound extraction yield |
| `srip11.fact_coverage.v1` | `FC` | Coverage of declared evaluated categories |

Formulas, missing-value semantics, units, windows, and calibration authority are
defined by the [SRS Metric Registry](../metric-registry.md) and compatible
implementation profiles. Missing or incompatible authority is `unverified`, not
zero.

---

## VII. Expected Outcomes

- Reduced token footprint for long sessions, with any quantitative reduction
  claim bound to a separately published benchmark and baseline.
- Improved semantic continuity without context overflow
- Dynamic memory lattice capable of bounded reasoning summaries
- Reliable recall of anchor facts without domain-specific hardcoding

---

## VIII. Conformance Requirements

A conforming SRIP-11 implementation must:

1. preserve immutable source and compression lineage;
2. bind schedules, representations, stores, thresholds, and metrics to a
   versioned implementation profile;
3. distinguish model-visible memory from metadata-only material;
4. preserve fact-source roles and prevent assistant output from silently
   becoming user fact authority;
5. expose validity and explicit missing-value semantics;
6. support deletion and retention governance without rewriting historical
   provenance;
7. avoid claiming universal performance from profile-specific evidence.

Concrete products, dimensions, class names, YAML fields, controller methods,
and numeric defaults are non-normative and belong to implementation profiles.

---

**End of SRIP-11 SMC v1.2**
*Sigma Stratum Research Group – 2026*
