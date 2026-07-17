---
title: Runtime Model and Profile Binding v0.9.5
description: Non-normative compatibility map for Gemini 3.5 calibration identifiers and Admin-visible aliases.
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

# Runtime Model and Profile Binding v0.9.5

| Field | Value |
| --- | --- |
| Information Class | `Derived-Public` |
| Source Context | Proprietary runtime model/profile registry |
| Sanitization | Public compatibility identifiers only; no credentials, provider configuration, or deployment topology |

This non-normative implementation profile records an identifier compatibility
surface for the v0.9.5 source line. It does not prescribe model providers or
make a lifecycle or availability guarantee.

| Runtime Mode | Internal Calibration Profile | Admin Alias | Base Profile |
| --- | --- | --- | --- |
| `standard` | `sigma_standard-gemini35` | `sigma_standard-gemini-3.5` | `sigma_standard-gemini` |
| `attractor_plus` | `sigma_attractor_plus-gemini35` | `sigma_attractor_plus-gemini-3.5` | `sigma_attractor_plus-gemini` |

The internal ID and Admin alias resolve to the same calibrated profile. The
runtime must preserve both requested and resolved identifiers in evidence when
their distinction matters; operators must not infer a concrete model solely
from a profile string.

Model selection remains lifecycle-registry-bound. A future model generation
requires a new compatibility binding and validation evidence rather than silent
reuse of these identifiers.
