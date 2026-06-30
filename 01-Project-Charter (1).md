# Project Charter

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> Produced during **Stage 1 — Discovery & Business Case**. See the [README](./README.md) for full project context, and [02-Business-Case.md](./02-Business-Case.md) / [03-Scope-Statement.md](./03-Scope-Statement.md) for the related artifacts from this same stage.

---

## Charter Summary

| Field | Detail |
|---|---|
| **Project Name** | ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning |
| **Sponsor** | Head of IT Risk & Change Management |
| **Project Manager** | Prachi Sharma |
| **Problem Statement** | A 9.5% change-failure rate across ~600 monthly production changes costs an estimated $5.5M annually, while CAB review time is distributed roughly evenly across changes regardless of actual risk, creating both unnecessary delay for routine changes and insufficient scrutiny for genuinely risky ones. |
| **Objectives** | 1) Provide CAB with an explainable risk score and contributing-factor breakdown for every change request.<br>2) Reduce overall change-failure rate.<br>3) Reduce average review dwell time for low-risk changes.<br>4) Operate strictly as an advisory input — the model does not approve or block changes. |
| **Success Metrics** | Change-failure rate reduction; recall ≥ 75% on historically failed changes; CAB-reported usefulness of explanations in UAT; no disparate risk flagging across business units once system-age effects are controlled for. |
| **In Scope (v1)** | Risk scoring and explanation for changes across core banking, payments, and customer-facing digital systems, surfaced inside the existing ServiceNow CAB workflow. |
| **Out of Scope (v1)** | Autonomous approval or rejection of any change; use of the model outside the CAB workflow; any feature derived directly from submitting-team identity. |
| **Budget** | $210,000 one-time build and validation cost; ~$2,400/month run cost (model hosting, monitoring, retraining pipeline). |
| **Key Assumptions** | Three years of historical change and incident data is sufficient to train a reliable model; Model Risk Validation will approve a tree-based, explainable model architecture; CAB will adopt the score as an input rather than ignoring it. |
| **Key Constraints** | No use of submitting-team identity as a direct model feature; independent model validation required before production use; model must remain advisory only in v1. |
| **Approval** | Approved by Head of IT Risk & Change Management, with conditions: Model Risk Validation and Compliance sign-off required before production deployment (tracked as a Stage 5 gate). |

---

## How This Charter Came Together

This project started with a CAB Chair's frustration, not a vendor pitch: the board was drowning in volume, routine changes were waiting days for a slot, and genuinely risky changes weren't getting meaningfully more scrutiny than routine ones — there simply wasn't a consistent way to tell them apart under time pressure.

The first job as PM was to confirm that was actually true with data, and to figure out — with Risk and Compliance at the table from day one — what kind of AI involvement in a CAB decision would even be acceptable in a regulated bank.

### PM Activities

- Ran discovery interviews with the CAB Chair, Head of IT Risk & Change Management, Site Reliability leads, and the Model Risk Validation function — deliberately bringing risk and compliance into the room at the discovery stage rather than after a solution was already chosen.
- Pulled three years of change and incident data from ServiceNow to quantify failure rate, cost per failed change, and CAB review dwell time — replacing anecdote with a measured baseline.
- Facilitated a scope-setting workshop to convert an initial ask for an "auto-approve low-risk changes" capability into something Model Risk would actually allow in a first release.
- Drafted this charter and the accompanying business case, and walked both through formal sponsor and Model Risk Validation approval gates before committing budget.

### Key Questions Asked

- **To the CAB Chair:** "Honestly, what fraction of changes get a real risk assessment today versus effectively a rubber stamp because the board is out of time?"
- **To Site Reliability:** "What does a failed change actually cost us once you include remediation effort, customer impact, and any regulatory incident reporting it triggers?"
- **To Model Risk Validation:** "What would a predictive model have to satisfy — explainability, documentation, independent validation — before it could influence a change approval decision in this environment?"
- **To Compliance:** "Is there any version of this where the model makes the approval decision itself, or are we only ever talking about an advisory input to a human reviewer?"

### Issues Faced & How They Were Resolved

- **The original ask — auto-approving low-risk changes — was a non-starter for Model Risk and Compliance.** Without an extensive audit trail, explainability framework, and a longer regulatory review cycle, autonomous decisioning wasn't viable for a v1. The business case was reframed around an advisory risk score that helps CAB prioritize its attention, with the human reviewer always making the final call — a scope change that actually made the project fundable faster, not slower.
- **An early data pull suggested change failure correlated with which team submitted the change, not just the change itself.** This was flagged as a fairness risk immediately rather than letting it quietly become a model feature: a team's changes might look riskier simply because they own older, more fragile systems, not because of how they work. This was carried forward as an explicit requirement for later requirements and testing stages, not resolved at this stage.
- **Finance initially wanted ROI calculated purely on reduced CAB headcount.** The business case was redirected toward reduced failed-change cost and faster review of low-risk changes instead — a framing the CAB Chair could support, versus one that would have made the project look like a headcount-reduction initiative and invited internal resistance.

---

*Document produced as part of Stage 1 — Discovery & Business Case. Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
