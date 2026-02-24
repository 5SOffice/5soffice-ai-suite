# Infrastructure (Local / VPS) — Initial Sizing & Deployment Notes

This document provides infrastructure guidance for building and piloting 5SOffice AI Suite.
Priority order:
1) #8 AI Legal Compliance Tracker & Advisor (Pilot)
2) #2 AI Document Management & Automation (Next)

Assumption (recommended for early phases):
- LLM is consumed via API (no GPU required initially).

---

## 1) Environments

### Local (Development)
Goal: fast iteration for dev/testing.
Recommended:
- CPU: 6–8 cores (Apple Silicon M1/M2/M3 is fine)
- RAM: 16GB minimum (32GB recommended if OCR-heavy)
- Disk: 100GB+ free SSD
- Docker/Compose for local stack

### Staging (Pilot)
Goal: stable demo for internal use and small tenant pilot.
Recommended:
- Start with a single VPS (all-in-one)
- Upgrade/split later as load increases

### Production (Later)
Goal: reliability, isolation, observability, backups.
- Split App/DB/Workers
- Harden security controls and monitoring

---

## 2) Recommended Deployment Options

### Option A — All-in-one VPS (best for Legal pilot)
Use for: #8 pilot with ~5–20 tenants.

Suggested sizing:
- Minimum: 2 vCPU / 4GB RAM / 60–80GB SSD
- Recommended: 2–4 vCPU / 8GB RAM / 80–120GB SSD

Runs:
- Web/API
- Postgres (with pgvector)
- Background jobs (crawler/indexer/alerts)
- Reverse proxy (Caddy/Nginx)
- Basic monitoring/log shipping

Pros:
- Cheapest, simplest ops
Cons:
- DB and app share resources; scaling needs planning

### Option B — Split-lite (when pilot stabilizes)
Use for: more tenants or heavier indexing, improved reliability.

- VPS-1 (App/API): 2 vCPU / 4–8GB RAM
- VPS-2 (DB): 2 vCPU / 4–8GB RAM (SSD quality matters)

Optional:
- Object storage (S3-compatible) for documents and snapshots

Pros:
- Better stability and easier scaling
Cons:
- Slightly more ops overhead

### Option C — Add OCR Worker (for #2 Document Management)
Use for: OCR workloads and document pipelines.

- VPS-1 (App/API): 2–4 vCPU / 8GB RAM
- VPS-2 (DB): 2–4 vCPU / 8GB RAM
- VPS-3 (Worker/OCR): 4 vCPU / 16GB RAM (recommended)

Pros:
- OCR does not slow down the app
Cons:
- Extra cost + scheduling/queue management needed

---

## 3) Core Components (Pilot stack)

Recommended for early phases:
- Postgres + pgvector (primary DB + vector search)
- Background job runner (cron/queue) for:
  - ingest/crawl Tier-1 sources
  - indexing
  - sending alerts (email/Zalo)
- Object storage:
  - preferred: S3-compatible (cost-effective and scalable)
  - fallback: local disk + backups

Notes:
- Keep the stack minimal for the pilot to learn quickly.
- Scale by splitting roles (app/db/worker) only when needed.

---

## 4) Scaling Triggers

### Legal pilot (#8)
Consider upgrading 4GB → 8GB RAM when:
- DB latency increases
- vector index grows quickly
- background jobs compete with API traffic

### Document/OCR (#2)
Separate OCR worker when:
- PDFs are scanned or multi-page
- ingestion queue increases
- RAM usage spikes during conversions

---

## 5) Security Baseline (minimum for staging/pilot)

- SSH key-only access; disable password login
- Firewall: allow only 80/443 and restricted SSH
- Secrets stored in environment variables (never commit secrets)
- TLS enabled (Caddy/Nginx)
- Tenant isolation enforced (see ADR-0001)
- Backups:
  - daily DB snapshot (minimum)
  - store backups off-machine if possible

---

## 6) GPU Consideration (Only if running local models)

For early phases, prefer API-based LLM usage.
If running local models later:
- GPU 12GB VRAM: experimentation only
- GPU 24GB+ VRAM: practical usage
- GPU VPS typically not “cheap”; evaluate cost vs API.

---

## 7) Suggested Starting Point (Recommended)

Phase 4 MVP (Legal pilot):
- 1 VPS: 2–4 vCPU / 8GB RAM / 80–120GB SSD (all-in-one)

When starting #2 (Document/OCR):
- Add 1 worker VPS: 4 vCPU / 16GB RAM
- Consider object storage (S3-compatible) for documents

---

## 8) Operational Notes (Later)
As the suite expands:
- introduce observability (metrics/logs/tracing)
- define runbooks and SLOs
- automate deployments (CI/CD)
- formalize data retention policies per tenant
