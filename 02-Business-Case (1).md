# Business Case

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> Produced during **Stage 1 — Discovery & Business Case**, alongside the [Project Charter](./01-Project-Charter.md). See the [README](./README.md) for full project context.

---

## The Problem, in Numbers

Solenne Financial Group's IT Change Advisory Board (CAB) reviews roughly **600 production changes a month** across core banking, payments, and customer-facing digital systems.

- **Baseline change-failure rate: 9.5%** — changes that were rolled back, triggered a P1/P2 incident, or required an emergency fix.
- **Estimated annual cost: $5.5M** — remediation effort, customer impact, and incident-driven regulatory reporting.
- **CAB itself had become a bottleneck:** reviewer attention was distributed roughly evenly across changes regardless of actual risk, meaning routine changes waited unnecessarily while genuinely risky changes didn't get meaningfully more scrutiny than routine ones.

This baseline wasn't assumed — it was established by pulling three years of change and incident data from ServiceNow specifically to quantify failure rate, cost per failed change, and CAB review dwell time, replacing anecdote with a measured starting point.

## Why Now

The trigger for this project wasn't a vendor pitch — it was the CAB Chair's frustration that there was no consistent way to distinguish low-risk from high-risk changes under time pressure. Confirming that this was actually true with data, before proposing any solution, was the first step in building a credible business case.

## The Proposed Solution

**ChangeGuard AI** is a predictive machine learning model that scores incoming change requests for risk and surfaces the specific factors driving that score, so CAB can focus its limited review time where it matters most.

It is built and governed as a **classical predictive ML system**, not a generative one — a deliberate choice given the regulatory environment, where model risk governance, explainability, and fairness testing carry as much weight as raw predictive accuracy.

## Financial Case

| | |
|---|---|
| **One-time build & validation cost** | $210,000 |
| **Ongoing run cost** | ~$2,400/month (model hosting, monitoring, retraining pipeline) |
| **Targeted change-failure rate** | 7.0% (down from 9.5% baseline) |
| **Projected annualized savings** | ~$1.5M target |
| **Actual savings run-rate at 6 months post-launch** | ~$1.3M, ramping as full-domain rollout annualizes |

### A Note on How the ROI Was Framed

Finance initially wanted ROI calculated purely on reduced CAB headcount. That framing was deliberately redirected toward **reduced failed-change cost and faster review of low-risk changes** instead. This wasn't just a financial-modeling choice — a headcount-reduction framing would have made the project look threatening to the very board whose adoption it depended on, and would likely have invited internal resistance that a cost-avoidance framing did not.

## Key Assumptions

- Three years of historical change and incident data is sufficient to train a reliable model.
- Model Risk Validation will approve a tree-based, explainable model architecture (rather than requiring or preferring a higher-accuracy but less explainable approach).
- CAB will adopt the score as a genuine input to their review rather than ignoring it — or, in the opposite failure mode, over-trusting it without exercising independent judgment.

*(Both failure modes named in this last assumption were later confirmed as real risks during deployment — see Stage 6 in the [README](./README.md#the-seven-stage-lifecycle).)*

## Key Constraints

- No use of submitting-team identity as a direct model feature.
- Independent model validation required before production use.
- The model must remain advisory only in v1 — it cannot approve or block a change itself.

## Risks Identified at the Business Case Stage

- **Fairness risk:** An early data pull suggested change failure correlated with which team submitted the change, not just the change's own characteristics. This was flagged immediately as a potential proxy for which teams own older, more fragile systems — not a genuine signal about how a team works — and carried forward as an explicit requirement for the requirements and evaluation stages rather than resolved here.
- **Regulatory/governance risk:** The original ask was for the model to auto-approve low-risk changes. Model Risk Validation and Compliance confirmed this was not viable for a v1 without a far more extensive audit trail and a longer regulatory review cycle. The business case was reframed around an advisory-only model before any budget was committed.

## Approval

This business case was walked through formal sponsor and Model Risk Validation approval gates before any budget was committed, and was **approved by the Head of IT Risk & Change Management**, with the explicit condition that Model Risk Validation and Compliance sign-off would be required before production deployment — a condition tracked through to the evaluation stage of the project.

---

*Document produced as part of Stage 1 — Discovery & Business Case. Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
