# SRIP Relationship Evidence Audit

Status: **Non-normative review draft**
Date: 2026-07-17

This document audits every edge in `srip-dependency-graph.yaml` against the
canonical SRIP metadata and relationship sections. It does not amend sources.

## Review Vocabulary

| Status | Meaning |
| --- | --- |
| `confirmed` | Directly supported by parent metadata, normative scope, or an explicit relationship/control section. |
| `inferred` | Architecturally plausible, but the exact type or direction is not explicitly declared. |
| `needs_decision` | Some relationship is supported, but not the strength represented by the graph, or it affects authority. |
| `conflict` | Contradicts the canonical source. |

`Parent Specs` proves a dependency but does not automatically prove that the
best integration verb is `extends`, `specializes`, or `governs`.

## Edge Audit

| # | Graph edge | Status | Canonical evidence and finding |
| --- | --- | --- | --- |
| 1 | `01 depends_on 00` | confirmed | SRIP-01 parent 00; direct foundational dependency. |
| 2 | `02 extends 01` | confirmed | SRIP-02 parent 01; attractor state extends runtime semantics. |
| 3 | `03 provides_evidence_to 02` | confirmed | SRIP-03 parent 02; drift metrics consume attractor state. |
| 4 | `04 extends 01` | inferred | SRIP-04 parents are 02 and 03; SRIP-01 is not declared. |
| 5 | `05 depends_on 00` | inferred | SRIP-05 parents are 02, 03, 04, and 06; 00 is indirect. |
| 6 | `06 constrains 01` | confirmed | SRIP-06 defines bounded runtime operation and safe-mode transitions. |
| 7 | `07 provides_evidence_to 02` | confirmed | SRIP-07 parent 02; density participates in attractor formation. |
| 8 | `08 provides_evidence_to 01` | inferred | SRIP-08 parents are 03, 05, and 06; exact edge to 01 is undeclared. |
| 9 | `09 extends 04` | confirmed | SRIP-09 parent 04. |
| 10 | `10 extends 03` | confirmed | SRIP-10 parent 03; AEP adds entropy regulation. |
| 11 | `10 related_to 07` | inferred | Conceptual density and entropy coupling is retained without a normative dependency. |
| 12 | `11 extends 09` | confirmed | SRIP-11 parent 09. |
| 13 | `13 specializes 06` | confirmed | SRIP-13 parent 06 and identity/safety scope. |
| 14 | `14 extends 04` | inferred | SRIP-14 lists 04 as related; its parents are 09 and 11. |
| 15 | `14 depends_on 09` | confirmed | Parent metadata and explicit integration section. |
| 16 | `14 depends_on 11` | confirmed | Parent metadata and explicit integration section. |
| 17 | `15 extends 02` | inferred | SRIP-15 operates on attractors, but 02 is not declared. |
| 18 | `15 depends_on 06` | confirmed | SRIP-15 now lists 06 as a parent and its Control Precedence makes safety constraining. |
| 19 | `06 constrains 15` | confirmed | SRIP-15 normative scope and Control Precedence section. |
| 20 | `16 provides_evidence_to 01` | inferred | SRIP-16 defines reflective evidence; parent metadata omits 01. |
| 21 | `17 extends 05` | confirmed | Parent metadata and explicit interoperability section. |
| 22 | `18 specializes 14` | confirmed | Parent metadata and explicit RMI relationship. |
| 23 | `12 governs 18` | confirmed | SRIP-18 says CDS retains deterministic decision authority. |
| 24 | `19 recovers 03` | confirmed | SRIP-19 parent 03; buffering responds to instability. |
| 25 | `19 depends_on 06` | confirmed | SRIP-19 parent 06. |
| 26 | `19 depends_on 13` | confirmed | Parent metadata and relationship section. |
| 27 | `19 related_to 15` | confirmed | SRIP-19 lists 15 as related; RCB remains usable without ADP. |
| 28 | `20 extends 13` | confirmed | SRIP-20 parent 13. |
| 29 | `20 governs 16` | confirmed | SRIP-20 treats RSM as evidence and denies it autonomous authority. |
| 30 | `20 constrains 17` | confirmed | SRIP-20 parent 17 and bounds exchanged influence. |
| 31 | `21 extends 13` | confirmed | Parent metadata and explicit RIS relationship. |
| 32 | `21 constrains 14` | confirmed | Parent metadata and explicit RMI relationship. |
| 33 | `21 feeds 19` | confirmed | Parent metadata and explicit RCB handoff. |
| 34 | `22 constrains 17` | confirmed | Parent metadata and explicit MAE relationship. |
| 35 | `22 governs 20` | confirmed | Parent metadata and explicit ANS relationship. |
| 36 | `23 depends_on 15` | confirmed | SRIP-23 parent 15. |
| 37 | `23 depends_on 19` | confirmed | SRIP-23 parent 19. |
| 38 | `22 governs 23` | confirmed | SRIP-23 parent 22 and governance required for promotion. |
| 39 | `24 extends 05` | confirmed | SRIP-24 parent 05. |
| 40 | `24 depends_on 14` | confirmed | SRIP-24 parent 14. |
| 41 | `24 depends_on 21` | confirmed | SRIP-24 parent 21. |
| 42 | `24 depends_on 22` | confirmed | SRIP-24 parent 22. |
| 43 | `22 constrains 24` | confirmed | EIL authority and governance invariants. |
| 44 | `25 specializes 24` | confirmed | Parent metadata and explicit EIL relationship. |
| 45 | `25 depends_on 22` | confirmed | SRIP-25 parent 22. |
| 46 | `22 constrains 25` | confirmed | IEM governance and event-authority invariants. |
| 47 | `26 extends 04` | confirmed | SRIP-26 parent 04. |
| 48 | `26 depends_on 09` | confirmed | SRIP-26 parent 09. |
| 49 | `26 depends_on 14` | confirmed | SRIP-26 parent 14. |
| 50 | `26 feeds 20` | confirmed | SRIP-20 is related; MIL evidence feeds ANS without taking authority. |

