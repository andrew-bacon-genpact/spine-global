# spine-global

The Spine's governed content mirror for AI Maestro.

## What this repo is

Maestro's agents reason over a body of client knowledge — policies, contracts,
playbooks, and learned plans. This repository is the **governed mirror** of that
knowledge: the version-controlled copy the Spine reads from at runtime.

The authoritative sources live upstream — the client's SharePoint policy library,
their contract repositories, their vendor master. This repo does not replace those
systems. It mirrors the slices Maestro needs, so that what an agent knows is always
a reviewed, attributable artifact rather than a live query against a system nobody
can audit after the fact.

## The one rule

**Nothing enters or changes except through a reviewed pull request.**

There is no other write path. Branch protection on `main` requires an approving
review, so every change to what the agents know is a diff a human signed off on.

## Provenance

Every content file carries frontmatter recording where it came from and when:

```yaml
source_store:    # the upstream system of record
source_version:  # the upstream version this mirrors
ingested:        # the date this copy was taken
owner:           # the analyst accountable for it
```

If a file has no provenance, it does not belong here.

## Layout

- `tenants/<tenant>/` — client-scoped content, isolated per tenant.
  - `policies/` — the client's operating policies, mirrored from their governed library.
  - `contracts/` — vendor and service agreements grounding contract-aware checks.
  - `plans/<case_type>/` — learned resolution plans, one folder per case type.
- `global/` — content shared across all tenants.
  - `playbooks/` — cross-tenant operating playbooks.

## Learned plans

When an operator resolves an exception in a way the system should generalize, the
**Planner agent** drafts a candidate plan and opens it here as a pull request,
authored under its own account and citing the case it learned from. An analyst
reviews it like any other change. A plan routes no live cases until that PR is
approved and the plan is activated.

This is the point of the repo: the agents get smarter only through changes a person
reviewed.
