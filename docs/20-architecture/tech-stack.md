# Tech Stack (Hybrid) — Initial Decision

This document defines the initial technology stack for 5SOffice AI Suite.

Decision: **Hybrid**
- **API/UI**: Node.js / TypeScript
- **Workers (crawl/OCR/batch)**: Python

Rationale:
- Node/TS is fast for product UI, dashboard, auth, and integration work (pilot #8).
- Python is strong for document/OCR and data pipelines (project #2).
- Separation helps scale without forcing one language to do everything.

---

## 1) Runtime split

### API/UI (Node/TS)
Use for:
- tenant portal + dashboard
- authentication/RBAC
- Legal pilot UI + Q&A endpoints
- alert configuration endpoints

Suggested frameworks (choose during implementation):
- Next.js (app + API routes) OR
- NestJS/Fastify (separate backend) + Next.js frontend

### Workers (Python)
Use for:
- scheduled crawling / ingestion
- indexing / embeddings jobs
- OCR and document processing pipelines
- batch generation of digests/checklists

Suggested frameworks (choose during implementation):
- FastAPI (internal service) + scheduler OR
- Celery/RQ (worker queue)

---

## 2) Data & storage (baseline)
- Database: Postgres
- Vector search: pgvector (inside Postgres) for early stages
- Queue/cache (optional early, recommended as we grow): Redis
- Object storage: S3-compatible (preferred) or local disk for early pilot

---

## 3) AI integration
- LLM via API (provider configurable)
- RAG with tiered sources (ADR-0002)
- Logging and audit trail (ADR-0003)
- Prompt/model versioning (ADR-0004)

High-impact outputs (Legal/Finance/HR) must:
- show sources + effective dates (Legal)
- enforce transparency disclosures
- enforce human oversight / escalation

---

## 4) Deployment model (pilot)
Start simple for pilot:
- Docker Compose (staging VPS)
Services (expected):
- `web` (Node/TS API/UI)
- `db` (Postgres + pgvector)
- `worker` (Python)
- `redis` (optional; add when queue needed)
- `proxy` (Caddy/Nginx for TLS)

---

## 5) Evolution path (aligned with roadmap)
Phase 4 (Legal pilot MVP):
- `web` + `db` + minimal `worker` (crawl/index/alerts)

Phase 6 (Platformization):
- shared packages/services
- proper queueing and observability
- stronger CI/CD and release process

Phase 7+ (Suite expansion):
- expand worker pipelines for OCR and automation (#2)
