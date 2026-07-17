---
title: Sigma Stratum Registry
description: Authoritative registry tracking post-core Sigma Runtime Improvement Proposals (SRIP-09+) — experimental extensions, governance updates, and long-term evolution of the Sigma Runtime architecture.
published: true
date: 2026-07-17T00:00:00.000Z
tags:
editor: markdown
dateCreated: 2025-12-31T09:55:42.132Z
---

> **Sigma Stratum Documentation - Public Specification Notice**
> This document is part of the **Sigma Runtime Standard (SRS)** public
> specification registry and the **Sigma Runtime Documentation (SRD)**.
>
> Specification License: CC BY 4.0.
>
> Independent implementation of public SRS/SRIP normative requirements is
> permitted under the applicable public specification terms.
>
> This registry does not license Sigma Runtime proprietary product assets,
> official certification, Sigma marks, white-label deployment, resale, managed
> Sigma Runtime deployment, enterprise deployment assets, or commercial use of
> CC BY-NC materials without separate authorization.
>
> For the active policy layer, see [Sigma IP, Licensing, and Certification
> Policy](../legal/ip-licensing-certification-policy.md) and [SRS Public
> Specification License](../legal/srs-public-specification-license.md).

# Sigma Stratum Registry

The **Sigma Stratum Registry** is the authoritative ledger for runtime proposals **beyond the core specification** (SRIP-09 and later).
It records extensions, experimental modules, and structural evolutions of the Sigma Runtime architecture.

---

## Purpose

This registry ensures:
- Transparent tracking of **active and evolving SRIPs**
- Version control and compatibility mapping with **SRS-03 Core**
- Reference linkage to **Zenodo DOIs** and **governance decisions**
- Persistent identifiers for each experimental proposal

All documents registered here form the **living layer** of the Sigma Runtime Standard public specification - a space where research evolves while preserving versioned specification lineage.

---

## Structure

Each SRIP is registered as a standalone entry:
```
/srs/registry/SRIP-09-LTM.md
/srs/registry/SRIP-10-AEP.md
/srs/registry/SRIP-11-SMC.md
/srs/registry/SRIP-12-CDS.md
/srs/registry/SRIP-13-RIS.md
/srs/registry/SRIP-14-RMI.md
/srs/registry/SRIP-15-ADP.md
/srs/registry/SRIP-16-RSM.md
/srs/registry/SRIP-17-MAE.md
/srs/registry/SRIP-18-CSI.md
/srs/registry/SRIP-19-RCB.md
/srs/registry/SRIP-20-ANS.md
/srs/registry/SRIP-21-EIB.md
/srs/registry/SRIP-22-GRC.md
/srs/registry/SRIP-23-DGL.md
/srs/registry/SRIP-24-EIL.md
/srs/registry/SRIP-25-IEM.md
/srs/registry/SRIP-26-MIL.md
/srs/registry/SRIP-27-TMC.md
/srs/registry/SRIP-28-TAL.md
```
Each file must include:
- metadata block including title, version, date, status, author, information class, change class, parent specs, related specs, and release alignment status;
- a `Specification Class` selected from `/srs/specification-classes`;
- summary of purpose and architecture;
- compatibility notes with prior SRIPs and SRS versions;
- license declaration.

`Release Alignment Status` is a governed enum. Any explanatory qualification
must be recorded separately as `Release Alignment Notes`.

---

## Numbering And Reading Order

SRIP numbers are immutable public proposal identifiers.

The registry is numerical and historical. It is not required to match the best conceptual reading order for a given architecture stack.

Rules:

- new SRIP numbers are assigned monotonically when a proposal is accepted into the public draft path;
- existing SRIP numbers are never reassigned to improve logical ordering;
- conceptual ordering is maintained in reading-order views such as `/srs/architecture-reading-order`;
- `Parent Specs`, `Related Specs`, `Extends`, `Amends`, and `Supersedes` describe architecture relationships.

This allows the standard to scale without breaking citations or historical continuity.

---

## Active Registry Entries

