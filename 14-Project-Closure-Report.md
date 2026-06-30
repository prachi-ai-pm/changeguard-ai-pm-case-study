# Project Closure Report

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> Closes out the 18-week discovery-to-launch delivery and transitions the project into standing post-launch governance. See the [README](./README.md) for full project context and [15-Lessons-Learned.md](./15-Lessons-Learned.md) for the reflective companion to this report.

---

## Closure Summary

| | |
|---|---|
| **Project** | ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning |
| **Sponsor** | Head of IT Risk & Change Management |
| **Project Manager** | Prachi Sharma |
| **Delivery Duration** | 18 weeks, discovery through full rollout |
| **Closure Status** | **Delivered and transitioned to standing governance.** All charter objectives met or substantially met; project formally closed against the Stage 1 charter and handed to Post-Launch Governance ([Stage 7](./README.md#the-seven-stage-lifecycle)) as an ongoing operational function, not a one-time delivery. |
| **Closure Date Equivalent** | 6 months post full rollout, aligned to the first outcomes review cycle |

---

## Objectives vs. Outcomes

| Charter Objective | Target | Outcome at 6 Months | Met? |
|---|---|---|---|
| Provide CAB with an explainable risk score and contributing-factor breakdown for every change request | 100% coverage, per-prediction SHAP explanation | Delivered and in production across all in-scope domains | **Yes** |
| Reduce overall change-failure rate | 7.0% (from 9.5% baseline) | 7.4% | **Substantially met** |
| Reduce average review dwell time for low-risk changes | Reduced from 3.2 business days | 1.6 business days | **Yes — exceeded** |
| Operate strictly as an advisory input | Model never approves/blocks a change | Confirmed by architecture and audit log design; held throughout rollout | **Yes** |
| Recall on historically high-risk changes | ≥ 75% | 78% (Stage 5 evaluation), holding at 76% in production | **Yes** |
| CAB override-rationale compliance | ≥ 95% | 97%, after one mid-rollout correction | **Yes** |
| No material disparity across business units | No material disparity | ~1.1x, within normal variation (down from ~1.9x pre-fix) | **Yes** |
| Annualized cost savings | ~$1.5M target | ~$1.3M run-rate, ramping as full-domain rollout annualizes | **On track, not yet fully realized** |

**Overall assessment:** Six of eight charter objectives were fully met at the 6-month mark; the remaining two (failure-rate target and full savings run-rate) were substantially met and are tracking toward target as the full-domain rollout annualizes. No objective was missed outright, and no objective required a scope reduction to be declared complete.

---

## Budget Closure

| | |
|---|---|
| **Approved one-time budget** | $210,000 |
| **Actual one-time spend** | $210,000 (no overrun — the Sprint 7–8 scope addition was absorbed within the original budget via formal change request, not incremental funding) |
| **Approved ongoing run cost** | ~$2,400/month |
| **Actual run cost at closure** | Tracking within 10% variance threshold after a batching optimization implemented in Stage 7; see [12-Budget.md](./12-Budget.md) for full variance detail |
| **Payback period** | Under 2 months at projected savings run-rate |

Budget closed with no overrun against the Stage 1 charter, and with cost-per-score monitoring formally handed to Post-Launch Governance as an ongoing line item rather than closed out as a one-time concern.

---

## Scope Closure

All in-scope deliverables defined in the [Scope Statement](./03-Scope-Statement.md) were delivered:

- Risk scoring and explanation across core banking, payments, and customer-facing digital systems
- Native surfacing inside the existing ServiceNow CAB workflow
- Top-3 contributing factors visible by default
- Divergence-rationale logging
- Full audit trail (score, inputs, decision, rationale)
- Phased rollout across all three planned phases, each clearing its success gate

One scope addition was delivered through the formal change-request process (expanded bias testing, [RAID Log](./07-RAID-Log.md) item C-01) rather than informally absorbed, and is reflected in the final delivered scope.

No in-scope deliverable was cut, descoped, or deferred to reach closure. Three items were deliberately left as forward-roadmap candidates rather than v1 commitments — see [Forward Roadmap](#forward-roadmap-handed-to-governance) below.

---

## Governance Sign-Offs on Record

| Gate | Outcome |
|---|---|
| Charter & Business Case approval | Approved, with Model Risk Validation and Compliance sign-off conditions attached |
| PRD & Data Readiness sign-off | Approved |
| Architecture Decision Record review | Approved — XGBoost + SHAP selected over higher-accuracy alternative |
| Independent Model Validation sign-off | Approved, with binding ongoing conditions (quarterly disparity monitoring, annual revalidation) |
| Phase 1, 2, and 3 rollout gates | All three cleared |

No governance gate was bypassed or waived to reach closure. The Independent Model Validation sign-off's ongoing conditions are the formal basis for the [Governance & Monitoring Plan](#what-transfers-to-standing-governance) below.

---

## What Transfers to Standing Governance

This project does not have a hard "end" in the traditional sense — production use of ChangeGuard AI carries binding ongoing obligations as a condition of its Independent Model Validation sign-off. The following transfer from project delivery into standing operational governance, owned going forward by the roles indicated:

| KPI / Control | Cadence | Owner | Threshold / Trigger |
|---|---|---|---|
| Change-failure rate | Monthly | Head of IT Risk & Change Management | Investigate if no improvement trend after 2 consecutive months |
| Disparity monitoring across business units | Quarterly | Model Risk Validation | Escalate any disparity not explained by a legitimate, documented feature |
| Override-rationale compliance | Weekly, ongoing | CAB Chair | Refresher training if compliance falls below 95% |
| Metric-gaming / behavioral adaptation review | Quarterly | PM + Data Science Lead | Investigate any flagged-risk trend that diverges from actual incident trend |
| Full model revalidation | Annual, or on significant drift | Independent Model Validation | Mandatory condition of continued production use |
| Cost-per-score | Monthly | PM | Investigate at 10% variance from Stage 1 forecast |

## Forward Roadmap (Handed to Governance)

Three items were deliberately deferred rather than committed to v1, and are now the property of standing governance rather than the closed project:

- Extend scoring to additional technology domains not in the original in-scope list, pending their own data readiness assessment.
- Explore a feedback loop where CAB override rationale is used to periodically retrain and refine the model, with the same fairness testing rigor applied to every retrain.
- Evaluate, with Model Risk Validation, whether a future version could support fast-tracking very-low-risk changes with lighter review — explicitly deferred until a longer production track record exists.

---

## Outstanding Items at Closure

| Item | Status | Disposition |
|---|---|---|
| Full savings run-rate not yet at $1.5M target | On track, ramping | Tracked monthly by Post-Launch Governance, not treated as an open project risk |
| Metric-gaming check (fragmented submissions) | Implemented in response to a Stage 7 finding | Now a standing quarterly review item, not a one-time fix |
| Domain expansion, retraining feedback loop, fast-track evaluation | Deferred by design | Forward roadmap, owned by governance, not scheduled |

No outstanding item at closure represents an unresolved risk to current production use — each is either tracking to target or has been converted into a standing monitoring control.

---

## Formal Acknowledgment

This project is closed against its Stage 1 charter with all governance gates cleared, budget within approved bounds, and all in-scope deliverables shipped. Continued production use of ChangeGuard AI is governed by the standing controls listed above, owned by the Head of IT Risk & Change Management, Model Risk Validation, the CAB Chair, and the PM/Data Science Lead pairing — not as residual project work, but as the normal operating condition of a regulated decision-support model in production.

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
