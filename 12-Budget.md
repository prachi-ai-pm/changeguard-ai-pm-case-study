# Budget

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> Source figures from the Stage 1 Project Charter and Business Case, broken out by category and tracked against the Stage 7 monitoring finding on cost-per-score drift. See the [README](./README.md) for full project context and the [Business Case](./02-Business-Case.md) for the original financial framing.

---

## Budget Summary

| | |
|---|---|
| **One-time build & validation cost** | $210,000 |
| **Ongoing run cost** | ~$2,400/month (model hosting, monitoring, retraining pipeline) |
| **Approved by** | Head of IT Risk & Change Management (Sponsor), with Model Risk Validation and Compliance sign-off conditions |
| **Targeted annualized savings** | ~$1.5M |
| **Actual savings run-rate at 6 months post-launch** | ~$1.3M, ramping as full-domain rollout annualizes |

---

## One-Time Build & Validation Cost Breakdown

| Category | Estimated Cost | Notes |
|---|---|---|
| Data science & ML engineering effort (2 data scientists, 9 sprints) | $95,000 | Largest single line — model development, feature engineering, SHAP integration |
| Data engineering effort (1 data engineer, including Stage 2 audit & SME relabeling support) | $38,000 | Includes the 4-week SME relabeling effort and data pipeline build |
| Backend / integration engineering (ServiceNow workflow integration) | $32,000 | In-workflow display, divergence-rationale logging, audit trail |
| QA & UAT coordination | $14,000 | Test planning, UAT facilitation, acceptance criteria validation |
| Model Risk Validation & Independent Model Validation review cycles | $18,000 | Documentation package preparation, expanded bias-testing scope addition (change request) |
| PM effort (discovery through launch) | $13,000 | Allocated portion of PM time across all 18 weeks |
| **Total one-time cost** | **$210,000** | |

## Ongoing Monthly Run Cost Breakdown

| Category | Estimated Monthly Cost | Notes |
|---|---|---|
| Model hosting / inference compute | ~$900 | Scales with change volume |
| Monitoring & disparity-tracking infrastructure | ~$700 | Supports quarterly fairness monitoring and live calibration tracking |
| Retraining pipeline (compute + data refresh) | ~$600 | Not a full retrain monthly — incremental refresh and drift-check infrastructure |
| Logging & audit-trail storage | ~$200 | Supports auditability requirement (every score, input set, and decision retained) |
| **Total monthly run cost** | **~$2,400** | |

---

## Financial Case

| | |
|---|---|
| **Baseline annual cost of status quo** | ~$5.5M (failed-change remediation, customer impact, incident-driven regulatory reporting) |
| **Targeted change-failure rate** | 7.0% (down from 9.5% baseline) |
| **Projected annualized savings** | ~$1.5M |
| **Payback period on one-time build cost** | Under 2 months at projected savings run-rate |
| **Actual savings run-rate, 6 months post-launch** | ~$1.3M, ramping as full-domain rollout annualizes |

### How ROI Was Framed

Finance initially wanted ROI calculated purely on reduced CAB headcount. That framing was deliberately redirected toward **reduced failed-change cost and faster review of low-risk changes** instead — a framing the CAB Chair could support, rather than one that would have made the project look like a headcount-reduction initiative and invited internal resistance from the very board whose adoption it depended on. See [Business Case](./02-Business-Case.md) for the full discussion.

---

## Budget Variance Tracking (Post-Launch)

A cost-per-score monitoring item was established in Stage 7 specifically because run cost was not assumed to hold steady once change volume grew beyond the original forecast.

| Finding | Stage | Response |
|---|---|---|
| Cost-per-score began rising faster than the Stage 1 forecast as change volume grew | 7 — Post-Launch Governance | Tracked monthly against the original forecast rather than waiting for the annual budget review; a 10% variance threshold was set as the trigger for action |
| Variance exceeded the 10% threshold | 7 | Worked with engineering on a batching optimization for inference calls, closing the gap before it became a larger issue or required a budget escalation |

This is tracked as risk **RR-10** in the [Risk Register](./08-Risk-Register.md) and remains an ongoing monthly monitoring item.

---

## Notes on Budget Governance

- **The budget was walked through a formal approval gate before any spend was committed**, not authorized informally — consistent with how every other scope and cost decision on this project was handled.
- **The Sprint 7–8 scope addition (expanded bias testing) was absorbed within the original $210,000 build budget** rather than requiring incremental funding, because it was scoped and approved as a formal change request against existing capacity rather than new spend — see [RAID Log](./07-RAID-Log.md) item C-01.
- **Run cost, not just build cost, was treated as a governed line item.** Many AI/ML projects budget carefully for build and then lose visibility into run cost once the project is "done." Monthly tracking against forecast was deliberately built into Stage 7 governance rather than left to surface only at an annual review.

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
