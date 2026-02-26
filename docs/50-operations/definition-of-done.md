# Definition of Done (DoD)

This DoD defines minimum completion criteria for changes in this repo.
It prevents incomplete or unsafe implementations—especially for AI features.

---

## 1) Docs changes (docs/*)
Done means:
- content is readable (headings/sections, no broken formatting)
- links work
- changes align with ADRs and AIMS policies where relevant

---

## 2) Code changes (apps/*, packages/*)
Done means:
- builds successfully
- basic tests pass (unit/integration as available)
- no secrets committed
- tenant isolation respected (ADR-0001)
- logging/audit trail considered (ADR-0003)
- rollback plan stated (even if simple)

---

## 3) AI feature changes (user-facing)
Done means:
- transparency disclosures implemented (AI-assisted indicator)
- high-impact domains (Legal/Finance/HR):
  - show sources and effective dates (Legal)
  - include limitation statements
  - enforce human oversight and escalation path
- prompt injection risk considered (retrieved content treated as untrusted)
- prompt/model versioning updated and documented (ADR-0004)
- audit metadata captured (ADR-0003)

---

## 4) Data / DB changes
Done means:
- migrations are included and reversible (where feasible)
- backup/restore impact considered
- tenant scoping is verified for new tables/queries

---

## 5) Pilot readiness checklist (staging)
Done means:
- environment variables documented (docs/50-operations/environments.md)
- runbook updated if operational behavior changes
- SLO impact considered (docs/50-operations/sla-slo.md)
