---
title: SRIP-03 Current Drift Monitor v0.9.5 Implementation Profile
description: Non-normative mapping between the current bounded drift monitor and the SRIP-03 reference metric contract.
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

# SRIP-03 Current Drift Monitor v0.9.5 Implementation Profile

| Field | Value |
| --- | --- |
| Information Class | `Derived-Public` |
| Source Context | Proprietary runtime implementation |
| Sanitization | Formula and conformance boundary only; no internal paths, prompts, private telemetry, or deployment detail |

This document is an `Implementation Profile`, not a change to the normative
SRIP-03 equal-weight reference formula. It records the bounded source/dev
behavior reviewed for the v0.9.5 line so readers do not mistake implementation
telemetry for implementation-neutral SRS metrics.

## Current Computation

For two consecutive assistant responses, the current monitor computes:

```text
semantic_distance = max(0, 1 - cosine_similarity(current, previous))
semantic = clamp(1 - exp(-1.5 * semantic_distance), 0, 1)
tonal = clamp(abs(current_word_count - previous_word_count)
              / max(current_word_count, previous_word_count, 1), 0, 1)
total = round(0.8 * semantic + 0.2 * tonal, 3)
```

`structural` is computed separately and is not included in `total`. The monitor
exposes legacy field names `semantic`, `tonal`, `structural`, and `total`.

## Conformance Disposition

- `total` is not `srs.composite_drift_index.v1` and must not be labeled `DI`.
- `semantic` is not a conforming `srs.semantic_drift_index.v1` observation
  unless a future version binds it to a stable metric ID, window, validity,
  calibration profile, and evidence reference.
- Missing previous-response authority currently produces zero-valued legacy
  fields. That compatibility behavior is not the SRS `unverified` semantics.
- The SRIP-03 equal-weight formula remains a foundational reference profile;
  it is not silently superseded by this implementation profile.

No public threshold, production-conformance, or cross-provider calibration
claim follows from this profile. A future conforming telemetry projection must
use a new schema version rather than reinterpret historical values in place.