## Audit Summary

| Status | Count |
| --- | ---: |
| confirmed | 43 |
| inferred | 7 |
| needs_decision | 0 |
| conflict | 0 |

No edge directly contradicts canonical text. Seven explanatory edges remain inferred; no edge is waiting on an unresolved dependency decision.

## Decision Register

### D1. Transitive foundational edges

`04 -> 01` and `05 -> 00` are useful explanatory shortcuts, but the headers use
more specific parents. Keep them as `inferred` presentation edges rather than
silently changing source metadata.

### D2. Telemetry targets

`08 -> 01` and `16 -> 01` describe evidence returning to runtime control, but
neither source declares 01 as a parent. Consider a graph-only `feeds_runtime`
view rather than changing source metadata for visualization.

### D3. AEP and symbolic density

Resolved: represent this as inferred `10 related_to 07`. No SRIP-10 source change is required unless a future AEP review makes symbolic density mandatory.

### D4. ADP attractor and safety dependencies

Resolved for safety: SRIP-06 is now a direct SRIP-15 parent. SRIP-02 remains an inferred architecture edge and is not added to the header.

### D5. RCB and perturbation

Resolved: use `19 related_to 15`; contradiction buffering remains usable when ADP is not implemented.

### D6. Control authority chain

`16 -> 20 -> 22` is supported as evidence -> autonomy boundary -> governance
legitimacy. It must not imply that GRC can override non-bypassable SRIP-06
safety. That question remains in the control-precedence review.

## Source-Change Boundary

This audit does not justify editing all headers. Source changes should occur
only when the owner intentionally changes a normative dependency or authority
boundary. Transitive presentation relationships belong in the integration graph
with lower confidence made explicit.
