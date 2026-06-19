---
doc_ref: MAESTRO-PB-003
title: Source flagging playbook
version: 1
source_store: Maestro operations handbook
source_version: "1.5"
ingested: 2025-04-02
owner: marcus.okafor
---

# Source flagging playbook

How operators report that the knowledge an agent reasoned over was wrong, stale, or
missing — and how those reports close the loop back into the governed mirror.

## 1. Flag kinds

- **Stale** — a source exists in the mirror but is behind the client's current
  version.
- **Missing** — a source the case needed was not in the context package at all.
- **Wrong** — a source is present and current but contradicts ground truth.

## 2. Raising a flag

An operator raises a flag from the case with the kind, the document, and where the
correct source can be found. The flag is routed to the analyst who owns that content
area as an action item.

## 3. Closing a flag

The owning analyst resolves a flag by opening a pull request against the governed
mirror: ingesting the missing source, updating the stale one, or correcting the wrong
one. The flag closes when that PR merges, linking the case to the change it caused.

## 4. Signal

A high rate of flags on a source area is itself signal that a knowledge source is
missing or poorly maintained, and is surfaced to leadership rather than left implicit.
