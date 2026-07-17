---
title: SRS Metric Registry
description: Canonical symbols, semantics, validity rules, calibration authority, and migration requirements for public Sigma Runtime metrics.
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

# SRS Metric Registry

| Field | Value |
| --- | --- |
| Information Class | `Open` |
| Change Class | `SRS-only` |

This registry is the canonical public authority for metric identifiers and
symbols used across SRS and SRIP documents. It prevents one symbol from carrying
multiple meanings and prevents an implementation-specific calibration from
silently becoming a universal conformance constant.

## 1. Registry Requirements

Every metric used by a normative requirement must declare:

- a stable metric identifier and unique public symbol;
- semantic meaning and measurement domain;
- value type, range, units, and direction;
- formula or an explicit `profile_defined` disposition;
- sampling window and aggregation authority;
- missing, invalid, and out-of-domain behavior;
- calibration profile and evidence reference;
- schema version and migration behavior.

If any required field is unavailable, the metric is `unverified`. A conforming
implementation must not substitute a numeric default or infer metric meaning
from the observed value.

## 2. Canonical Core Metrics

| Metric ID | Symbol | Meaning | Domain / Units | Formula Authority | Missing Semantics | Calibration / Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| `srs.semantic_drift_index.v1` | `SDI` | Conceptual or embedding displacement across causally ordered observations. | `[0,1]`, dimensionless after profile normalization | `profile_defined`; SRIP-03 contains a foundational reference profile | `unverified`; never zero-fill | SRIP-03 profile; cross-provider calibration required for conformance claims |
| `srs.symbolic_density.v1` | `SD` | Symbolic information density over a declared token, motif, or structure window. | `[0,1]`, dimensionless after profile normalization | `profile_defined` by SRIP-07-compatible implementation profile | `unverified`; never alias to `SDI` | SRIP-07 profile and evidence reference required |
| `srs.symbolic_drift.v1` | `SV` | Change or distortion in symbolic density or motif structure across a declared window. | `[0,1]`, dimensionless after profile normalization | `profile_defined` | `unverified` | SRIP-03 profile required |
| `srs.control_posture_drift.v1` | `PD` | Difference between observed and expected runtime control posture. | `[0,1]`, dimensionless after profile normalization | `profile_defined` | `unverified` | SRIP-03 profile required |
| `srs.semantic_compression_ratio.v1` | `SCR` | Declared ratio between retained and source semantic material. | `(0,1]`, dimensionless | `profile_defined`; numerator and denominator must be declared | `unverified`; zero is invalid | SRIP-03/SRIP-11 profile required |
| `srs.composite_drift_index.v1` | `DI` | Composite drift evidence derived from registered component metrics. | Non-negative, profile-normalized | Foundational SRIP-03 reference formula; production conformance requires a versioned calibration profile | `unverified` if any required component, denominator, or profile is invalid | SRIP-03 reference profile; implementation evidence required |
| `srs.phase_stability_index.v1` | `PSI` | Stability of the active phase relative to a declared phase model. | `[0,1]`, dimensionless | `profile_defined` | `unverified` | SRIP-02/SRIP-08 profile required |
| `srs.phase_stability_delta.v1` | `PSD` | Absolute difference between observed and expected phase stability. | `[0,1]`, dimensionless | `abs(PSI_observed - PSI_expected)` | `unverified` if either input is unavailable | SRIP-02 |
| `srs.phase_shift_delta.v1` | `PSDelta` (`PSΔ` display) | Temporal change in phase alignment. | Profile-defined normalized delta | `profile_defined` | `unverified` | SRIP-02/SRIP-08 profile required |
| `srs.phase_coherence_index.v1` | `PCI` | Coherence of phase alignment under a declared phase-vector model. | `[0,1]`, dimensionless | SRIP-08 profile | `unverified` | SRIP-08 |
| `srs.continuity_index.v1` | `CI` | Continuity across a declared memory or trajectory window. | `[0,1]`, dimensionless | `profile_defined` | `unverified` | SRIP-04 profile required |
| `srs.retention_index.v1` | `RI` | Retention of declared core motifs or records. | `[0,1]`, dimensionless | `profile_defined` | `unverified` | SRIP-04 profile required |
| `srs.entropy_ratio.v1` | `ER` | Signal-to-noise or entropy relation under a declared estimator. | `[0,1]`, dimensionless | `profile_defined` | `unverified` | SRIP-04 profile required |
| `srs.control_carryover.v1` | `CC` | Coherence of control state across declared windows. | `[0,1]`, dimensionless | `profile_defined` | `unverified` | SRIP-04 profile required |

`profile_defined` is not permission to choose an undocumented formula. It means
the producing implementation must bind the observation to a versioned profile
that supplies the omitted formula, window, normalization, and calibration
evidence.

### 2.1 Registered Extension Metrics

