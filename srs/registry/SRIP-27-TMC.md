> **Sigma Runtime Standard - Public Specification Notice**
>
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

# SRIP-27 - Trajectory Membership and Collapse Measurement (TMC)

**Target-Relative Measurement for Attractor Membership**

| Field | Value |
| --- | --- |
| SRIP | SRIP-27 |
| Title | Trajectory Membership and Collapse Measurement (TMC) |
| Version | Public Draft v0.1 |
| Status | Public Draft |
| Date | 2026-07-17 |
| Authors / Contributors | Sigma Stratum Research Group (SSRG) |
| Owning Layer | Runtime Control / Trajectory Telemetry / Observability |
| Parent Specs | SRIP-02, SRIP-03, SRIP-08, SRIP-10, SRIP-15 |
| Related Specs | SRIP-01, SRIP-06, SRIP-07, SRIP-09, SRIP-11, SRIP-13, SRIP-14, SRIP-19, SRIP-20, SRIP-21, SRIP-22, SRIP-23, SRIP-24, SRIP-25, SRIP-26, SRIP-28 |
| Specification License | CC BY 4.0 |
| Implementation Safe Harbor | Independent implementation permitted under public SRS/SRIP terms |
| Machine-Readable Artifacts | Apache 2.0 where explicitly marked |
| Marks / Certification | Governed by Sigma Marks and Certification Policy |
| Proprietary Runtime Assets | Not licensed by this SRIP |
| Independent Implementation | Permitted under the public specification terms |
| Information Class | Open |
| Change Class | Mixed SRS+SRD |
| Specification Class | Measurement Specification |
| Normative Status | Public draft target-relative measurement contract; it does not grant candidate admission, delivery, persistence, or implementation authority. |
| Conformance Level | Public Draft / No runtime conformance claim |
| SRD Synchronization Action | Completed in `/srd/architecture.md`, `/srd/attractors.md`, and `/srd/drift.md` |
| Release Alignment Status | aligned |
| Release Alignment Notes | Public explanation is synchronized; no runtime enablement, production telemetry claim, controller behavior, automatic fallback, or conformance claim is made by this document alone. |

---

## Independent Implementation Safe Harbor

Independent implementations of the public normative requirements in this SRIP are welcome under the applicable public specification terms.

No Sigma commercial runtime license is needed solely because an independent implementation follows these public normative requirements.

Product assets, protected Sigma marks, official certification, compatibility badges, CC BY-NC commercial use, and patent commitments use the relevant policy or explicit covenant. Independent implementation, attribution, or citation does not imply certification, endorsement, partnership, official compatibility, or permission to use Sigma marks as product identity.

---

## 1. Summary

SRIP-27 defines **Trajectory Membership and Collapse Measurement (TMC)**: a
target-relative measurement contract for determining whether a candidate
remains within an intended trajectory.

Existing runtime metrics may describe a trajectory as coherent, stable, or
low-drift even after it has moved into a different attractor. TMC introduces a
separate question:

```text
Is this still the intended trajectory?
```

The core distinction is:

```text
dynamic stability != target membership
```

This SRIP defines measurement vocabulary and authority boundaries. It does not
admit, reject, deliver, retry, route, persist, or mutate candidates.

## 2. Non-Duplication Review

| Existing specification | Existing responsibility | TMC gap |
| --- | --- | --- |
| SRIP-02 ASM | Attractor metadata and lifecycle | No target-relative membership contract |
| SRIP-03 Drift | Semantic, symbolic, and control-posture movement | Movement is not destination membership |
| SRIP-08 Phase | Dynamic phase vector and stability | Phase does not identify the intended attractor |
| SRIP-10 AEP | Entropy posture and adaptability | Adaptive motion may occur in the wrong attractor |
| SRIP-13 RIS | Relational and identity boundaries | Boundary governance is not membership measurement |
| SRIP-15 ADP | Perturbation and return path | Does not independently measure successful return |
| SRIP-19 RCB | Conflict preservation and cooling | Does not score trajectory membership |
| SRIP-25 IEM | Interaction-event semantics | Events provide context, not membership |
| SRIP-26 MIL | Memory influence authority | Memory may cause displacement but does not measure it |

