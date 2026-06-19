---
doc_ref: MAESTRO-PB-001
title: Exception triage playbook
version: 3
source_store: Maestro operations handbook
source_version: "3.2"
ingested: 2025-04-02
owner: marcus.okafor
---

# Exception triage playbook

A shared playbook for how any case type enters the queue, gets assigned, and is
worked. Tenant plans specialize this; nothing here is tenant-specific.

## 1. Gates

Every case passes four gates before it can resolve automatically:

1. **Intake** — the event is parsed and its references extracted.
2. **Signature match** — the case is compared against known plan signatures.
3. **Plan check** — a matched plan's steps are validated against the case file shape.
4. **Disposition** — the plan runs, or the case escalates to a human.

A case that fails any gate escalates rather than guesses.

## 2. Assignment

An escalated case is routed to the operator whose skills and current load best fit
it. Assignment records why the case reached that operator, so the handoff carries
context rather than just a ticket.

## 3. Working the case

The operator sees the full context package the agent assembled, the agent's
reasoning, and the specific question that needs a human. The operator's resolution
and rationale are recorded and become provenance for any plan learned from the case.

## 4. After resolution

Where a resolution generalizes, the Planner agent drafts a candidate plan for review.
Where the operator flagged a missing or stale source, a flag is routed to the
accountable analyst.
