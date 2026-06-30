# Stakeholder Register

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> See the [README](./README.md) for full project context and the [Communication Plan](./06-Communication-Plan.md) for how engagement with each stakeholder was operationalized.

---

## Register

| Stakeholder | Role / Function | Interest | Influence | Stake / Expectations | Engagement Strategy |
|---|---|---|---|---|---|
| **Head of IT Risk & Change Management** | Project Sponsor | High | High | Wants reduced change-failure cost and a defensible, regulator-ready governance model; ultimately accountable for the approval gate and rollback decisions | Weekly status touchpoints during build; joint rollback decision authority with PM; direct escalation point for cross-team conflicts (e.g., performance-review concern in Stage 6) |
| **CAB Chair** | Process owner for the Change Advisory Board | High | High | Needs CAB's review bottleneck solved without losing reviewer judgment or being blamed for poor outcomes if reviewers over- or under-trust the score | Discovery interviews; consulted on display design to reduce rubber-stamping risk; weekly override-pattern summaries during rollout; first point of escalation on override-compliance issues |
| **Model Risk Validation (Lead / Function)** | Independent governance partner, engaged from discovery onward | High | High | Needs explainability, documentation, and fairness testing sufficient to clear a validation review; will block production use if not satisfied | Brought into the room at discovery, not after a solution was chosen; consulted on architecture trade-offs; formal requirement-setting in PRD; requested and received a formal change request process for added scope |
| **Independent Model Validation (Lead)** | Final, independent sign-off authority before production use | High | High | Needs methodology, data lineage, fairness testing, and documentation complete enough to approve; sets binding conditions of sign-off | Engaged formally at the evaluation stage; documentation package submitted, gap remediated and resubmitted on request; final sign-off recorded with explicit ongoing conditions |
| **Compliance** | Regulatory and policy oversight | High | High | Needs assurance the model is advisory-only and won't create unmanaged regulatory exposure | Present at discovery; consulted on whether the model could ever make an autonomous decision (it cannot, by design); co-approver of Independent Model Validation sign-off |
| **Site Reliability Engineering (SRE) Leads** | Subject-matter input on change/incident reality | Medium | Medium | Wants the failure definition to reflect operational reality, not just regulatory reportability | Discovery interviews on failure cost; central voice in the failure-taxonomy workshop; coordinated manual relabeling of ambiguous historical records |
| **Data Science Lead** | Technical delivery lead | High | Medium | Wants a model that is both technically sound and approvable; navigates the accuracy-vs-explainability trade-off directly | Weekly sprint cadence; joint evaluation of architecture options; led investigation into bias-testing and metric-gaming findings |
| **Data Engineers (2)** | Build team — data pipeline and feature engineering | Medium | Low | Needs clear, estimable requirements given known data quality issues | Embedded in sprint planning and backlog grooming; consulted on feasibility of mid-build feature additions |
| **Backend / Integration Engineer** | Build team — ServiceNow workflow integration | Medium | Low | Needs the score and explanation to surface cleanly inside the existing CAB workflow without disrupting it | Included in sprint planning; responsible for the in-workflow display implementation |
| **QA Analyst** | Build team — quality assurance | Medium | Low | Needs testable acceptance criteria tied to the PRD | Included in sprint planning and UAT coordination |
| **Finance** | Budget and ROI oversight | Medium | Medium | Initially wanted ROI framed around CAB headcount reduction | Business case discussion redirected the ROI framing toward failed-change cost avoidance to keep CAB Chair support and avoid internal resistance |
| **Procurement** | Vendor evaluation support | Low | Low | Needed a clear answer on whether the third-party SaaS option could meet explainability requirements | Consulted once during the build-vs-buy evaluation in Stage 3; option ruled out early on compliance grounds |
| **CAB Members (Reviewers)** | End users of the risk score and explanation | High | Medium | Want a tool that helps them work faster without being used to judge their performance, and without being forced to defer to a number they don't trust | UAT participation; targeted training on reading explanations, not just the label; working sessions before pilot; divergence-rationale logging gives them a structured way to push back on the model |
| **Affected Technology Domain Teams** | Teams whose changes are being scored | Medium | Medium | Concerned the score could be used against them in performance reviews | Direct briefing before pilot expansion to their domain; explicit written sponsor commitment that the score would never be used in individual performance evaluation |
| **Internal Comms** | Change communications support | Low | Low | Needs framing guidance to avoid the rollout being perceived as replacing reviewer judgment | Consulted on rollout messaging — framed as a tool that protects reviewer judgment with better information |

---

## Notes on Stakeholder Management

- **Risk and Compliance were brought into the room at discovery**, before any solution was chosen — a deliberate choice that shaped what was fundable from day one, rather than something negotiated after a model was already built.
- **The CAB Chair and affected technology teams were the stakeholders whose concerns surfaced latest** — the performance-review concern in particular wasn't raised in earlier stakeholder conversations, and required a sponsor-level commitment once it did surface during rollout.
- **Finance's initial ROI framing was a stakeholder-management problem as much as a financial one** — accepting the headcount-reduction framing would have turned a process-improvement project into something that looked like a threat to the board it depended on for adoption.

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