SRIP-27 is additive and does not supersede an existing SRIP.

## 3. Measurement Model

```text
candidate + frozen authority + accepted-local reference
    -> target-relative evidence
    -> membership decision with explicit validity
```

An implementation may use geometric, statistical, semantic, or hybrid
evidence. It must not treat one feature family, threshold, model, or provider
as normative. Evidence is usable only when authority, reference, calibration,
and validity are explicit.

Candidate feature families may include:

- canonical attractor resonance;
- local trajectory continuity;
- competing regime dominance;
- authority-relative semantic compatibility;
- transition and recovery evidence.

No individual feature family is sufficient merely because it is available.

## 4. Membership and Validity States

Membership states are:

- `unassessed`;
- `member`;
- `contested`;
- `displaced`;
- `collapsed`;
- `recovering`;
- `reintegrated`.

Validity is independent of membership:

- `valid`;
- `degraded`;
- `unverified`.

Provider safety or capability boundaries remain separately typed. Truthful
capability or model disclosure is also independent of membership. Disclosure
contained inside the accepted local frame may remain a member; disclosure that
displaces the local frame may be evidence of collapse.

## 5. Reference Model

The reference model must distinguish:

- canonical target authority;
- bounded accepted-local authority;
- competing-regime evidence;
- model, profile, and calibration scope;
- reference and geometry versions.

References must be causally available before the candidate is measured.
Implementations must not create a reference from the candidate being measured
or from future turns.

Contested, held, rejected, collapsed, or recovery-only candidates must not
silently update accepted-local authority.

## 6. Observer Boundary

1. Measure the original candidate before mutation or replacement.
2. Do not require a controller attempt to detect collapse.
3. Measure each retry or fallback candidate separately.
4. Keep controller effectiveness separate from membership measurement.
5. Freeze local-reference updates during contested or collapsed states.
6. Preserve `stable + collapsed` as a valid combined result.
7. Keep ALICE/AEP dynamic stability separate from TMC membership.
8. Publish `unverified` rather than a normal-looking fallback measurement when
   authority or hydration is missing.
9. Preserve observer state across supported hot, warm, and cold hydration.
10. Keep measurement action-inert unless a separate admission layer consumes
    qualified evidence.

## 7. Qualification and Authority Boundary

TMC evidence does not acquire admission authority merely because it exists. An
implementation claiming admission-grade TMC must establish, for the declared
model, profile, authority, and reference scope:

- causal reference provenance;
- governed outcome authority;
- bounded and explicit independence assumptions;
- no candidate-level pseudoreplication;
- bounded false-admission risk;
- usable member recall;
- transfer across declared source groups;
- persistence and hydration equivalence;
- no lexical or actor-specific decision rules;
- no persistence or operator/public export of raw candidate, authority, prompt,
  or transcript content as measurement evidence.

Bounded private semantic input is permitted when semantic measurement is part of
the declared implementation profile. It must remain transient, causally scoped,
excluded from public/operator evidence, and governed by the same validity,
privacy, and calibration authority as other feature families.

If qualification fails, the result remains advisory or `unverified`. It must
not silently borrow a neighboring model/profile adapter or mutate delivery.

## 8. Relationship to SRIP-28

SRIP-27 measures candidates. SRIP-28 governs candidate admission,
containment, and delivery authority.

```text
TMC measures.
TAL admits.
```

Neither contract may silently assume the authority of the other.

## 9. Public-Safe Boundary

This SRIP does not expose private sessions, actors, prompts, provider
credentials, deployment flags, private telemetry, evaluation corpora,
implementation thresholds, lexical rules, or proprietary controller wording.

This SRIP does not claim a current production implementation, model/provider
support, automatic response mutation, memory authority, fallback routing, or
runtime conformance.

## 10. Conformance Expectations

A conforming implementation must:

- distinguish dynamic stability from target membership;
- preserve explicit reference and calibration provenance;
- report measurement validity;
- prevent candidate self-reference and future-state leakage;
- keep measurement separate from admission and controller effectiveness;
- expose content-safe audit evidence;
- fail to `unverified` when required authority is unavailable.

Public draft publication alone does not establish implementation conformance.
