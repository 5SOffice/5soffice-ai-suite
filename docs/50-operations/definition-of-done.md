# Definition of Done (DoD)

This DoD defines minimum completion criteria for changes in this repo.
It helps prevent incomplete or unsafe implementations—especially for AI features.

---

## 1) Docs changes (`docs/*`)

Done means:

- Markdown is readable (proper headings/sections, no broken formatting)
- Links work (no 404 paths)
- Content aligns with ADRs and AIMS policies where relevant
- README documentation index updated when new key docs are added (when applicable)

---

## 2) Code changes (`apps/*`, `packages/*`)

Done means:

- Build succeeds
- Basic tests pass (unit/integration as available)
- No secrets committed (keys/tokens/passwords)
- Tenant isolation is respected (ADR-0001)
- Logging/audit trail fields are considered (ADR-0003)
- Rollback plan is stated (even if simple)

---

## 3) AI feature changes (user-facing)

Done means:

- AI-assisted indicator is visible (transparency)
- High-impact domains (**Legal/Finance/HR**) enforce:
  - Sources + effective dates (Legal)
  - Limitation statement (Legal: “general guidance, not legal advice”)
  - Human oversight and escalation path (AIMS policy)
- Prompt injection risk considered:
  - Retrieved content treated as **untrusted input**
  - System policies cannot be overridden by document text
- Prompt/model versioning updated when prompts change (ADR-0004)
- Audit metadata captured for high-impact outputs (ADR-0003)

---

## 4) Data / DB changes

Done means:

- Migrations included (and reversible where feasible)
- Backup/restore impact considered
- New tables/queries are tenant-scoped and verified

---

## 5) Pilot readiness checklist (staging)

Done means:

- Environment variables documented (docs/50-operations/environments.md)
- Runbook updated if operational steps changed (docs/50-operations/runbooks.md)
- SLO impact considered (docs/50-operations/sla-slo.md)