| Metric ID | Symbol | Meaning | Domain / Units | Formula Authority | Missing Semantics | Calibration / Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| `srip10.terminological_isometry.v1` | `TI` | Proportional stability of declared terminology over a window. | `[0,1]`, profile-normalized | `profile_defined` | `unverified` | SRIP-10 profile |
| `srip10.semantic_drift_coefficient.v1` | `SDC` | AEP profile estimate of mean inter-cycle semantic displacement. | `[0,1]`, profile-normalized | SRIP-10 profile | `unverified` | SRIP-10 calibration evidence |
| `srip10.logic_noise_ratio.v1` | `L/N` | Profile-defined relation between logical signal and noise. | Non-negative ratio | `profile_defined`; numerator and denominator required | `unverified` if denominator or profile is invalid | SRIP-10 profile |
| `srip11.compression_ratio.v1` | `CR` | Tokens retained divided by tokens input. | `[0,1]` | `tokens_retained / tokens_input` | `unverified` when input count is zero | SRIP-11 profile |
| `srip11.semantic_loss.v1` | `SL` | Distance between source and compressed representations. | `[0,1]`, profile-normalized | SRIP-11 reference uses `1 - cosine_similarity` | `unverified` for missing/incompatible embeddings | SRIP-11 profile |
| `srip11.topology_cohesion.v1` | `TC` | Mean declared edge weight within a cluster. | Profile-defined normalized value | `profile_defined` | `unverified` for empty/invalid cluster | SRIP-11 profile |
| `srip11.phase_continuity.v1` | `PC` | Correlation or alignment of reasoning vectors across phases. | Profile-defined correlation | `profile_defined` | `unverified` | SRIP-11/SRIP-08 profile |
| `srip11.anchor_recall_integrity.v1` | `ARI` | Declared anchor facts retrieved divided by declared anchor facts. | `[0,1]` | `retrieved_declared_anchors / declared_anchors` | `unverified` when denominator is zero | SRIP-11 profile |
| `srip11.fact_extraction_rate.v1` | `FER` | Successful fact extractions divided by extraction attempts. | `[0,1]` | `facts_extracted / extraction_attempts` | `unverified` when denominator is zero | SRIP-11 profile |
| `srip11.fact_coverage.v1` | `FC` | Declared fact categories represented divided by categories evaluated. | `[0,1]` | `represented_categories / evaluated_categories` | `unverified` when denominator is zero | SRIP-11 profile |
| `srip17.provenance_completeness.v1` | `PRC` | Completeness of source, scope, timestamp, and integrity metadata for an exchange artifact. | `[0,1]`, profile-normalized | `profile_defined` | `unverified` when required provenance fields or profile authority are missing | SRIP-17 exchange profile |
| `srip16.meta_coherence.v1` | `MC` | Compatibility between causally ordered meta-vectors or snapshots. | Profile-defined normalized value | `profile_defined` | `unverified` | SRIP-16 measurement profile |
| `srip16.reflective_drift.v1` | `RD` | Change in valid self-model evidence across a declared window. | Profile-defined normalized value | `profile_defined` | `unverified` | SRIP-16 measurement profile |
| `srip16.self_correction_count.v1` | `SCC` | Accepted bounded interventions in a declared window. | Non-negative integer count | exact event count | `unverified` if event authority/window is missing | SRIP-16 event profile |
| `srip16.reflection_budget_ratio.v1` | `RBR` | Reflective budget consumed divided by available declared budget. | `[0,1]` | `reflective_budget_used / available_budget` | `unverified` when denominator is zero | SRIP-16 budget profile |
| `srip16.recovery_recurrence.v1` | `RR` | Recovery or verification event frequency over a declared window. | Non-negative count or rate, profile-declared | `profile_defined` | `unverified` | SRIP-16 event profile |

`SDC` is an AEP profile metric and is not an alias for canonical `SDI`. A
producer must preserve their distinct metric IDs even when both are derived from
semantic displacement evidence.

`PC` is reserved for SRIP-11 Phase Continuity. SRIP-17 Provenance Completeness
uses `PRC`. A historical symbol-only `PC` observation without metric ID and
source-SRIP provenance is ambiguous and therefore `unverified`.

## 3. SDI Collision Migration

Telemetry schema `srs-telemetry-v1` reserves:

- `SDI` exclusively for `srs.semantic_drift_index.v1`;
- `SD` exclusively for `srs.symbolic_density.v1`.

Earlier SRIP-02 text used `SDI` for symbolic density while SRIP-03 used `SDI`
for semantic drift. That legacy collision is superseded by this registry.

Migration rules:

1. New producers must emit `schema_version: srs-telemetry-v1` and stable metric
   IDs, not symbol-only tuples.
2. A legacy SRIP-02 record with explicit `density` field provenance may be
   migrated to `SD` while preserving the original field and source schema ref.
3. A legacy symbol-only `SDI` observation without schema or field provenance is
   `ambiguous` and must be exposed as `unverified`.
4. Consumers must not disambiguate legacy `SDI` from its numeric value,
   neighboring metrics, model, provider, or session date.
5. Persisted historical evidence remains immutable; migration creates a
   versioned projection with lineage to the source record.

Example v1 envelope:

```yaml
schema_version: srs-telemetry-v1
metrics:
  - metric_id: srs.semantic_drift_index.v1
    symbol: SDI
    value: 0.21
    validity: valid
    calibration_profile_ref: profile:example-semantic-drift-v1
  - metric_id: srs.symbolic_density.v1
    symbol: SD
    value: 0.48
    validity: valid
    calibration_profile_ref: profile:example-symbolic-density-v1
```

## 4. Current Implementation Disposition

The v0.9.5 source/dev implementation reviewed on 2026-07-17 does not emit the
canonical metric IDs in this registry and does not produce an
`srs-telemetry-v1` envelope. Existing runtime and UI fields are legacy
implementation telemetry, not silently conforming observations.

The current drift calculation is documented separately in the
[SRIP-03 v0.9.5 implementation profile](implementation-profiles/SRIP-03-drift-monitor-v095-profile.md).
Other canonical metrics remain `unverified` with respect to current public
telemetry conformance until a versioned read-only projection and evidence ref
exist.

## 5. Conformance Boundary

Vocabulary conformance means using the registered meaning and validity rules.
Measurement conformance additionally requires a versioned implementation
profile and evidence reference. A metric marked `profile_defined` cannot support
an implementation-neutral threshold claim by itself.

The public [SRIP Evidence Matrix](evidence-matrix.md) records whether each SRIP
has public specification, implementation, test, and benchmark evidence.
