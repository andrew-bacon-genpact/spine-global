---
doc_ref: ACME-AP-POL-114
title: Duplicate invoice handling policy
version: 2
effective: January 2025
source_store: Acme policy library (governed SharePoint)
ingested: 2025-01-14
owner: marcus.okafor
---

# Duplicate invoice handling policy

## 1. Scope

This policy governs the identification and disposition of suspected duplicate vendor invoices across Acme Inc. accounts-payable operations.

## 2. Definitions

**Invoice pair.** Two invoices from the same vendor identified by the detection
process as candidates for the same underlying obligation.

**Match fields.** The fields compared when assessing a pair: vendor identity,
purchase-order reference, line items, and total amount.

**Confidence.** The detection process's calibrated estimate, between 0 and 1, that
a pair represents the same obligation billed twice.

**Disposition.** The terminal decision on a pair: confirmed duplicate (blocked) or
rejected match (released to payment).

## 3. Detection

A nightly batch check compares newly received invoices against invoices received in
the preceding window. For each candidate pair it computes a confidence score from the
match fields and the interval between document dates. Pairs scoring above the
dismissal threshold in section 4.1 are carried forward for disposition; all others
are closed without action and retained for audit.

## 4. Disposition rules

### 4.1 Automatic disposition thresholds

- A pair with confidence **≤ 0.30** is dismissed automatically as a non-duplicate and
  released to the normal payment schedule.
- A pair with confidence **≥ 0.85** is treated as a confirmed duplicate and blocked
  from payment automatically under section 4.3.
- A pair with confidence **between 0.30 and 0.85** is routed for human review under
  section 4.2 before any payment disposition is applied.

### 4.2 Review threshold

Invoice pairs that match exactly on amount and purchase-order reference within a 45-day window must be routed for human review before any payment disposition is applied.

### 4.3 Disposition

A confirmed duplicate is blocked from payment and returned to the vendor. A rejected match is released to the normal payment schedule with the reviewer's rationale recorded on the case.

## 5. Records and audit

Every disposition — automatic or reviewed — is recorded on the case with its
confidence score, the match fields that drove it, and, where a human reviewed the
pair, the reviewer's identity and rationale. Records are retained for the statutory
audit period. Automatic dismissals under section 4.1 are sampled quarterly to confirm
the thresholds remain calibrated.
