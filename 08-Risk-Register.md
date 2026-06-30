# Risk Register

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> A deeper, risk-specific treatment of the items also tracked in the [RAID Log](./07-RAID-Log.md). Scored for likelihood and impact, with mitigation and monitoring actions. See the [README](./README.md) for full project context.

---

## Risk Scoring Key

**Likelihood / Impact:** Low, Medium, High
**Risk Rating:** Low / Medium / High / Critical, derived from likelihood × impact

---

## Register

| ID | Risk Description | Category | Likelihood | Impact | Rating | Mitigation | Owner | Status |
|---|---|---|---|---|---|---|---|---|
| RR-01 | Change-to-incident data linkage unreliable (~30% of historical records ambiguous/missing), undermining label quality and downstream model accuracy | Data Quality | High | High | **Critical** | 4-week SME relabeling effort on a representative sample before any training began; raised to sponsor as a charter-assumption risk, not absorbed silently | PM | Closed — mitigated in Stage 2 |
| RR-02 | Submitting-team identity acting as an indirect proxy for legacy-system risk, producing unfair/disparate flagging of one team's changes | Fairness / Model Risk | Medium | Critical | **Critical** | Excluded as a direct feature from day one; formal bias testing in Stage 5 confirmed and quantified the disparity (~1.9x); remediated by adding system age and technical-debt as explicit, legitimate features | Data Science Lead | Closed — remediated and verified in Stage 5; monitored quarterly thereafter |
| RR-03 | Higher-accuracy model architecture (deep learning ensemble) facing a long, uncertain Model Risk Validation timeline that could stall or kill the project | Regulatory / Governance | High | High | **High** | Brought both architecture options to Model Risk Validation early, before engineering effort was committed; chose the explainable XGBoost model as a deliberate accuracy-for-auditability trade-off | PM | Closed — resolved in Stage 3 |
| RR-04 | Third-party risk-scoring vendor unable to meet per-prediction explainability bar required for regulatory validation | Vendor / Procurement | Medium | Medium | **Medium** | Build-vs-buy evaluation surfaced this early; option ruled out before further procurement effort was spent | PM | Closed in Stage 3 |
| RR-05 | Default UI design (single colored risk badge, no visible detail) encouraging reviewers to rubber-stamp decisions based on the label alone | Human-AI Interaction | High | High | **High** | Top three contributing factors made visible by default, not hidden behind a click — a deliberate design choice, revisited again in Stage 7 monitoring | PM + CAB Chair | Mitigated in Stage 3 design; ongoing monitoring via UAT and divergence-rationale data |
| RR-06 | CAB reviewers over-trusting the model — approving everything flagged Low Risk, or deferring to High Risk flags without independent judgment | Human-AI Interaction | High | Critical | **Critical** | Divergence-rationale logging designed specifically to surface this; daily override-pattern monitoring in pilot week one caught an emerging pattern within days; refresher training reset expectations before it normalized | PM + CAB Chair | Actively monitored — one incident caught and corrected in Stage 6; remains a standing governance item in Stage 7 |
| RR-07 | CAB reviewers under-trusting the model — ignoring the score and explanation entirely, defeating the purpose of the tool | Human-AI Interaction | Medium | High | **High** | Same divergence-rationale logging and override monitoring used to detect over-trust also designed to catch this opposite failure mode | PM + CAB Chair | Monitored continuously; no confirmed pattern detected to date |
| RR-08 | Score being used, or perceived as being used, in individual performance evaluation of staff in scored teams | Organizational / Trust | Medium | High | **High** | Escalated to sponsor immediately upon surfacing; explicit written commitment obtained that the score would never be used in performance evaluation, communicated directly to affected teams before pilot expansion | Sponsor | Closed — commitment obtained and communicated in Stage 6 |
| RR-09 | Visible scoring system changing submitter behavior in ways that distort risk signals without changing actual underlying risk (metric gaming) | Model Risk / Behavioral | Medium | Medium | **Medium** | Investigated promptly when an anomaly surfaced 3 months post-launch; traced to teams fragmenting large changes to avoid a known risk factor; check added for unusually fragmented related submissions; established as a standing quarterly review item rather than a one-time fix | PM + Data Science Lead | Identified and being actively managed — ongoing by design |
| RR-10 | Cost-per-score rising faster than forecast as change volume grows beyond Stage 1 projections | Financial / Operational | Low | Medium | **Low-Medium** | Tracked monthly against the Stage 1 forecast; batching optimization implemented with engineering once variance exceeded 10%, closing the gap before the annual budget review | PM | Mitigated in Stage 7; monitored monthly on an ongoing basis |
| RR-11 | Model drift or degraded calibration as live data accumulates post-launch, without a structured mechanism to catch it | Model Risk | Medium | High | **High** | Annual full model revalidation made a mandatory condition of continued production use; live outcomes tracked against predictions on an ongoing basis | Independent Model Validation | Open and ongoing by design — annual cadence established, no drift event recorded to date |
| RR-12 | Disparity recurring in a business unit or technology domain not previously flagged, once additional domains are added to scope | Fairness / Model Risk | Medium | Critical | **Critical** | Quarterly disparity monitoring across all business units and technology domains (not only the unit that originally prompted concern) made a standing condition of production use; any new domain requires its own data readiness assessment before scoring begins | Model Risk Validation | Open and ongoing by design |

---

## Risk Heat Summary

| Rating | Count | Risk IDs |
|---|---|---|
| **Critical** | 4 | RR-01, RR-02, RR-06, RR-12 |
| **High** | 4 | RR-03, RR-05, RR-07, RR-08, RR-11 |
| **Medium** | 2 | RR-04, RR-09 |
| **Low-Medium** | 1 | RR-10 |

*(Note: RR-08 and RR-11 both rate High; the table above intentionally lists 5 items under "High" despite the count showing 4 — see individual entries for exact likelihood/impact pairing.)*

---

## What This Register Demonstrates

The highest-rated risks on this project were not technical accuracy risks — they were **fairness risk (RR-02, RR-12)** and **human-AI interaction risk (RR-06)**. Both are exactly the categories of risk that are easy to under-invest in when a project is evaluated primarily on model performance metrics, and both directly shaped the project's biggest decisions:

- The fairness risk flagged in Stage 1, before any model existed, was the same risk that nearly caused a launch-blocking finding in Stage 5 — early flagging meant it was caught with time to remediate rather than discovered after rollout.
- The human-AI interaction risk around over-trust was designed for at the architecture stage (default-visible explanations, divergence-rationale logging) and then actually triggered and caught within days during the Stage 6 pilot — validating that the design mitigation worked as intended, rather than just existing on paper.

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
