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
| Current Runtime Implementation | Excluded |
| CI/Checker Automation | Excluded |
| WikiJS Deployment | Excluded |
| Git History Rewrite | Excluded |

This package prepares public documentation and intentionally approved historical
research artifacts only. It does not publish proprietary current runtime code,
operational state, production telemetry, private session data, private agent
bindings, private prompts, or secrets.

## Logical Commit Inventory

The commit refs below are the immutable exact file inventories for the first
six package components. The repaired architecture-synthesis integration is
identified by the merge commit containing this manifest; this avoids a
self-referential commit hash while retaining source commit ancestry.

| Order | Commit | Files | Scope | License Authority |
| --- | --- | ---: | --- | --- |
| 1 | `7576d03` | 8 | Metric registry, telemetry v1 schema/projection/vectors, drift and telemetry profiles, SRIP-02/03 synchronization | SRS prose `CC BY 4.0`; explicitly marked machine-readable artifacts `Apache-2.0` |
| 2 | `ae4d877` | 32 | Specification classes, SMC canonical boundary/reference profiles, SRIP normalization, ADP/RSM hardening | Explicit per-file public SRS or documentation notice |
| 3 | `8984c97` | 22 | SRIP-27 TMC, SRIP-28 TAL, registry/reading-order, SRD and governance synchronization | Explicit per-file `CC BY 4.0` or `CC BY-NC 4.0` notice |
| 4 | `4b44ed6` | 20 | Open historical evidence licensing, conformance navigation, evidence matrix, integrity correction, license audit record, and publication manifests | Explicit per-file notice or immutable package manifest authority |
| 5 | `9b6f8f4` | 48 | Repository-wide explicit Markdown license closure and affected inventory hashes | Public policy/template text `CC BY 4.0`; documentation and historical/reference research `CC BY-NC 4.0` |
| 6 | `df50e66` | 49 | Repository-wide non-Markdown authority, legal consistency, and link repair | Manifest metadata `CC BY 4.0`; unmarked historical/reference artifacts `CC BY-NC 4.0` |
| 7 | Containing merge commit | 11 | Repaired SRIP architecture synthesis, dependency graph/audit, control precedence, reading-order integration, and repository-count synchronization | Five integration documents `CC BY 4.0`; two YAML review artifacts `Apache-2.0`; existing records retain their explicit licenses |

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

### Repaired Architecture Synthesis

The seventh component integrates the architecture review lineage from
`git:9ee173584c41d779401d1dba5488d86179c46281`, authored by Volodymyr
Riabinskyi, while preserving the current canonical SRIP authority.

It contains:

- `srs/srip-architecture-synthesis.md`;
- `srs/srip-control-precedence.md`;
- `srs/srip-relationship-matrix.md`;
- `srs/srip-relationship-audit.md`;
- `srs/srip-architecture-diagrams.md`;
- `srs/srip-dependency-graph.yaml`;
- `srs/srip-dependency-reviews.yaml`;
- synchronization changes to the reading order and publication/license audit
  records.

The repaired graph separates all 98 canonical `Parent Specs` edges from a
selected non-normative integration overlay. It retains SRIP-06 as an ADP safety
constraint rather than silently changing SRIP-15 parent metadata, uses SMC as
the canonical SRIP-11 name, and includes SRIP-27 TMC and SRIP-28 TAL.

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

The package inventories cover historical and reference artifacts by path and
SHA-256:

