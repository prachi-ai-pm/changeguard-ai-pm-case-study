# User Stories

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> Story-level detail for the highest-priority items in the [Product Backlog](./10-Product-Backlog.md), written from the perspective of the actual end users and governance stakeholders identified in the [Stakeholder Register](./05-Stakeholder-Register.md). See the [README](./README.md) for full project context.

---

## Epic E2 — Risk Scoring Model

### US-01
**As a** CAB reviewer,
**I want** every change request to receive a Low / Medium / High risk classification before my review session,
**so that** I can prioritize my limited review time toward the changes that actually carry the most risk.

**Acceptance Criteria:**
- 100% of changes routed through CAB receive a score before review.
- Score is generated within 1 hour of change submission.
- Score is one of exactly three values: Low, Medium, High.

**Linked Backlog Item:** PB-07
**Linked Requirement:** PRD — Risk score per change

---

### US-02
**As a** CAB reviewer,
**I want** the model to account for timing patterns (e.g., weekend or pre-holiday submissions) in addition to the change's technical content,
**so that** the score reflects real-world risk factors, not just what's in the change ticket.

**Acceptance Criteria:**
- Timing-related features are included in the model's feature set.
- The feature's contribution is visible in the per-prediction explanation when it materially affects the score.

**Linked Backlog Item:** PB-08
**Linked Decision:** Stage 4, Sprint 6 mid-build finding

---

## Epic E3 — Explainability & Feature Attribution

### US-03
**As a** CAB reviewer without a data science background,
**I want** to see the top three factors driving a change's risk score in plain language,
**so that** I can understand and act on the score without needing data science support.

**Acceptance Criteria:**
- CAB members can identify the top 3 contributing factors without data science support (verified in UAT).
- Explanation is generated using per-prediction SHAP-based attribution.
- Explanation language is plain language, not raw feature names or statistical jargon.

**Linked Backlog Item:** PB-09, PB-10
**Linked Requirement:** PRD — Explainability

---

### US-04
**As a** Model Risk Validation reviewer,
**I want** every prediction to come with a reviewable, per-prediction explanation rather than only a global feature-importance ranking,
**so that** I can validate the model meets our explainability bar before approving it for production use.

**Acceptance Criteria:**
- Explanation method is SHAP-based and applied per individual prediction, not only in aggregate.
- Explanation format is reviewable by a non-technical CAB member.
- Requirement is documented precisely enough in the PRD for engineering to build directly against it.

**Linked Backlog Item:** PB-09
**Linked Issue:** Stage 2 — initial explainability language too vague to design against

---

## Epic E4 — Fairness & Proxy-Discrimination Prevention

### US-05
**As a** Model Risk Validation lead,
**I want** confirmation that submitting-team identity is excluded as both a direct and an easily-derived model feature,
**so that** the model cannot unfairly penalize a team for who they are rather than the actual risk of their changes.

**Acceptance Criteria:**
- Submitting-team identity is not used as a direct input feature.
- Fairness testing confirms no easily-derived proxy for team identity materially drives the score.
- Verified by formal fairness testing in Stage 5, not just a design-time assertion.

**Linked Backlog Item:** PB-11, PB-12
**Linked Requirement:** PRD — No proxy discrimination

---

### US-06
**As a** lead of the team supporting the oldest core banking systems,
**I want** my team's changes to be flagged as risky because of legitimate, explainable factors like system age — not because of an unexplained pattern tied to my team,
**so that** I can trust the score is measuring the change, not penalizing my team for circumstances outside our control.

**Acceptance Criteria:**
- Disparity testing run across all business units and technology domains, not only the unit that prompted the original concern.
- Any disparity found is traced to a specific, legitimate, documented feature (e.g., system age) rather than left unexplained.
- System age and technical-debt indicators are added as explicit model features once identified as the true driver of disparity.

**Linked Backlog Item:** PB-14
**Linked Risk:** [Risk Register](./08-Risk-Register.md) RR-02

---

### US-07
**As a** Data Science Lead,
**I want** a quarterly check for unusually fragmented related change submissions,
**so that** I can detect if a domain is splitting changes specifically to game a known risk factor, rather than mistaking that pattern for genuine risk reduction.

**Acceptance Criteria:**
- A flagged-risk trend that diverges from the actual incident trend triggers an investigation.
- The check identifies clusters of related submissions that appear to be artificially fragmented.
- Findings are raised directly with the affected domain lead, not treated as a one-time violation to discipline.

**Linked Backlog Item:** PB-24
**Linked Issue:** [RAID Log](./07-RAID-Log.md) I-07

---

## Epic E5 — CAB Workflow Integration & Display

### US-08
**As a** CAB reviewer,
**I want** the risk score and its top contributing factors visible by default, without an extra click,
**so that** I'm not tempted to rubber-stamp a decision based on a colored label alone.

