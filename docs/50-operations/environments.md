# Environments (Local / Staging / Production)

This document defines environment conventions for 5SOffice AI Suite, including configuration, secrets, and deployment expectations.

---

## 1) Environment overview

### Local (Development)
Purpose:
- fast iteration and testing

Characteristics:
- runs via Docker Compose
- uses local or dev credentials
- minimal monitoring

### Staging (Pilot)
Purpose:
- stable demo environment for pilot tenants
- pre-production validation

Characteristics:
- hosted on VPS
- real domain + TLS
- restricted access for admin functions
- backups enabled

### Production (Later)
Purpose:
- reliable service for multiple tenants

Characteristics:
- split app/db/worker (recommended)
- observability (metrics/logs/tracing)
- stricter access controls and rotation policies

---

## 2) Configuration principles

- Configuration is provided via environment variables.
- Secrets must never be committed to Git.
- All requests must resolve tenant context (tenant_id) per ADR-0001.
- High-impact modules (Legal/Finance/HR) must enforce transparency and human oversight.

---

## 3) Required environment variables (baseline)

### Core
- `APP_ENV` = `local` | `staging` | `production`
- `APP_BASE_URL` (e.g., https://pilot.5soffice.com.vn)
- `PORT`

### Database
- `DATABASE_URL` (Postgres)
- `DB_SSL` (true/false, staging/prod typically true)

### Authentication / Session
- `AUTH_SECRET` (session/JWT secret)
- `COOKIE_SECURE` (true in staging/prod)
- `ALLOWED_ORIGINS` (CORS allowlist)

### AI / LLM Provider
- `LLM_PROVIDER` (e.g., openai/xai/other)
- `LLM_API_KEY`
- `LLM_MODEL_DEFAULT`
- `LLM_MODEL_HIGH_IMPACT` (recommended separate selection for Legal/Finance/HR)

### RAG / Knowledge
- `RAG_INDEX_STRATEGY` (e.g., pgvector)
- `RAG_GLOBAL_CORPUS_ENABLED` (true/false)
- `RAG_TENANT_INDEX_ENABLED` (true/false)

### Logging / Audit (ADR-0003)
- `LOG_LEVEL`
- `AUDIT_LOG_ENABLED` (true/false)
- `AUDIT_REDACTION_ENABLED` (true/false)
- `AUDIT_RETENTION_DAYS`

### Background jobs
- `WORKER_ENABLED` (true/false)
- `JOB_SCHEDULE_TIMEZONE` (Asia/Ho_Chi_Minh)
- `CRAWL_ENABLED` (true/false)

### Notifications (email/Zalo)
- `EMAIL_PROVIDER`
- `EMAIL_API_KEY`
- `ZALO_OA_ENABLED` (true/false)
- `ZALO_OA_ACCESS_TOKEN` (if applicable)

### Storage
- `STORAGE_PROVIDER` (local/s3)
- `STORAGE_BUCKET`
- `STORAGE_ACCESS_KEY`
- `STORAGE_SECRET_KEY`
- `STORAGE_REGION`
- `STORAGE_ENDPOINT` (if S3-compatible)

---

## 4) Environment-specific expectations

### Local
- `COOKIE_SECURE=false`
- use dev keys where possible
- test tenant isolation using seeded tenants

### Staging
- TLS enabled (Caddy/Nginx)
- restricted admin access
- daily DB backups enabled
- basic monitoring enabled

### Production (later)
- split infra recommended
- automated deployments
- secrets rotation policy
- stronger monitoring and incident response

---

## 5) Do-not-do list
- Do not commit `.env` files with secrets
- Do not disable tenant isolation checks
- Do not provide legal/financial “final decisions” without required disclosures and human oversight
