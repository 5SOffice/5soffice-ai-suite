# Security Baseline (Pilot)

This document defines minimum security controls for the pilot stage.
It supports multi-tenant isolation and AI governance expectations.

---

## 1) Account and access controls
- Enforce strong authentication for platform admin accounts
- Restrict admin access to a minimal set of users
- Use least privilege for roles (RBAC)
- Disable unused accounts promptly

---

## 2) Infrastructure hardening (VPS)
- SSH key-only login; disable password login
- Firewall: allow only required ports (80/443, restricted SSH)
- Keep OS packages updated
- Separate environments (local/staging/prod) where applicable

---

## 3) Secrets management
- Never commit secrets to Git
- Store secrets via environment variables or secret manager
- Rotate keys if exposure is suspected
- Separate keys per environment

---

## 4) Data protection & tenant isolation
- Enforce tenant context for every request (ADR-0001)
- Ensure DB queries are tenant-scoped
- Ensure RAG retrieval indexes are tenant-scoped by default (ADR-0002)
- Prevent cross-tenant content in AI outputs (hard requirement)

---

## 5) AI-specific security (RAG + prompt risks)
- Use Tier-1 authoritative sources for legal/regulatory outputs
- Defend against prompt injection:
  - treat retrieved content as untrusted input
  - prevent “instructions” in documents from overriding system policies
- For high-impact outputs:
  - show sources and effective dates
  - enforce human oversight (see AIMS policies)

---

## 6) Logging and audit
- Capture audit metadata per ADR-0003:
  - tenant_id, user role, timestamp, model/prompt version, sources
- Restrict access to audit logs
- Minimize sensitive content in logs (redaction where appropriate)

---

## 7) Backups and recovery
- Daily DB backups (minimum)
- Off-machine storage preferred
- Periodic restore test in staging
- Document retention and deletion policies (to be defined)

---

## 8) Vulnerability and incident handling (pilot)
- Track security issues in GitHub Issues (private details via secure channel if needed)
- Critical incident definition:
  - suspected data leakage
  - unauthorized access
  - high-impact AI error causing material risk
- Response:
  - contain → investigate → remediate → document

---

## 9) Future enhancements (post-pilot)
- Automated security scans in CI
- WAF and rate limiting
- Secrets manager integration
- Expanded privacy baseline and DPIA-style assessments (where applicable)