**Acceptance Criteria:**
- Top three contributing factors are shown by default alongside the risk score on first view.
- No additional click or navigation is required to see the explanation.
- UAT confirms this design measurably increases reported usefulness of explanations versus a label-only design.

**Linked Backlog Item:** PB-15
**Linked Decision:** Stage 3 ADR — Human-in-the-Loop & Display Design

---

### US-09
**As a** CAB reviewer,
**I want** to see the score and explanation directly inside the ServiceNow workflow I already use,
**so that** I don't need to switch tools or context to use this during a review.

**Acceptance Criteria:**
- Score and explanation are surfaced natively inside the existing ServiceNow CAB workflow.
- No separate login, tool, or interface is required to access the score.

**Linked Backlog Item:** PB-16
**Linked Requirement:** Charter — "In Scope (v1)"

---

### US-10
**As a** CAB Chair,
**I want** reviewers to record a one-line rationale whenever their decision diverges from the model's score, in either direction,
**so that** I have structured data to identify both over-trust and under-trust patterns before they become normalized.

**Acceptance Criteria:**
- Divergence-rationale field is required whenever a reviewer's final decision differs from the model's score.
- Field captures direction of divergence (reviewer more cautious vs. less cautious than the model).
- Data is retrievable for override-pattern monitoring during rollout and ongoing governance.

**Linked Backlog Item:** PB-17
**Linked Decision:** Stage 3 ADR — designed specifically to surface over-trust and under-trust later (validated in Stage 6)

---

## Epic E6 — Auditability & Logging

### US-11
**As a** Model Risk Validation reviewer,
**I want** every score, its inputs, and the reviewer's final decision logged and retrievable,
**so that** I can audit any individual decision and satisfy regulatory documentation requirements.

**Acceptance Criteria:**
- Every score generated is logged with its full input feature set.
- The reviewer's final decision and any divergence rationale are logged against the same record.
- Logged records are retrievable on demand for audit review.

**Linked Backlog Item:** PB-18
**Linked Requirement:** PRD — Auditability

---

## Epic E7 — Validation & Governance Readiness

### US-12
**As an** Independent Model Validation lead,
**I want** a complete documentation package covering model methodology, data lineage, fairness testing, and explainability output,
**so that** I can issue a sign-off decision with clearly stated conditions for continued production use.

**Acceptance Criteria:**
- Documentation package covers methodology, data lineage, fairness testing, and explainability output in full.
- Any documentation gap identified during review (e.g., relabeling methodology) is remediated and resubmitted before sign-off.
- Sign-off explicitly states conditions of continued use (e.g., quarterly disparity monitoring, annual revalidation).

**Linked Backlog Item:** PB-20, PB-21
**Linked Deliverable:** Evaluation Report, Fairness Review & Independent Validation Sign-Off (Stage 5)

---

## Epic E8 — Launch Readiness

### US-13
**As a** CAB Chair preparing for pilot rollout,
**I want** a go-live runbook with explicit rollback triggers and a named decision owner,
**so that** the team can act quickly and decisively if something goes wrong during rollout, instead of debating ownership in the moment.

**Acceptance Criteria:**
- Runbook names specific rollback triggers (e.g., override-rationale compliance falling below threshold, a disparity flag reappearing, a confirmed performance-evaluation misuse).
- Runbook names a decision owner with a defined response time (e.g., within 48 hours of a trigger being raised).
- Runbook is reviewed and accepted before Phase 1 pilot begins.

**Linked Backlog Item:** PB-23
**Linked Deliverable:** Go-Live Runbook & Communications Plan (Stage 6)

---

### US-14
**As a** CAB member participating in UAT,
**I want** to test the score and explanation against real changes before full rollout,
**so that** any usability gaps — like skimming past the explanation — are caught and addressed before they become embedded habits in production.

**Acceptance Criteria:**
- UAT is conducted with real CAB members, not only internal testers.
- UAT specifically measures whether explanations changed how reviewers approached a decision, not just whether the explanation was technically present.
- Usability findings (e.g., label-skimming) are fed into the Stage 6 rollout and training plan, not deferred indefinitely.

**Linked Backlog Item:** PB-22
**Linked Issue:** [RAID Log](./07-RAID-Log.md) I-04

---

## Story Map by Epic

| Epic | Stories |
|---|---|
| E2 — Risk Scoring Model | US-01, US-02 |
| E3 — Explainability & Feature Attribution | US-03, US-04 |
| E4 — Fairness & Proxy-Discrimination Prevention | US-05, US-06, US-07 |
| E5 — CAB Workflow Integration & Display | US-08, US-09, US-10 |
| E6 — Auditability & Logging | US-11 |
| E7 — Validation & Governance Readiness | US-12 |
| E8 — Launch Readiness | US-13, US-14 |

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
