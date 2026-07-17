---
title: Runtime Telemetry v0.9.5 Mapping
description: Draft mapping from current Sigma Runtime fields to canonical SRS metric identities.
published: false
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

# Runtime Telemetry v0.9.5 Mapping

## Status And Authority

| Field | Value |
| --- | --- |
| Information Class | `Derived-Public` |
| Source Context | Proprietary runtime implementation reviewed through a sanitized mapping |
| Publication Status | Local draft; not approved or published |
| Source Binding | Pending an approved immutable public release/evidence ref |

This mapping intentionally omits internal file paths, private class/method
names, prompts, deployment details, and private telemetry payloads. It records
only the minimum public producer semantics needed for conformance analysis.

The mapping does not make current UI or runtime fields conformant. It prevents
similar names from being treated as equivalent without formula, profile, and
evidence authority.

## Dispositions

| Disposition | Meaning |
| --- | --- |
| `projectable_unverified` | A bounded source field and compatible candidate formula exist, but profile/calibration/evidence requirements are incomplete. |
| `legacy_nonconformant` | A similarly named field exists but its formula or missing-value semantics differ from the registered metric. |
| `not_implemented` | No exact current producer was found. A projection must emit `unverified` or omit it under a declared scope. |

## Metric Mapping

| Metric ID | v0.9.5 source candidate | Disposition | Reason |
| --- | --- | --- | --- |
| `srs.semantic_drift_index.v1` | legacy semantic-drift component | `legacy_nonconformant` | Zero-fills missing previous response and lacks a frozen calibration/evidence profile. |
| `srs.symbolic_density.v1` | ALICE symbolic-density observation | `projectable_unverified` | Bounded calculation exists; normative window, calibration, and evidence profile are not frozen. |
| `srs.symbolic_drift.v1` | none | `not_implemented` | No registered symbolic-density delta producer. |
| `srs.control_posture_drift.v1` | none | `not_implemented` | No expected-versus-observed posture metric producer. |
| `srs.semantic_compression_ratio.v1` | none | `not_implemented` | Existing token compression ratio is not semantic retention. |
| `srs.composite_drift_index.v1` | legacy composite-drift component | `legacy_nonconformant` | Current `0.8 semantic + 0.2 tonal` formula is not canonical DI. |
| `srs.phase_stability_index.v1` | ALICE stability observation | `projectable_unverified` | State exists; declared phase model and calibration evidence are incomplete. |
| `srs.phase_stability_delta.v1` | none | `not_implemented` | No canonical observed-versus-expected PSI producer. |
| `srs.phase_shift_delta.v1` | none | `not_implemented` | Phase transitions exist, but no registered normalized phase-shift metric. |
| `srs.phase_coherence_index.v1` | none | `not_implemented` | Runtime `coherence` is not silently equivalent to phase-vector PCI. |
| `srs.continuity_index.v1` | none | `not_implemented` | No registered SRIP-04 continuity producer. |
| `srs.retention_index.v1` | none | `not_implemented` | No registered retained-motif denominator authority. |
| `srs.entropy_ratio.v1` | none | `not_implemented` | Local entropy signals do not implement the registered estimator contract. |
| `srs.control_carryover.v1` | none | `not_implemented` | No registered cross-window control carryover producer. |
| `srip10.terminological_isometry.v1` | AEP TI observation | `projectable_unverified` | Formula implementation exists; profile, validity, and calibration evidence require freeze. |
| `srip10.semantic_drift_coefficient.v1` | AEP SDC observation | `projectable_unverified` | Formula implementation exists; model/profile calibration is not a public conformance artifact. |
| `srip10.logic_noise_ratio.v1` | AEP L/N observation | `projectable_unverified` | Formula implementation exists; numerator/denominator and calibration profile require freeze. |
| `srip11.compression_ratio.v1` | SMC compression-ratio observation | `projectable_unverified` | Retained/input token counts exist; source lineage and evidence profile are incomplete. |
| `srip11.semantic_loss.v1` | SMC semantic-loss observation | `projectable_unverified` | Cosine-loss calculation exists; embedding/profile compatibility and evidence are incomplete. |
| `srip11.topology_cohesion.v1` | none | `not_implemented` | Graph weights exist without a registered cluster aggregation producer. |
| `srip11.phase_continuity.v1` | none | `not_implemented` | No registered reasoning-vector correlation producer. |
| `srip11.anchor_recall_integrity.v1` | none | `not_implemented` | Retrieval counts lack a declared anchor denominator. |
| `srip11.fact_extraction_rate.v1` | none | `not_implemented` | Fact totals exist, but attempt authority is not emitted. |
| `srip11.fact_coverage.v1` | none | `not_implemented` | No declared evaluated-category denominator. |
| `srip17.provenance_completeness.v1` | none | `not_implemented` | Readiness artifacts do not implement a registered exchange completeness metric. |
| `srip16.meta_coherence.v1` | none | `not_implemented` | No dedicated calibrated RSM producer. |
| `srip16.reflective_drift.v1` | none | `not_implemented` | No dedicated calibrated RSM producer. |
| `srip16.self_correction_count.v1` | none | `not_implemented` | Existing intervention events are not bound to the SRIP-16 event profile. |
| `srip16.reflection_budget_ratio.v1` | none | `not_implemented` | No declared reflective budget denominator. |
| `srip16.recovery_recurrence.v1` | none | `not_implemented` | Recovery events are not bound to a registered SRIP-16 window/profile. |

## Initial Implementation Scope

The first source/dev projection should implement only the seven
`projectable_unverified` mappings. It must publish them as `degraded` or
`unverified` until their profiles and evidence are frozen. The two
`legacy_nonconformant` fields must never be relabeled as canonical metrics.

The remaining metrics stay `unverified`; implementing their measurement
algorithms is outside the telemetry projection and requires separate SRIP work.
