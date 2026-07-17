---
title: SRIP Evidence Matrix
description: Public evidence status for specification, implementation, testing, benchmarking, and unsupported claims across the SRIP corpus.
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

# SRIP Evidence Matrix

| Field | Value |
| --- | --- |
| Information Class | `Open` |
| Change Class | `SRS-only` |

This matrix reports evidence visible in the public documentation repository. It
does not inspect private runtime code, private evaluation corpora, production
telemetry, or unpublished tests.

## Status Vocabulary

| Status | Meaning |
| --- | --- |
| `specified` | A public contract or draft exists. |
| `implemented` | A public artifact or explicit release-scoped implementation claim is linked. |
| `tested` | Reproducible test or validation evidence is linked to the SRIP surface. |
| `benchmarked` | A dataset/run manifest and measured comparison are publicly linked. |
| `unsupported` | Public evidence is insufficient for the stronger claim. This does not prove non-implementation. |

`system-level` means a report exercises a runtime containing multiple layers but
does not isolate the named SRIP. It cannot establish layer-specific causality.

## Corpus Matrix

| SRIP | Specification | Implementation Evidence | Test Evidence | Benchmark Evidence | Public Evidence Disposition |
| --- | --- | --- | --- | --- | --- |
| SRIP-00 | specified | system-level only | system-level only | none isolated | unsupported for layer-specific conformance |
| SRIP-01 | specified | system-level only | system-level only | none isolated | unsupported for layer-specific conformance |
| SRIP-02 | specified | system-level only | system-level only | none isolated | unsupported for metric conformance without profile |
| SRIP-03 | specified | [bounded drift-monitor profile](implementation-profiles/SRIP-03-drift-monitor-v095-profile.md) | no linked conformance suite | none isolated | current implementation is profile-bound, not equal-weight reference conformance |
| SRIP-04 | specified | system-level only | system-level only | none isolated | unsupported for implementation-neutral thresholds |
| SRIP-05 | specified | historical interoperability lineage | no linked conformance suite | none isolated | unsupported for current protocol certification |
| SRIP-06 | specified | system-level safety claims | system-level only | none isolated | unsupported for layer-specific conformance |
| SRIP-07 | specified | system-level only | system-level only | none isolated | unsupported for metric conformance without profile |
| SRIP-08 | specified | system-level only | system-level only | none isolated | unsupported for phase-model conformance without profile |
| SRIP-09 | specified | partial implementation claim | no linked isolated suite | none isolated | unsupported for full conformance |
| SRIP-10 | specified | partial implementation claim | public validation tables | historical named-run artifacts | bounded historical validation; unsupported for current isolated conformance |
| SRIP-11 | specified | historical applicability claim and reference profile | no linked isolated suite | historical target only | unsupported for the historical `10x` claim |
| SRIP-12 | specified | bounded feature-gated implementation claim | no public linked conformance suite | none | partial implementation; unsupported for full conformance |
| SRIP-13 | specified | active proposal claim | none linked | none isolated | unsupported for full conformance |
| SRIP-14 | specified | partial implementation claim | none linked in public SRIP | none isolated | unsupported for full conformance |
| SRIP-15 | specified | architecture draft | none linked | ablation required | unsupported for comparative benefit claims |
| SRIP-16 | specified | architecture draft | none linked | none | unsupported for calibrated pressure measurement |
| SRIP-17 | specified | protocol draft | none linked | none | unsupported for implementation conformance |
| SRIP-18 | specified | implementation-ready architecture claim | none linked | none | unsupported for runtime conformance |
| SRIP-19 | specified | architecture draft | none linked | none | unsupported for calibrated contradiction energy |
| SRIP-20 | specified | governance architecture draft | none linked | none | unsupported for runtime enablement |
| SRIP-21 | specified | architecture draft | none linked | none | unsupported for runtime conformance |
| SRIP-22 | specified | governance architecture draft | none linked | none | unsupported for runtime or legal legitimacy claims |
| SRIP-23 | specified | research architecture draft | none linked | none | unsupported pending evaluation protocol |
| SRIP-24 | specified | architecture draft | none linked | none | unsupported for runtime conformance |
| SRIP-25 | specified | semantic protocol draft | none linked | none | unsupported for event-model conformance |
| SRIP-26 | specified | architecture draft | none linked | none | unsupported for runtime conformance |
| SRIP-27 | specified | measurement draft | none public | none public | unsupported for public measurement conformance |
| SRIP-28 | specified | admission protocol draft | none public | none public | unsupported for public admission conformance |

## Public Historical Evidence References

- [SRIP-10 empirical results](registry/SRIP-10-AEP.md#45-empirical-results-non-normative-validation-evidence)
- [SRIP-10 empirical target corridors and benchmark tables](registry/SRIP-10-AEP.md#appendix-b-empirical-target-corridors-non-normative-calibration-evidence)
- [Sigma Runtime v0.3.7 Comprehensive Validation Report](../sigma-runtime/SR-EI-037/SIGMA_Runtime_0_3_7_CVR.md)
- [PTR-500 v0.5.0 validation suite](../sigma-runtime/SR-050/README.md)
- [PTR-500 AEP validation v3](../sigma-runtime/SR-052/README.md)

These reports and datasets are openly available historical evidence. A package
is classified as benchmark evidence only when its dataset, run manifest,
estimator, model/profile scope, and reproducible verdict are all declared. None
of these references, by itself, validates every later SRIP or current runtime
conformance.

## Update Rule

An evidence status may be strengthened only by adding a stable evidence ref,
declared scope, model/profile binding where applicable, dataset or fixture
authority, and a reproducible verdict. Removing an unsupported marker without
new evidence is not permitted.
