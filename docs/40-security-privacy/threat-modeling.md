# Threat Modeling (Pilot)

This document outlines key threat scenarios and mitigations for the pilot stage.
Focus: multi-tenant isolation, RAG integrity, AI output safety, and basic infrastructure risks.

---

## 1) Threat model scope
In scope:
- Tenant isolation across app/data/AI layers
- Legal compliance module (#8) RAG pipeline
- Basic auth and admin functions
- Logging/audit trail

Out of scope (early pilot):
- Advanced DDoS protection
- Full security audit
- Complex insider threat modeling

---

## 2) Top threats (pilot)

### T1 — Cross-tenant data leakage
Scenario:
- A query or retrieval returns data from another tenant

Impact:
- Critical (confidentiality breach)

Mitigations:
- Enforce tenant_id middleware on every request (ADR-0001)
- Tenant-scoped DB queries and RAG indexes by default (ADR-0002)
- Add automated isolation tests (unit/integration)
- Incident response runbook for suspected leakage

---

### T2 — Prompt injection via retrieved content
Scenario:
- Retrieved documents contain malicious instructions that override system behavior

Impact:
- High (incorrect outputs, data exposure attempts)

Mitigations:
- Treat retrieved content as untrusted input
- System prompt and policies must not be overridden
- Strip or ignore instruction-like patterns in documents where possible
- Keep Tier-1 sources authoritative and validated

---

### T3 — Hallucination in high-impact domain (Legal/Finance/HR)
Scenario:
- AI generates incorrect legal interpretation or checklist

Impact:
- High (wrong actions, compliance risk)

Mitigations:
- Require citations + effective dates for legal outputs
- Confidence/uncertainty handling
- Human oversight and escalation path (AIMS policy)
- Track and review critical errors (monitoring loop)

---

### T4 — Source integrity / poisoning
Scenario:
- Ingestion pulls incorrect or tampered content, or outdated versions are used

Impact:
- High (wrong legal guidance)

Mitigations:
- Maintain a source trust registry (Tier 1 allowlist)
- Snapshot and version source documents
- Validate freshness and effective dates
- Monitor ingestion failures and anomalies

---

### T5 — Secret leakage
Scenario:
- API keys or tokens committed to Git or exposed in logs

Impact:
- High (account compromise, billing abuse)

Mitigations:
- Secrets never in Git
- Use env vars / secret manager
- Redact secrets in logs
- Rotate keys on exposure

---

### T6 — Unauthorized admin access
Scenario:
- Compromised admin account leads to tenant data exposure

Impact:
- High/Critical

Mitigations:
- Strong auth controls for admin
- Least privilege + RBAC
- Audit admin actions (ADR-0003)
- Restrict admin endpoints and access

---

## 3) Security testing (pilot-grade)
Minimum:
- tenant isolation tests
- auth/role tests
- injection resilience checks (prompt/RAG)
- basic dependency scanning (optional early, recommended later)

---

## 4) Incident severity (pilot)
- Critical: suspected data leakage, unauthorized access
- High: high-impact hallucination causing material risk, secret exposure
- Medium/Low: availability or performance issues

Response steps:
- contain → investigate → remediate → document → improve controls
