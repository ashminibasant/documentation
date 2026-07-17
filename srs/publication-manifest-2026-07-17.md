---
title: Documentation Publication Manifest - 2026-07-17
description: Owner-review manifest for the SRS, SRIP, SRD, telemetry, evidence, and licensing publication package.
published: true
date: 2026-07-17T00:00:00.000Z
tags:
editor: markdown
dateCreated: 2026-07-17T00:00:00.000Z
---

> **Sigma Runtime Standard - Public Specification Notice**
>
> This manifest is licensed under Creative Commons Attribution 4.0
> International (`CC BY 4.0`). It does not alter the per-file licenses of the
> artifacts it inventories.

# Documentation Publication Manifest - 2026-07-17

## Publication Authority

| Field | Value |
| --- | --- |
| Information Class | `Open` |
| Package Status | `owner_review_pending` |
| Source Branch | `main` |
| Base Revision | `git:0d216c035c8ca0c96a6b9d64102ab74379dc9733` |
| Push Status | Not pushed |
| Runtime Implementation | Excluded |
| CI/Checker Automation | Excluded |
| WikiJS Deployment | Excluded |
| Git History Rewrite | Excluded |

This package prepares public documentation only. It does not publish private
runtime code, operational state, production telemetry, session data, agent
bindings, prompts, or secrets.

## Logical Commit Inventory

The commit refs below are the immutable exact file inventories for the first
three package components. The evidence/licensing component contains this
manifest and therefore receives its commit ref only in the owner handoff after
commit creation.

| Order | Commit | Files | Scope | License Authority |
| --- | --- | ---: | --- | --- |
| 1 | `7576d03` | 8 | Metric registry, telemetry v1 schema/projection/vectors, drift and telemetry profiles, SRIP-02/03 synchronization | SRS prose `CC BY 4.0`; explicitly marked machine-readable artifacts `Apache-2.0` |
| 2 | `ae4d877` | 32 | Specification classes, SMC canonical boundary/reference profiles, SRIP normalization, ADP/RSM hardening | Explicit per-file public SRS or documentation notice |
| 3 | `8984c97` | 22 | SRIP-27 TMC, SRIP-28 TAL, registry/reading-order, SRD and governance synchronization | Explicit per-file `CC BY 4.0` or `CC BY-NC 4.0` notice |
| 4 | Pending in this worktree | 20 | Open historical evidence licensing, conformance navigation, evidence matrix, integrity correction, license backlog, and publication manifests | Explicit per-file notice or immutable package manifest authority |

## Component File And License Inventory

### Telemetry Contract

Commit `7576d03` contains:

- `srs/conformance/schemas/srs-telemetry-v1.schema.json` - `Apache-2.0`;
- `srs/conformance/test-vectors/srs-telemetry-v1.json` - `Apache-2.0`;
- six SRS/profile Markdown files - explicit `CC BY 4.0` public
  specification notices.

### Normative SRIP Cleanup

Commit `ae4d877` is the exact 32-file inventory. It contains canonical SRS
documents, compatibility redirects, implementation profiles, governance text,
and the SRIP template. Each changed file states its own authority. The canonical
SMC contract is implementation-neutral; concrete defaults and backend examples
are isolated in a non-normative reference profile.

### TMC, TAL, Registry, And SRD

Commit `8984c97` is the exact 22-file inventory. SRS/SRIP normative documents use
their explicit `CC BY 4.0` notices. SRD and governance documents retain their
explicit `CC BY-NC 4.0` notices. This component does not relicense either class.

### Historical Evidence And Conformance

The fourth component contains the following publication files:

- `sigma-runtime/SR-050/README.md`;
- `sigma-runtime/SR-050/PUBLICATION-MANIFEST.md`;
- `sigma-runtime/SR-050/ARTIFACT-INVENTORY.sha256`;
- `sigma-runtime/SR-EI-0412/README.md`;
- `sigma-runtime/SR-EI-0412/SIGMA_Runtime_SR-EI-0412_Model_Agnostic_Validation.md`;
- `sigma-runtime/SR-EI-0412/PUBLICATION-MANIFEST.md`;
- `sigma-runtime/SR-EI-0412/ARTIFACT-INVENTORY.sha256`;
- `sigma-runtime/SR-EI-047/README.md`;
- `sigma-runtime/SR-EI-047/SIGMA_Runtime_v047_memory_module_200-test.md`;
- `sigma-runtime/SR-EI-047/PUBLICATION-MANIFEST.md`;
- `sigma-runtime/SR-EI-047/ARTIFACT-INVENTORY.sha256`;
- five files under `srs/conformance/`;
- `srs/evidence-matrix.md`;
- `team/repository-integrity-report-v09.md`;
- `team/repository-license-remediation-backlog.md`;
- this manifest.

The three evidence inventories cover 60 historical artifacts by path and SHA-256:

| Package | Inventory | Covered Artifacts | Manifest License | Default Unmarked Artifact License |
| --- | --- | ---: | --- | --- |
| SR-050 | `sigma-runtime/SR-050/ARTIFACT-INVENTORY.sha256` | 52 | `CC BY 4.0` | `CC BY-NC 4.0` |
| SR-EI-0412 | `sigma-runtime/SR-EI-0412/ARTIFACT-INVENTORY.sha256` | 5 | `CC BY 4.0` | `CC BY-NC 4.0` |
| SR-EI-047 | `sigma-runtime/SR-EI-047/ARTIFACT-INVENTORY.sha256` | 3 | `CC BY 4.0` | `CC BY-NC 4.0` |

An explicit existing per-file license always takes precedence over a package
default. Raw JSON, PDF, image, and dialogue-derived artifacts remain unchanged.

## Validation Record

The package is publication-ready only when all of the following remain true at
the final commit:

- telemetry positive vectors pass and every declared negative vector fails;
- the canonical registry contains 29 unique SRIP IDs with complete metadata;
- local Markdown links resolve after URL decoding;
- all three artifact inventories pass SHA-256 verification;
- the public tree contains no proprietary information-class declaration for
  these three historical evidence packages;
- no deleted checker or GitHub Actions workflow is referenced;
- changed and new files have explicit license authority;
- no private filesystem path, session/agent identifier, prompt, or secret is
  introduced by this publication diff;
- `git diff --check` passes;
- no push has occurred.

The final owner handoff records the validation commands, results, fourth commit
ref, branch status, and any deviation from this manifest.

## Evidence Limitations

Historical evidence is scoped to its named run, model, profile, version,
dataset, and historical metric definition. Public availability does not imply
current runtime conformance, production readiness, causal isolation of every
SRIP layer, or transfer to another provider/model generation.

The evidence matrix uses `benchmarked` only when a public dataset, run manifest,
estimator, and reproducible verdict are available. `specified`, `implemented`,
`tested`, and `benchmarked` are independent evidence states and are not inferred
from one another.

## Remaining License Work

The bounded repository-wide debt is recorded in
[`team/repository-license-remediation-backlog.md`](../team/repository-license-remediation-backlog.md).
It identifies 27 unchanged Markdown files that still require explicit
content-owner license authority. That debt is not silently relicensed by this
package and does not leave any new or modified publication file unclassified.

## Owner Gate

Creation of the four local commits does not authorize publication. Push remains
blocked until an explicit owner review and separate approval.
