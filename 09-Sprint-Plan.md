# Sprint Plan

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> Covers **Stage 4 — Build & Delivery Coordination**: nine two-week sprints, run as hybrid Agile inside the project's broader Waterfall-style stage-gate structure. See the [README](./README.md) for full project context, the [WBS](./04-WBS.md) for how this maps to the overall work breakdown, and the [Product Backlog](./10-Product-Backlog.md) / [User Stories](./11-User-Stories.md) for what was actually being built sprint to sprint.

---

## Sprint Cadence

- **Sprint length:** 2 weeks
- **Total sprints:** 9 (Sprint 1 → Sprint 9)
- **Sprint 0 equivalent:** Stages 1–3 (Discovery, Requirements, Architecture) — treated as a Waterfall-style stage gate before iterative build began, consistent with the project's hybrid methodology
- **Ceremonies:** Sprint planning, weekly RAID log review with sponsor, backlog grooming, sprint review/demo, retrospective
- **PM cadence layered on top of sprints:** weekly status to sponsor; as-needed working sessions with Model Risk Validation at stage gates

---

## Sprint-by-Sprint Plan

### Sprints 1–3 — Data Foundation
**Goal:** Establish a reliable, modeled dataset before any model training begins.

| | |
|---|---|
| **Status** | Complete — extended by 1 sprint (originally planned as Sprints 1–2) |
| **Key Deliverables** | Cleaned dataset; SME-relabeled sample for ambiguous change-to-incident linkage; feature pipeline v1 |
| **Why it ran long** | Feature engineering surfaced more data quality issues than the Stage 2 audit alone had predicted. Rather than let the slip go uncommunicated, the sprint plan was re-baselined early and the sponsor was given the revised date along with the underlying reason. |
| **What filled the extra capacity** | Data science used the extra time productively to explore additional candidate features instead of idling. |

### Sprints 4–5 — Model Development
**Goal:** Stand up a working baseline model with explainability built in from the start, not bolted on later.

| | |
|---|---|
| **Status** | Complete |
| **Key Deliverables** | XGBoost baseline model; initial SHAP integration |
| **Notes** | Architecture (XGBoost over a deep learning ensemble) had already been decided and logged in the Stage 3 ADR — this sprint pair was about execution, not re-opening that decision. |

### Sprint 6 — Feature Enrichment
**Goal:** Incorporate a strong, generalizable signal discovered mid-build without losing sprint discipline.

| | |
|---|---|
| **Status** | Complete — reprioritized |
| **Key Deliverables** | Timing-related risk features (weekend / pre-holiday submission pattern) added to the feature set |
| **Why this got its own sprint** | The team found that changes submitted on weekends or immediately before public holidays had a substantially higher failure rate, independent of technical content. This was strong enough and stable enough across the dataset to justify re-prioritizing the backlog mid-stream rather than deferring it to a later release. |

### Sprints 7–8 — Validation Prep & Expanded Bias Testing
**Goal:** Prepare the documentation and fairness testing package Model Risk Validation would actually need to sign off.

| | |
|---|---|
| **Status** | Complete — scope added via formal change request |
| **Key Deliverables** | Documentation package for Model Risk Validation; expanded fairness tests across business units |
| **Scope change** | Model Risk Validation requested bias testing broader than what was originally scoped in the PRD. This was logged as a formal change request, scoped with data science, and approved by the sponsor for its schedule impact — not absorbed informally into existing sprint capacity. |

### Sprint 9 — UAT & Launch Readiness
**Goal:** Confirm the model and its explanations are actually usable by real CAB members, and that the team is ready to go live safely.

| | |
|---|---|
| **Status** | Complete |
| **Key Deliverables** | CAB User Acceptance Testing; go-live runbook drafted |
| **Notes** | UAT surfaced that several CAB members were defaulting to the headline Low/Medium/High label and skimming past the contributing factors — this didn't block launch readiness but was carried into the Stage 6 rollout plan as an active monitoring item. |

---

## Sprint Summary Table

| Sprint | Goal | Key Deliverables | Status |
|---|---|---|---|
| 1–3 | Data foundation | Cleaned dataset, SME-relabeled sample, feature pipeline v1 | Complete — extended by 1 sprint |
| 4–5 | Model development | XGBoost baseline model, initial SHAP integration | Complete |
| 6 | Feature enrichment | Timing-related risk features added after mid-build finding | Complete — reprioritized |
| 7–8 | Validation prep & expanded bias testing | Documentation package for Model Risk Validation, expanded fairness tests | Complete — scope added via change request |
| 9 | UAT & launch readiness | CAB UAT, go-live runbook drafted | Complete |

---

## How Sprint Discipline Was Maintained

- **Weekly RAID log reviews with the sponsor** ran across all nine sprints — risk and issue visibility didn't wait for sprint boundaries.
- **Every schedule or scope change was surfaced explicitly**, not absorbed silently: the Sprint 1–3 extension was re-baselined and explained; the Sprint 7–8 scope addition went through a formal change request.
- **A strong technical signal found mid-sprint (Sprint 6) was actioned immediately** rather than parked in a backlog for "later" — recognizing a good signal and acting on it was treated as more important than protecting the original sprint plan.

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
