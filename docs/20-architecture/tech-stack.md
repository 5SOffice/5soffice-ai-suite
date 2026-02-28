# Tech Stack (Hybrid) — Initial Decision

This document defines the initial technology stack for **5SOffice AI Suite**.

## Decision: Hybrid

- **API/UI:** Node.js / TypeScript
- **Workers (crawl/OCR/batch):** Python

### Rationale

- **Node/TS** is fast for product UI, dashboard, auth, and integrations (good for pilot #8).
- **Python** is strong for data pipelines and OCR/document processing (critical for project #2).
- A hybrid split lets each part use the best tooling without forcing one language to do everything.

---

## 1) Runtime split

### API/UI (Node/TS)

Use for:
- Tenant portal + dashboard
- Authentication + RBAC
- Legal pilot UI + Q&A endpoints
- Alert configuration and subscription endpoints

Suggested options (choose during implementation):
- **Next.js** (app + API routes), or
- **NestJS/Fastify** backend + **Next.js** frontend

### Workers (Python)

Use for:
- Scheduled crawling / ingestion (legal sources)
- Indexing / embeddings jobs
- OCR and document processing pipelines
- Batch generation of digests/checklists

Suggested options (choose during implementation):
- **FastAPI** internal worker service + scheduler, or
- **Celery/RQ** with a queue (recommended as load grows)

---

## 2) Data & storage (baseline)

- **Database:** PostgreSQL
- **Vector search:** pgvector (inside PostgreSQL) for early stages
- **Queue/cache:** Redis (optional early, recommended as we scale)
- **Object storage:** S3-compatible (preferred) or local disk (temporary for early pilot)

---

## 3) AI integration (governance must-follow)

- LLM via API (provider configurable)
- RAG with tiered sources (ADR-0002)
- Logging and audit trail (ADR-0003)
- Prompt/model versioning (ADR-0004)

High-impact outputs (**Legal/Finance/HR**) must:
- Show **sources + effective dates** (Legal)
- Include **transparency disclosures**
- Enforce **human oversight + escalation path**

---

## 4) Deployment model (pilot)

Start simple for the pilot:
- Docker Compose (staging VPS)

Minimal services (expected):
- `web` (Node/TS API/UI)
- `db` (Postgres + pgvector)
- `worker` (Python)
- `redis` (optional; add when needed)
- `proxy` (Caddy/Nginx for TLS)

---

## 5) Evolution path (aligned with roadmap)

### Phase 4 — Legal pilot MVP (#8)
- `web` + `db` + minimal `worker` (crawl/index/alerts)

### Phase 6 — Platformization
- Shared packages/services
- Proper queueing and observability
- CI/CD and release process

### Phase 7+ — Suite expansion
- Expand worker pipelines for OCR and document automation (#2)
