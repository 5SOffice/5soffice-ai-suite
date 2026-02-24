# Runbooks (Pilot Operations)

This document provides operational runbooks for staging/pilot environments.
It is intentionally lightweight for early phases.

---

## 1) Day-0: Initial setup checklist

- [ ] Provision VPS (or split App/DB if needed)
- [ ] Configure firewall (allow 80/443, restrict SSH)
- [ ] Enable SSH key-only login; disable password login
- [ ] Install Docker + Docker Compose (or chosen runtime)
- [ ] Configure domain and TLS (Caddy/Nginx)
- [ ] Set environment variables (no secrets in Git)
- [ ] Start services
- [ ] Verify health endpoints
- [ ] Verify tenant isolation (ADR-0001)
- [ ] Enable daily DB backups

---

## 2) Start / Stop services

### Start
- Pull latest image/build
- Apply DB migrations
- Start app + worker + DB
- Verify:
  - API health
  - login/auth
  - a simple RAG query (if enabled)
  - job scheduler running

### Stop (graceful)
- Stop worker first (finish jobs)
- Stop app
- Stop DB last

---

## 3) Backup & Restore

### Backup (minimum daily)
- DB snapshot/dump
- Store backup off-machine if possible
- Record:
  - timestamp
  - environment (staging/prod)
  - DB version

### Restore (staging test recommended)
- Provision clean DB
- Restore from snapshot
- Run migrations if needed
- Validate:
  - authentication works
  - tenant data present and isolated
  - basic queries and alerts operate

---

## 4) Pilot monitoring (minimum)

Track:
- uptime / error rate
- DB health (disk, connections)
- worker queue/backlog
- alert delivery success rate
- high-impact AI output errors (critical incidents)

Minimum actions:
- set basic log retention
- define who receives alerts for failures (admin email)

---

## 5) Incident handling (pilot-grade)

### When an incident occurs
- [ ] Identify scope: tenant(s), module, time window
- [ ] Preserve logs (ADR-0003)
- [ ] If data leakage suspected:
  - disable affected endpoints
  - notify project lead immediately
  - start investigation and containment

### Common incidents
1) **LLM provider outage**
- fallback model/provider if available
- degrade gracefully (disable high-impact responses)

2) **Crawl/source ingestion failure**
- retry schedule
- alert admin
- keep previous index active

3) **High-impact hallucination (Legal/Finance/HR)**
- mark as critical
- log sources/prompt version
- improve guardrails / adjust prompt
- require escalation when uncertain

---

## 6) Release checklist (staging)

Before deploying a change:
- [ ] ADR impact assessed (0001–0004)
- [ ] Tenant isolation tests pass
- [ ] Transparency disclosures present (high impact)
- [ ] Human oversight enforced (Legal/Finance/HR)
- [ ] Audit logging schema intact
- [ ] Rollback plan exists

---

## 7) Access control and roles (pilot)

Minimum roles per tenant:
- Tenant Admin
- Tenant User

Platform roles (internal):
- Platform Admin (restricted)

Operational rule:
- Admin actions must be logged.