| SRIP | Title | Status | Date | Maintainer |
|------|--------|---------|------|-------------|
| [SRIP-09-LTM](registry/SRIP-09-LTM.md) | Long-Term Memory and Structural Coherence Layer (LTM-SC) | **Active Proposal / Partial Implementation** | 2026-04-11 | SSRG |
| [SRIP-10-AEP](registry/SRIP-10-AEP.md) | Adaptive Entropy Protocol (AEP) | **Public Draft v0.2 / Partial Implementation** | 2026-05-20 | SSRG |
| [SRIP-11-SMC](registry/SRIP-11-SMC.md) | Structural Memory Compression (SMC) | **Active / v1.2** | 2026-07-17 | SSRG |
| [SRIP-12-CDS](registry/SRIP-12-CDS.md) | Commerce Decision State Layer (CDS) | **Active Proposal / Partial Implementation** | 2026-04-11 | SSRG |
| [SRIP-13-RIS](registry/SRIP-13-RIS.md) | Relational Identity Stabilization (RIS) | **Active Proposal** | 2026-04-11 | SSRG |
| [SRIP-14-RMI](registry/SRIP-14-RMI.md) | Retrieval and Memory Integration Layer (RMI) | **Active Proposal / Partial Implementation** | 2026-04-28 | SSRG |
| [SRIP-15-ADP](registry/SRIP-15-ADP.md) | Attractor Dynamics and Controlled Perturbation Layer (ADP) | **Public Draft** | 2026-04-28 | SSRG |
| [SRIP-16-RSM](registry/SRIP-16-RSM.md) | Recursive Self-Modeling (RSM) | **Public Draft** | 2026-05-14 | SSRG |
| [SRIP-17-MAE](registry/SRIP-17-MAE.md) | Multi-Agent Exchange (MAE) | **Public Draft** | 2026-05-14 | SSRG |
| [SRIP-18-CSI](registry/SRIP-18-CSI.md) | Commerce Semantic Integration Layer (CSI) | **Public Draft / Implementation-Ready Architecture** | 2026-05-14 | SSRG |
| [SRIP-19-RCB](registry/SRIP-19-RCB.md) | Recursive Contradiction Buffering (RCB) | **Public Draft** | 2026-05-21 | SSRG |
| [SRIP-20-ANS](registry/SRIP-20-ANS.md) | Autonomy Negotiation and Boundary Stabilization (ANS) | **Public Draft** | 2026-05-26 | SSRG |
| [SRIP-21-EIB](registry/SRIP-21-EIB.md) | External Identity Binding and Mode Reconciliation (EIB) | **Public Draft** | 2026-05-26 | SSRG |
| [SRIP-22-GRC](registry/SRIP-22-GRC.md) | Governance Recursion and Collusion Boundary (GRC) | **Public Draft** | 2026-05-28 | SSRG |
| [SRIP-23-DGL](registry/SRIP-23-DGL.md) | Dialectical Generation Layer (DGL) | **Public Draft** | 2026-06-27 | SSRG |
| [SRIP-24-EIL](registry/SRIP-24-EIL.md) | Environment Interface Layer (EIL) | **Public Draft** | 2026-06-27 | SSRG |
| [SRIP-25-IEM](registry/SRIP-25-IEM.md) | Interaction Event Model (IEM) | **Public Draft** | 2026-06-27 | SSRG |
| [SRIP-26-MIL](registry/SRIP-26-MIL.md) | Memory Influence Layer (MIL) | **Public Draft** | 2026-07-05 | SSRG |
| [SRIP-27-TMC](registry/SRIP-27-TMC.md) | Trajectory Membership and Collapse Measurement (TMC) | **Public Draft** | 2026-07-17 | SSRG |
| [SRIP-28-TAL](registry/SRIP-28-TAL.md) | Trajectory Admission Loop (TAL) | **Public Draft** | 2026-07-17 | SSRG |

---

## Deprecated Registry Entries

| SRIP | Title | Status | Date | Maintainer |
|------|--------|---------|------|-------------|
| [SRIP-10-ACE](registry/retired/SRIP-10-ACE.md) | Anti-Crystallization Equilibrium Model (ACE) | **Deprecated (Superseded by AEP)** | 2026-01-07 | SSRG |

### Governance

Registry entries are maintained by the **Sigma Stratum Research Group (SSRG)**.

For conceptual navigation, see:

- [`architecture-reading-order.md`](architecture-reading-order.md)
- [`specification-classes.md`](specification-classes.md)
- [`metric-registry.md`](metric-registry.md)
- [`evidence-matrix.md`](evidence-matrix.md)

For inquiries or submissions:
[contact@sigmastratum.org](mailto:contact@sigmastratum.org)
[github.com/sigmastratum/documentation](https://github.com/sigmastratum/documentation)
