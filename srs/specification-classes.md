---
title: SRS Specification Classes
description: Public classification of normative, protocol, measurement, governance, research, and implementation-profile documents.
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

# SRS Specification Classes

| Field | Value |
| --- | --- |
| Information Class | `Open` |
| Change Class | `SRS-only` |

Document status and document class answer different questions. `Public Draft`
describes maturity; a specification class describes what kind of conformance
claim the document can support.

| Class | Purpose | Implementation Claim |
| --- | --- | --- |
| Foundational Specification | Defines cross-runtime vocabulary and invariants. | Requires operational conformance criteria and compatible profiles. |
| Runtime Architecture Specification | Defines a runtime component, data boundary, or governed processing layer. | Requires profile-bound implementation evidence for runtime conformance. |
| Runtime Protocol | Defines ordered boundaries, state transitions, authority, or exchange semantics. | May be implemented without prescribing internal algorithms. |
| Measurement Specification | Defines metrics, validity, calibration, and evidence authority. | Requires versioned measurement profiles and validation evidence. |
| Architecture Draft | Defines a proposed layer and its boundaries. | Does not imply implementation readiness. |
| Governance Architecture Draft | Defines authority, contestability, audit, or institutional boundaries. | Does not imply a runtime governance implementation or legal validity. |
| Research Architecture Draft | Defines a falsifiable research direction or candidate architecture. | Requires an evaluation protocol before implementation conformance. |
| Implementation Profile | Binds a specification to concrete algorithms, providers, thresholds, stores, or libraries. | Applies only to the declared profile and evidence scope. |

Every canonical SRIP must declare `Specification Class`. Architecture,
governance, and research drafts remain public and citable, but they must not be
presented as implementation-ready merely because they are in the SRIP registry.

Representative classifications (the canonical class for every SRIP is recorded
in that SRIP's metadata):

- SRIP-11 SMC: `Runtime Architecture Specification`;
- SRIP-15 ADP: `Architecture Draft`;
- SRIP-16 RSM: `Architecture Draft`;
- SRIP-20 ANS: `Governance Architecture Draft`;
- SRIP-22 GRC: `Governance Architecture Draft`;
- SRIP-23 DGL: `Research Architecture Draft`;
- SRIP-27 TMC: `Measurement Specification`;
- SRIP-28 TAL: `Runtime Protocol`.

The [SRIP Evidence Matrix](evidence-matrix.md) tracks public evidence separately
from these classes.
