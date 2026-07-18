---
title: Repository License Authority Remediation Record
description: Completed repository-wide audit of explicit and hash-bound license authority across the public documentation repository.
published: true
date: 2026-07-18T00:00:00.000Z
tags:
editor: markdown
dateCreated: 2026-07-17T00:00:00.000Z
---

> **Sigma Stratum Documentation - License Notice**
>
> This audit record is licensed under Creative Commons
> Attribution-NonCommercial 4.0 International (`CC BY-NC 4.0`).

# Repository License Authority Remediation Record

## Completion Status

| Field | Value |
| --- | --- |
| Status | `complete` |
| Audit Date | 2026-07-18 |
| Tracked Files Audited | 292 |
| Markdown Files Audited | 142 |
| Explicit Per-Document Authorities | 142 |
| Package-Only Markdown Authorities | 0 |
| Hash-Bound Package Inventories | 10 |
| Hash-Bound Package Artifacts | 169 |
| Explicit Standalone Machine Artifacts | 5 |
| Open Remediation Items | 0 |
| Push Status | Not pushed |

The repository-level `LICENSE` requires each document to identify its own
license. The initial lexical audit found 27 files that did not contain a license
marker. A stricter authority audit then rejected incidental mentions of the word
`license`, policy links, and package defaults as substitutes for a document's
own notice.

That stricter audit produced a finite closure set of 43 Markdown files:

- 9 public legal/policy documents;
- 1 reusable public license template;
- 2 root/governance documentation files;
- 31 historical or reference research documents.

All 43 now state an explicit top-of-document license. Five of them were already
covered by hash-bound package inventories but lacked a qualifying top notice:
four relied only on the package default, while `PTR-500.md` also carried a
compatible footer license. The affected `SR-050` and `SR-EI-0412` inventories
were updated to their new content hashes.

A second repository-wide pass then inspected every tracked extension rather
than only `*.md`. It found 72 binary, structured-data, and extensionless
artifacts without an unambiguous per-file or hash-bound authority after embedded
PDF notices were considered. Seven publication manifests now bind every file in
those scopes to immutable path-and-hash inventories. To avoid split authority,
the new inventories cover all 84 existing non-Markdown artifacts in those
scopes, including source files already covered by the repository source-code
default and PDFs with embedded notices.

The complete package-authority set is:

| Scope | Covered Artifacts | Default Unmarked Artifact License |
| --- | ---: | --- |
| Root research and visual assets | 4 | `CC BY-NC 4.0` |
| `runtime/` reference artifacts | 15 | `CC BY-NC 4.0` |
| `sigma-runtime/SR-050/` | 52 | `CC BY-NC 4.0` |
| `sigma-runtime/SR-052/` | 36 | `CC BY-NC 4.0` |
| `sigma-runtime/SR-053/` | 20 | `CC BY-NC 4.0` |
| `sigma-runtime/SR-EI-03/` | 8 | `CC BY-NC 4.0` |
| `sigma-runtime/SR-EI-037/` | 23 | `CC BY-NC 4.0` |
| `sigma-runtime/SR-EI-0412/` | 5 | `CC BY-NC 4.0` |
| `sigma-runtime/SR-EI-046/` | 3 | `CC BY-NC 4.0` |
| `sigma-runtime/SR-EI-047/` | 3 | `CC BY-NC 4.0` |

The repaired SRIP architecture synthesis adds five non-normative public
integration documents under explicit `CC BY 4.0` notices and two
machine-readable YAML review artifacts under explicit `Apache-2.0` authority.
They are self-licensed and do not rely on a package default or hash inventory.

## License Disposition

| Document Class | Files Updated | License |
| --- | ---: | --- |
| Public legal and policy texts | 9 | `CC BY 4.0` |
| Reusable public license template | 1 | `CC BY 4.0` |
| Root and governance documentation | 2 | `CC BY-NC 4.0` |
| Historical and reference research documents | 31 | `CC BY-NC 4.0` |
| New publication manifests | 7 | `CC BY 4.0` |
| New immutable inventories | 7 | `CC BY 4.0` metadata; package default for listed artifacts |
| Public architecture integration reviews | 5 | `CC BY 4.0` |
| Machine-readable architecture review artifacts | 2 | `Apache-2.0` |

The public-policy notices license document text only. They do not grant rights
to Sigma marks, certification, patents, or proprietary runtime assets. Research
notices do not override explicit licenses on referenced software, datasets, or
other artifacts.

## Integrity Rules

- Existing explicit per-file terms always take precedence over directory or
  package defaults.
- Historical report bodies remain semantically unchanged; raw JSON/PDF/image
  artifacts remain byte-for-byte unchanged.
- A future Markdown file must include an explicit self-license notice; a casual
  reference to licensing elsewhere in the text is insufficient.
- Binary or structured artifacts may use a package authority only when an
  immutable path-and-hash inventory unambiguously covers them.
- Any license change remains a content-owner and legal-review action rather than
  an automated inference.
- A package manifest declares publication authority for listed artifacts; it
  does not independently prove third-party chain-of-title or provider-output
  rights outside the repository owner's publication decision.