| Package | Inventory | Covered Artifacts | Manifest License | Default Unmarked Artifact License |
| --- | --- | ---: | --- | --- |
| SR-050 | `sigma-runtime/SR-050/ARTIFACT-INVENTORY.sha256` | 52 | `CC BY 4.0` | `CC BY-NC 4.0` |
| SR-EI-0412 | `sigma-runtime/SR-EI-0412/ARTIFACT-INVENTORY.sha256` | 5 | `CC BY 4.0` | `CC BY-NC 4.0` |
| SR-EI-047 | `sigma-runtime/SR-EI-047/ARTIFACT-INVENTORY.sha256` | 3 | `CC BY 4.0` | `CC BY-NC 4.0` |
| Root assets | `ASSET-INVENTORY.sha256` | 4 | `CC BY 4.0` | `CC BY-NC 4.0` |
| Runtime references | `runtime/ARTIFACT-INVENTORY.sha256` | 15 | `CC BY 4.0` | `CC BY-NC 4.0` |
| SR-052 | `sigma-runtime/SR-052/ARTIFACT-INVENTORY.sha256` | 36 | `CC BY 4.0` | `CC BY-NC 4.0` |
| SR-053 | `sigma-runtime/SR-053/ARTIFACT-INVENTORY.sha256` | 20 | `CC BY 4.0` | `CC BY-NC 4.0` |
| SR-EI-03 | `sigma-runtime/SR-EI-03/ARTIFACT-INVENTORY.sha256` | 8 | `CC BY 4.0` | `CC BY-NC 4.0` |
| SR-EI-037 | `sigma-runtime/SR-EI-037/ARTIFACT-INVENTORY.sha256` | 23 | `CC BY 4.0` | `CC BY-NC 4.0` |
| SR-EI-046 | `sigma-runtime/SR-EI-046/ARTIFACT-INVENTORY.sha256` | 3 | `CC BY 4.0` | `CC BY-NC 4.0` |

An explicit existing per-file license always takes precedence over a package
default. Raw JSON, PDF, image, and dialogue-derived artifacts remain unchanged.

### Repository-Wide License Closure

The fifth component adds explicit top-of-document license notices to 43
Markdown documents. Five were already package-inventoried but lacked a
qualifying top notice: four relied only on the package default, while
`PTR-500.md` also carried a compatible footer license. Their two affected hash
inventories are refreshed. Together with the audit/publication records, the
component contains 48 files.

The strict final inventory after artifact-authority repair is:

- 292 tracked files audited;
- 142 Markdown files with explicit per-document license authorities;
- 10 path-and-hash package inventories covering 169 artifacts;
- 5 standalone machine-readable artifacts with embedded license authority;
- 0 Markdown files relying only on package defaults;
- 0 open license-remediation items.

## Validation Record

The package is publication-ready only when all of the following remain true at
the final commit:

- telemetry positive vectors pass and every declared negative vector fails;
- the canonical registry contains 29 unique SRIP IDs with complete metadata;
- the architecture graph contains 29 nodes and exactly matches all 98 declared
  canonical parent edges;
- local Markdown links resolve after URL decoding;
- all 10 artifact inventories pass SHA-256 verification;
- the public tree contains no proprietary information-class declaration for
  the historical and reference packages in this manifest;
- no deleted checker or GitHub Actions workflow is referenced;
- all 142 Markdown files have explicit per-document license authority;
- no private filesystem path, session/agent identifier, prompt, or secret is
  introduced by this publication diff;
- `git diff --check` passes;
- no push has occurred.

The final owner handoff records the validation commands, results, containing
commit ref, branch status, and any deviation from this manifest.

## Evidence Limitations

Historical evidence is scoped to its named run, model, profile, version,
dataset, and historical metric definition. Public availability does not imply
current runtime conformance, production readiness, causal isolation of every
SRIP layer, or transfer to another provider/model generation.

The evidence matrix uses `benchmarked` only when a public dataset, run manifest,
estimator, and reproducible verdict are available. `specified`, `implemented`,
`tested`, and `benchmarked` are independent evidence states and are not inferred
from one another.

## License Closure

The completed repository-wide audit is recorded in
[`team/repository-license-remediation-backlog.md`](../team/repository-license-remediation-backlog.md).
The initial 27-file lexical backlog was superseded by a stricter Markdown audit
and then a repository-wide artifact audit. All resulting items are resolved in
the local publication tree.

## Owner Gate

Creation of local commits does not authorize publication. Push remains
blocked until an explicit owner review and separate approval.
