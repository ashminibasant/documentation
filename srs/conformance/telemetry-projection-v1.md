---
title: SRS Telemetry Projection v1
description: Draft read-only envelope for projecting implementation telemetry into canonical SRS metric observations.
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

# SRS Telemetry Projection v1

## Status

| Field | Value |
| --- | --- |
| Information Class | `Open` |
| Change Class | `SRS-only` |
| Publication Status | Local draft; not approved or published |

This is a local draft contract. It has not been published, implemented by the
v0.9.5 runtime, or used to make a conformance claim.

The first canonical schema is `srs-telemetry-v1`. No released
`srs-telemetry-v0` or `srs-telemetry-v1` predecessor exists. The temporary
`srs-telemetry-v2` name used during the July 2026 SDI collision audit is
superseded before publication and does not establish version lineage.

## Purpose

The projection gives implementations a deterministic, machine-readable way to
publish existing measurements under the canonical identities in the
[SRS Metric Registry](/srs/metric-registry).

It is an observation boundary, not a measurement algorithm. It must not:

- change an implementation's metric formula;
- infer missing values or replace them with zero;
- mutate runtime, memory, checkpoints, accepted history, or calibration state;
- select a control posture or authorize an action;
- scan raw transcript text to infer metric meaning;
- expose prompts, message bodies, embeddings, secrets, or actor-specific data.

## Envelope

The machine-readable schema is
[`srs-telemetry-v1.schema.json`](schemas/srs-telemetry-v1.schema.json).
Content-safe conformance examples are stored in
[`srs-telemetry-v1.json`](test-vectors/srs-telemetry-v1.json).

```yaml
schema_version: srs-telemetry-v1
projection_contract: srs_telemetry_projection_v1
action_authority: none
producer:
  implementation_id: sigma-runtime
  implementation_version: 0.9.5
  source_revision_ref: git:sha1:<immutable revision>
observation:
  observation_ref: <content-safe opaque ref>
  scope: runtime_cycle
  sequence: 571
metrics:
  - metric_id: srs.symbolic_density.v1
    symbol: SD
    value_type: scalar
    value: 0.48
    unit: ratio
    validity: degraded
    validity_reasons:
      - calibration_missing
    source_contract_ref: alice_state_v1
    source_field: symbolic_density
    calibration_profile_ref: null
    evidence_ref: null
```

## Observation Rules

1. Metric entries are ordered lexicographically by `metric_id`.
2. A metric ID and symbol must match the Metric Registry exactly.
3. `valid` requires a compatible source contract, implementation profile,
   calibration authority, and evidence reference.
4. `degraded` may carry a value when the value is measured but one declared
   quality condition is impaired. The reason must be explicit.
5. `unverified` must carry `value: null`. Consumers must not infer a value from
   a legacy field, neighboring metric, model, provider, date, or UI state.
6. A legacy symbol-only `SDI` without field/schema provenance is
   `unverified` with `ambiguous_legacy_symbol`.
7. A source field whose formula differs from the registered metric is not
   projected under that metric ID. It is reported as `unverified` with
   `formula_incompatible` or omitted by a declared profile.
8. Reprojection of the same frozen source observation and profile must be
   byte-equivalent after canonical JSON serialization.

JSON Schema validates envelope shape and local type constraints. Lexicographic
metric ordering and exact `metric_id`/`symbol` correspondence with the Metric
Registry are semantic conformance checks and must be validated by a conforming
producer or consumer; schema validity alone does not establish them.

## Validity

The validity states are:

| State | Meaning |
| --- | --- |
| `valid` | Source, formula, profile, calibration, and evidence authority are compatible. |
| `degraded` | A measured value exists, but a declared quality condition is impaired and identified. |
| `unverified` | Meaning, source, profile, calibration, or evidence authority is missing or incompatible. No numeric value is published. |

Validity is not a score and must not be ordered numerically. An implementation
may add a new validity reason only in a new schema version.

## Lineage And Scope

Every envelope is bound to an implementation-neutral immutable source revision
reference and every observation is bound to a content-safe opaque source ref.
The revision reference uses a scheme-qualified form, such as a VCS revision,
content digest, or immutable release artifact identifier; consumers must not
assume Git or SHA-1. Metric entries retain the producing contract and field
names. A profile may project only fields it explicitly maps; neighboring
model/profile adapters cannot substitute for a missing mapping.

Historical source records remain immutable. Migration creates a new projection
with source lineage; it does not rewrite the original telemetry.

## Conformance Boundary

Producing a syntactically valid envelope is schema conformance only. A metric is
measurement-conformant only when its implementation profile and evidence prove
the registered formula, window, units, validity behavior, and calibration
scope. Unknown or unsupported metrics remain `unverified`.

## Source Implementation Gate

A source implementation may be proposed only after its branch authority is
clean and synchronized. The initial implementation must be a pure function with
no database, checkpoint, memory, controller, prompt, or provider dependencies.
It remains default-off and is qualified first against the content-safe test
vectors. Runtime attachment, Observe/Workbench exposure, UI changes, and
production telemetry are separate later gates.
