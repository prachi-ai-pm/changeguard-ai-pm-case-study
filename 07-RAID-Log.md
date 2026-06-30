# RAID Log

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> RAID = Risks, Assumptions, Issues, Dependencies (and Decisions, tracked separately as Change items below). Entries span the full project lifecycle. See the [README](./README.md) for full project context and the [Risk Register](./08-Risk-Register.md) for a deeper treatment of risk items specifically.

---

## Risks

| ID | Description | Stage Raised | Owner | Status |
|---|---|---|---|---|
| R-01 | Change-to-incident data linkage unreliable enough to undermine label quality (~30% of historical records ambiguous or missing) | 1 / formalized in 2 | PM | Mitigated — SME relabeling completed over a 4-week effort in Stage 2 |
| R-02 | Submitting-team identity could act as a proxy for legacy-system risk, creating unfair flagging | 1 | Data Science Lead | Carried forward — confirmed and remediated in Stage 5 |
| R-03 | Initial model architecture choice would face a long, uncertain Model Risk Validation timeline | 3 | PM | Resolved — simpler, fully explainable XGBoost model chosen instead |
| R-04 | Third-party SaaS option could not provide per-prediction explainability required for validation | 3 | PM | Closed — option ruled out before further evaluation effort spent |
| R-05 | UI design (single risk badge, no default detail) could encourage reviewer rubber-stamping | 3 | PM + CAB Chair | Mitigated — top-3 contributing factors made default-visible |
| R-06 | CAB reviewers could either ignore the score (under-trust) or defer to it completely (over-trust) | 1 (assumption) → 6 (realized) | PM + CAB Chair | Actively monitored — over-trust pattern detected and corrected in pilot week one |
| R-07 | Score could be perceived or used as an input to individual performance evaluation | 6 | Sponsor | Closed — written sponsor commitment obtained and communicated before pilot expansion |
| R-08 | Visible scoring system could change submitter behavior in ways that distort monitoring signals (metric gaming) | 7 | PM + Data Science Lead | Identified and being actively monitored — quarterly behavioral review established |
| R-09 | Cost-per-score could rise faster than forecast as change volume grows | 7 | PM | Mitigated — monthly tracking against Stage 1 forecast with a 10% variance trigger |

## Assumptions

| ID | Description | Stage Raised | Owner | Status |
|---|---|---|---|---|
| A-01 | Three years of historical change and incident data is sufficient for reliable model training | 1 | PM | Validated, with caveats on linkage quality (see R-01) |
| A-02 | Model Risk Validation will approve a tree-based, explainable model architecture | 1 | PM | Validated in Stage 3 |
| A-03 | CAB will adopt the score as a genuine input rather than ignoring it | 1 | PM | Partially validated — required active correction of an over-trust pattern in Stage 6, then held |
| A-04 | System metadata (age, criticality) is consistently available for in-scope systems | 2 | Data Engineer | Partially false — gaps found and manually backfilled before modeling |

## Issues

| ID | Description | Stage Raised | Owner | Status |
|---|---|---|---|---|
| I-01 | Stakeholders did not agree on what counted as a change "failure" before this project started | 2 | PM | Resolved — cross-functional workshop produced a single signed-off taxonomy |
| I-02 | Model Risk Validation's initial explainability language ("must be explainable") was not precise enough to design against | 2 | PM | Resolved — concrete SHAP-based, per-prediction requirement written into PRD |
| I-03 | Feature engineering took longer than planned due to data quality issues | 4 | PM | Resolved — sprint plan re-baselined, sponsor informed with underlying reason |
| I-04 | UAT showed several CAB members defaulting to the Low/Medium/High label and skimming past contributing factors | 5 | PM | Resolved — built into Stage 6 rollout plan as an ongoing monitoring item |
| I-05 | Independent Model Validation flagged the Stage 2 relabeling methodology documentation as insufficiently detailed | 5 | PM + Data Science Lead | Resolved — methodology writeup clarified and resubmitted |
| I-06 | A small number of pilot-week reviewers approved every High-Risk change without recording a required divergence rationale | 6 | PM + CAB Chair | Resolved — flagged within days; refresher session reset expectations |
| I-07 | One domain's flagged-risk rate fell faster than its actual incident rate — initially looked like a false positive improvement | 7 | PM + Data Science Lead | Resolved — traced to submitters fragmenting changes in response to the visible scoring system; check added for unusually fragmented related submissions |

## Dependencies

| ID | Description | Stage Raised | Owner | Status |
|---|---|---|---|---|
| D-01 | Model Risk Validation sign-off required before production use | 1 | Model Risk Validation Lead | Closed — obtained in Stage 5, with ongoing conditions |
| D-02 | Independent Model Validation review and sign-off required before go-live | 5 | Independent Model Validation Lead | Closed — sign-off obtained, with quarterly/annual conditions attached |
| D-03 | Sponsor and Model Risk Validation sign-off on each rollout phase's results required before proceeding to the next phase | 6 | Sponsor | Closed — all three phases cleared their gates |
| D-04 | Quarterly disparity monitoring and annual revalidation are mandatory conditions of continued production use | 5 → 7 | Model Risk Validation | Open and ongoing by design — not a one-time dependency |

## Changes

| ID | Description | Stage Raised | Owner | Status |
|---|---|---|---|---|
| C-01 | Expanded bias testing across business units requested by Model Risk Validation, beyond original PRD scope | 4 | Model Risk Validation Lead | Approved via formal change request — absorbed in Sprints 7–8 with sponsor sign-off on schedule impact |

---

## RAID Summary by Stage

| Stage | Risks | Assumptions | Issues | Dependencies | Changes |
|---|---|---|---|---|---|
| 1 — Discovery & Business Case | R-01 (raised), R-02 | A-01, A-02, A-03 | — | D-01 | — |
| 2 — Requirements & Data Readiness | R-01 (formalized) | A-04 | I-01, I-02 | — | — |
| 3 — Solution Design & Architecture | R-03, R-04, R-05 | — | — | — | — |
| 4 — Build & Delivery Coordination | — | — | I-03 | — | C-01 |
| 5 — Evaluation & Model Risk Review | R-02 (resolved) | — | I-04, I-05 | D-02 | — |
| 6 — Deployment & Change Management | R-06 (realized), R-07 | A-03 (tested) | I-06 | D-03 | — |
| 7 — Post-Launch Governance | R-08, R-09 | — | I-07 | D-04 (ongoing) | — |

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
