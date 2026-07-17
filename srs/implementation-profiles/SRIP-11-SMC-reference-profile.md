---
title: SRIP-11 SMC Reference Implementation Profile
description: Non-normative historical implementation choices for Structural Memory Compression.
published: true
date: 2026-07-17T00:00:00.000Z
tags:
editor: markdown
dateCreated: 2026-07-17T00:00:00.000Z
---

> **Sigma Runtime Standard - Public Specification Notice**
>
> Specification License: CC BY 4.0.
> Independent implementation is permitted under the public SRS/SRIP terms.
> Machine-readable artifacts: Apache License 2.0 where explicitly marked.
> Proprietary Sigma Runtime assets and Sigma marks are not licensed by this document.

# SRIP-11 SMC Reference Implementation Profile

| Field | Value |
| --- | --- |
| Information Class | `Derived-Public` |
| Source Context | Historical and current proprietary runtime implementation context |
| Sanitization | Historical public configuration and method identifiers only; no prompts, private data, deployment, or operational paths |

This document is non-normative. It preserves one historical implementation
shape for SRIP-11 without making its libraries, embedding dimensions, thresholds,
or storage layout requirements of the backend-agnostic public standard.

The retired `CMT` architecture alias is retained in historical SRIP-11 lineage.
New references use the canonical `SMC` name. A bounded implementation may keep
legacy wire fields while it migrates, but those fields must not define a second
architecture namespace.

## Configuration Compatibility

| Surface | Canonical Behavior | Compatibility Behavior |
| --- | --- | --- |
| Configuration input | `smc` | A lone `cmt` block may be accepted and normalized before inheritance or runtime use. |
| Effective configuration | Emit one `smc` block | A document containing both `smc` and `cmt` is invalid. |
| Persistence and API | Versioned implementation fields | Existing names such as `cmt_enabled` may remain legacy wire aliases until a separately versioned schema migration. |
| Diagnostic payloads | SMC terminology | Existing `cmt` payload keys may remain compatibility fields when explicitly documented. |

Accepting a legacy field does not make `CMT` a second public SRIP name.

## Historical Profile

| Surface | Reference Choice | Normative Status |
| --- | --- | --- |
| Embedding | MiniLM-compatible 384-dimensional vector | Example only |
| Graph store | NetworkX directed graph | Example only |
| Vector store | FAISS index | Example only |
| Rib Point interval | 10-50 cycles | Calibration example |
| Cluster size | 5-10 Rib Points | Calibration example |
| Anchor buffer | First 8 cycles | Calibration example |
| Fact extraction | First 3 cycles, then every 10 cycles | Calibration example |
| Semantic-loss trigger | `0.25` | Historical threshold; not universal |

## Historical Configuration Examples

The following examples preserve the concrete defaults formerly embedded in the
canonical SRIP. They describe one historical profile and are not conformance
requirements.

```yaml
smc:
  anchor_buffer:
    enabled: true
    cycles: 8
  fact_extraction:
    enabled: true
    interval: 10
    early_cycles: 3
    min_confidence: 0.7
    max_facts: 30
  domain_adapter: null
```

Historical adapters included conversational, healthcare, defense, business,
education, legal, and technical extraction profiles. Those names do not create
normative SMC domains.

One identity-specific runtime example used a non-prompt `behavior` block:

```yaml
behavior:
  compression:
    list_tolerance: 0.6
  token_policy:
    base_limit: 900
    min_limit: 400
    max_limit: 1200
```

The historical behavior interpreted `list_tolerance >= 0.8` as no list penalty,
scaled lower values by `1 - list_tolerance`, and allowed `base_limit` to override
the default completion limit. These choices are not part of the SMC contract.

## Historical Runtime Coupling

One implementation exposed compression feedback through methods named
`AEPController.monitor_compression()` and
`AEPController.trigger_phase_regeneration()`. Semantic loss above `0.25` could
queue temporary expansion under that profile. These identifiers and the trigger
are historical implementation evidence, not required interfaces or universal
control semantics.

The same profile used the illustrative retention formula:

```text
retention_weight = (density * coherence) / max(0.01, entropy)
```

Implementations must not reuse this formula without declaring compatible units,
windows, normalization, and calibration evidence.

Illustrative structures:

```python
@dataclass
class RibPoint:
    id: str
    cycle_range: tuple[int, int]
    vector: list[float]  # 384 dimensions in this profile only
    summary: str
    phase: str
    density: float
    entropy: float
    lineage: list[str]

    # Historical profile only:
    # retention_weight = (density * (1 - entropy)) / max(0.01, entropy)

@dataclass
class Cluster:
    id: str
    rib_points: list[str]
    centroid: list[float]
    theme: str
    phase_distribution: dict[str, int]
    cohesion: float
```

Equivalent implementations may use different embedding models, dimensions,
graph stores, vector stores, schedules, and retrieval engines if they preserve
the normative SRIP-11 boundaries, lineage, validity, and observability.

Historical fact-category examples included identity, context, constraints,
relationships, history, commitments, and preferences. Historical rendering
grouped known facts by category before model-visible recall. Both the category
set and rendering format are implementation-profile choices.

## Evidence Boundary

The statement `10x reduction in token footprint for sessions above 500 cycles`
is a historical target, not a public conformance result. It must not be presented
as a benchmarked outcome without a dataset, baseline, estimator, run manifest,
and evidence reference.
