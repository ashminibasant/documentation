---
title: Repository License Authority Remediation Record
description: Completed audit record for explicit per-document license authority across the public documentation repository.
published: true
date: 2026-07-17T00:00:00.000Z
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
| Audit Date | 2026-07-17 |
| Markdown Files Audited | 130 |
| Explicit Per-Document Authorities | 130 |
| Package-Only Markdown Authorities | 0 |
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

## License Disposition

| Document Class | Files Updated | License |
| --- | ---: | --- |
| Public legal and policy texts | 9 | `CC BY 4.0` |
| Reusable public license template | 1 | `CC BY 4.0` |
| Root and governance documentation | 2 | `CC BY-NC 4.0` |
| Historical and reference research documents | 31 | `CC BY-NC 4.0` |

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
