# Product Backlog

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> Translated from the PRD requirements (Stage 2) and Architecture Decision Record (Stage 3) into an estimable, sprint-ready backlog. See the [README](./README.md) for full project context, the [Sprint Plan](./09-Sprint-Plan.md) for how this backlog was actually delivered, and [User Stories](./11-User-Stories.md) for the detailed story-level breakdown of the top items.

---

## Epics

| Epic ID | Epic | Linked Requirement / Decision |
|---|---|---|
| E1 | Reliable Training Data Foundation | Data Readiness Assessment (Stage 2) |
| E2 | Risk Scoring Model | Functional requirement: risk score per change (Stage 2 PRD) |
| E3 | Explainability & Feature Attribution | Functional requirement: explainability (Stage 2 PRD); ADR Stage 3 |
| E4 | Fairness & Proxy-Discrimination Prevention | Functional requirement: no proxy discrimination (Stage 2 PRD); fairness risk (Stage 1) |
| E5 | CAB Workflow Integration & Display | ADR human-in-the-loop design (Stage 3) |
| E6 | Auditability & Logging | Functional requirement: auditability (Stage 2 PRD) |
| E7 | Validation & Governance Readiness | Model Risk Validation requirements (Stages 2, 3, 5) |
| E8 | Launch Readiness | UAT and go-live runbook (Stage 4 Sprint 9, Stage 6) |

---

## Backlog (Prioritized)

| ID | Epic | Item | Priority | Estimate (pts) | Sprint Delivered | Status |
|---|---|---|---|---|---|---|
| PB-01 | E1 | Audit ~21,000 historical change records for completeness and reliability | Must | 8 | Pre-Sprint (Stage 2) | Done |
| PB-02 | E1 | Run cross-functional workshop to agree a single failure taxonomy | Must | 5 | Pre-Sprint (Stage 2) | Done |
| PB-03 | E1 | SME-relabel ambiguous change-to-incident linkage sample | Must | 13 | Sprints 1–3 | Done |
| PB-04 | E1 | Backfill missing system metadata (age, criticality) for in-scope systems | Must | 5 | Sprints 1–3 | Done |
| PB-05 | E1 | Build feature pipeline v1 from cleaned dataset | Must | 8 | Sprints 1–3 | Done |
| PB-06 | E2 | Train and validate XGBoost baseline classification model | Must | 13 | Sprints 4–5 | Done |
| PB-07 | E2 | Produce Low / Medium / High risk classification for every submitted change | Must | 8 | Sprints 4–5 | Done |
| PB-08 | E2 | Add timing-related risk features (weekend/pre-holiday submission pattern) | Should | 5 | Sprint 6 | Done — added via mid-build re-prioritization |
| PB-09 | E3 | Integrate SHAP for per-prediction feature attribution | Must | 8 | Sprints 4–5 | Done |
| PB-10 | E3 | Surface top 3 contributing factors in plain language | Must | 5 | Sprints 4–5 | Done |
| PB-11 | E4 | Exclude submitting-team identity as a direct model feature | Must | 3 | Sprints 1–3 | Done |
| PB-12 | E4 | Run bias/disparity testing across business units | Must | 8 | Sprints 7–8 | Done |
| PB-13 | E4 | Expand bias testing scope per Model Risk Validation request | Must | 8 | Sprints 7–8 | Done — delivered via formal change request |
| PB-14 | E4 | Add system age / technical-debt indicators as explicit features (fairness remediation) | Must | 5 | Stage 5 (post-Sprint 9, pre-launch) | Done |
| PB-15 | E5 | Display top 3 contributing factors by default, not behind a click | Must | 5 | Sprints 4–5 | Done |
| PB-16 | E5 | Surface score and explanation directly inside existing ServiceNow CAB workflow | Must | 13 | Sprints 4–5 | Done |
| PB-17 | E5 | Build divergence-rationale field for reviewer overrides | Must | 5 | Sprints 4–5 | Done |
| PB-18 | E6 | Log every score, its inputs, and the reviewer's final decision | Must | 8 | Sprints 4–5 | Done |
| PB-19 | E6 | Ensure score generated within 1 hour of change submission (latency requirement) | Must | 5 | Sprints 4–5 | Done |
| PB-20 | E7 | Produce documentation package for Model Risk Validation review | Must | 8 | Sprints 7–8 | Done |
| PB-21 | E7 | Remediate documentation gap on Stage 2 relabeling methodology | Must | 3 | Stage 5 (post-build) | Done |
| PB-22 | E8 | Run CAB User Acceptance Testing on score + explanation usefulness | Must | 8 | Sprint 9 | Done |
| PB-23 | E8 | Draft go-live runbook with rollback triggers and decision ownership | Must | 5 | Sprint 9 | Done |
| PB-24 | E5 | Add check for unusually fragmented related change submissions (anti-gaming) | Should | 5 | Post-launch (Stage 7) | Done — added post-launch in response to monitoring finding |
| PB-25 | E1 | Extend scoring to additional technology domains pending data readiness assessment | Could | 13 | Not yet scheduled | Backlog — Forward Roadmap |
| PB-26 | E2 | Explore feedback loop using CAB override rationale to periodically retrain model | Could | 13 | Not yet scheduled | Backlog — Forward Roadmap |
| PB-27 | E5 | Evaluate fast-tracking very-low-risk changes with lighter review | Won't (v1) | — | Not yet scheduled | Backlog — explicitly deferred pending longer production track record |

---

## Backlog by Priority (MoSCoW)

| Priority | Count | Notes |
|---|---|---|
| **Must** | 21 | Core v1 scope — required for launch and regulatory sign-off |
| **Should** | 2 | High-value additions identified during build/operation, not launch-blocking |
| **Could** | 2 | Forward roadmap items, explicitly deferred |
| **Won't (v1)** | 1 | Explicitly out of scope for v1, named in the Scope Statement |

---

## Notes on Backlog Evolution

- **PB-08, PB-13, and PB-24 were not in the original PRD.** Each entered the backlog through an explicit mechanism — mid-sprint re-prioritization (PB-08), a formal change request (PB-13), or a post-launch monitoring finding (PB-24) — consistent with how scope changes were handled throughout this project. None were absorbed silently.
- **PB-14 (fairness remediation) was a launch blocker, not a backlog nice-to-have.** It's listed here for completeness of the backlog record, but it was treated with the urgency of a defect, not a feature request — see the [Risk Register](./08-Risk-Register.md), RR-02.
- **PB-25 through PB-27 are intentionally unscheduled.** They reflect the Forward Roadmap captured in Stage 7 governance and are retained in the backlog rather than discarded, so they're visible for future scoping.

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
