# SLA / SLO (Pilot Baseline)

This document defines a lightweight service level objective (SLO) baseline for the pilot stage.
It is not a contractual SLA yet. It helps set expectations and guide operations.

---

## 1) Definitions
- **SLO**: Internal reliability target.
- **SLA**: External commitment (not applicable for early pilot unless explicitly agreed).

---

## 2) Pilot-stage scope
Applies to:
- #8 Legal Compliance Tracker & Advisor (pilot)
- Core platform services (auth, tenant context, dashboard, alerts)

Does not apply to:
- Third-party provider outages (LLM provider, email, Zalo, hosting), but we track them.

---

## 3) Proposed pilot SLO targets (initial)

### Availability
- SLO: **99.0% monthly** for pilot web/API availability
- Exclusions: planned maintenance windows (announced)

### Latency (API)
- SLO: 95th percentile response time:
  - General requests: < 2.0s
  - AI responses (RAG + LLM): < 8–15s (depends on provider)

### Alert delivery (Legal updates)
- SLO: 95% of scheduled alerts are delivered within the defined window
- Window definition:
  - Daily digest: delivered within 2 hours of scheduled run time
  - Critical alerts (optional later): within 30 minutes

### Data integrity
- SLO: **0 tolerance** for cross-tenant data leakage
- Any suspected leakage is a critical incident.

---

## 4) Support & response targets (pilot)
- Acknowledgement of pilot incidents: within 1 business day
- Critical incidents (data leak suspected): immediate escalation to project lead

---

## 5) Maintenance windows (pilot)
- Preferred maintenance window: off-peak hours (local time Asia/Ho_Chi_Minh)
- Maintenance communication: internal note or tenant notice (if needed)

---

## 6) Monitoring signals (minimum)
Track monthly:
- uptime
- error rate
- DB health (disk/CPU/memory)
- worker backlog
- alert success/failure rate
- high-impact AI errors (see AIMS monitoring)

---

## 7) Revision
This SLO baseline will be revised after:
- pilot rollout learnings
- increased tenant count
- transition to production-grade operations
