---
doc_ref: MAESTRO-PB-004
title: Citation standards playbook
version: 1
source_store: Maestro operations handbook
source_version: "1.1"
ingested: 2025-04-02
owner: marcus.okafor
---

# Citation standards playbook

Every disposition an agent applies must be grounded in a citable source. This
playbook defines what a valid citation is.

## 1. What counts as a citation

A citation names a governed source and, where the source has structure, the specific
section relied on — for example, `ACME-AP-POL-114 v3 §4.4` or a contract by its
`doc_ref`. A citation to a source not in the mirror is not a valid citation.

## 2. Versioning

A citation pins the source version it relied on. When a source is updated, plans that
cited the prior version are re-validated against the new one before they continue to
route, so a policy change cannot silently invalidate a live plan.

## 3. In learned plans

A learned plan lists its citations explicitly. The reviewer checks that each cited
source exists in the mirror at the cited version and actually supports the step it
grounds. A plan whose citations do not resolve does not merge.

## 4. On the case

Every applied disposition records the citations it relied on, so an auditor can trace
any decision back to the governed source that authorized it.
