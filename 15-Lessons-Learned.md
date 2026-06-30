# Lessons Learned

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> A reflective review captured as part of Stage 7 — Post-Launch Governance, fed into the forward roadmap and into how this case study is presented. See the [Project Closure Report](./14-Project-Closure-Report.md) for the formal closure record and the [README](./README.md) for full project context.

---

## The Headline Lesson

The most interesting finding in this entire project showed up three months after full rollout, and it wasn't a model accuracy problem — it was a behavioral one. A decision-support model changes the behavior of the people being scored, and that needs to be actively watched for, not assumed away just because the model itself is performing well. This single insight reshaped how Post-Launch Governance is run on this project, and is the lesson most worth carrying into the next one.

---

## Lessons by Stage

### Stage 1 — Discovery & Business Case
**Lesson:** The first version of a stakeholder's ask is rarely the version that gets funded. The original request — auto-approving low-risk changes — was a non-starter for Model Risk and Compliance. Reframing it into an advisory risk score, before any budget was committed, made the project fundable faster, not slower. Bringing Risk and Compliance into the room at discovery, rather than after a solution was chosen, was the single highest-leverage move in the whole project — it shaped what was fundable from day one instead of creating expensive rework later.

**Carry forward:** Treat governance and compliance partners as a design input at discovery, not a checkpoint to pass through later.

### Stage 2 — Requirements & Data Readiness Assessment
**Lesson:** Stakeholders had not agreed on what counted as a change "failure" before this project started. Almost no one talks about getting alignment on what a metric even means before measuring against it — but without that agreement, every downstream number would have been built on a contested foundation. The cross-functional failure-taxonomy workshop was unglamorous work, but it was load-bearing for everything that followed.

**Carry forward:** Don't let a metric definition stay implicit just because everyone seems to be nodding along. Make it explicit and get it signed off before it becomes the basis for a model.

### Stage 3 — Solution Design & Architecture
**Lesson:** The model architecture with the best raw predictive performance was not the one that could actually ship in a regulated environment. Choosing the less powerful but more explainable model was a deliberate accuracy-for-auditability trade-off, made consciously and early rather than discovered late after engineering effort had already been sunk into the more complex option.

**Carry forward:** Bring competing architecture options to governance partners before committing engineering effort, not after. A trade-off decided early is a design choice; the same trade-off discovered late is a schedule risk.

### Stage 4 — Build & Delivery Coordination
**Lesson:** A strong, generalizable signal (the weekend/pre-holiday submission risk pattern) showed up mid-sprint, not during planning. Re-prioritizing the backlog to incorporate it immediately — rather than parking it for a future release — meant the model launched with a materially better feature set. Protecting the original sprint plan would have been the safer-looking choice and the worse one.

**Carry forward:** When the team surfaces a strong technical signal mid-build, the discipline question isn't "should we stick to the plan" — it's "is this good enough to justify replanning," and that's a judgment call worth making quickly rather than deferring by default.

### Stage 5 — Evaluation, Testing & Model Risk Review
**Lesson:** This is the strongest story in the whole case study, and the clearest argument for taking fairness testing seriously before launch rather than after. The early signal that submitting-team identity might act as a proxy for legacy-system risk, flagged all the way back in Stage 1, turned out to be real — formal bias testing in Stage 5 confirmed a ~1.9x disparity. Tracing it to a legitimate, explainable cause (system age) rather than leaving it unexplained, and remediating before launch, is the difference between catching a fairness problem and causing real harm after rollout.

**Carry forward:** A fairness concern flagged early and dismissed as "probably fine" is not closed — it's deferred. Carry it through to formal testing rather than letting early reassurance substitute for verification.

### Stage 6 — Deployment & Change Management
**Lesson:** Shipping a well-validated, fair, accurate model is not the same as shipping a model that's used well. A small group of reviewers showed an over-trust pattern — approving every High-Risk change without recording the required divergence rationale — within the first week of pilot. Catching it within days, rather than letting it normalize before the next scheduled checkpoint, only worked because the monitoring design (daily override-pattern checks in week one) was built to catch exactly this failure mode before launch, not invented in response to the incident.

**Carry forward:** Design monitoring for the human-AI interaction failure modes you expect, before launch — don't wait to build detection until after a pattern has already had time to normalize.

### Stage 7 — Post-Launch Governance & Continuous Improvement
**Lesson:** A visible scoring system changes the behavior of the people being scored — not maliciously, but rationally. When one domain's flagged High-Risk rate fell faster than its actual incident rate improved, the cause wasn't model drift; it was a team fragmenting large changes into smaller submissions specifically because change size was a known risk factor. This is a fundamentally different category of problem from anything a standard accuracy or fairness metric would catch, and it's the kind of insight that separates active model governance from "ship and monitor a dashboard."

**Carry forward:** Once a scoring system is visible to the people it scores, treat behavioral adaptation as an expected, ongoing phenomenon to monitor for — not a one-time anomaly to patch and close.

---

## Cross-Cutting Lessons

- **Every schedule, scope, or budget change was surfaced explicitly, never absorbed silently.** The Sprint 1–3 extension was re-baselined and explained to the sponsor with the underlying reason, not presented as an unexplained delay. The Sprint 7–8 scope addition went through a formal change request. This pattern, repeated consistently across the project, did more for stakeholder trust than any individual technical decision.
- **The riskiest parts of this project were not the model's accuracy — they were fairness and human-AI interaction.** Both categories are easy to under-invest in when a project is evaluated primarily on model performance metrics. On this project, both were treated with the same rigor as accuracy from the start, and both ended up being where the real findings were.
- **"Done" is not the same as "closed."** This project transitions into standing governance rather than ending — quarterly disparity checks, annual revalidation, and ongoing cost-per-score tracking are not residual cleanup; they're the normal operating condition of a regulated decision-support model in production. Treating post-launch monitoring as a first-class deliverable, not an afterthought, is itself a lesson worth naming.

---

## How These Lessons Shaped the Forward Roadmap

Two of the three forward-roadmap items captured in the [Project Closure Report](./14-Project-Closure-Report.md#forward-roadmap-handed-to-governance) trace directly back to lessons on this page:

- The retraining-feedback-loop idea (using CAB override rationale to periodically retrain the model) is a direct response to the Stage 6 and 7 lessons about human-AI interaction — if reviewers are generating high-quality divergence data, that data should eventually inform the model, not just be logged.
- The decision to explicitly defer fast-tracking very-low-risk changes until a longer production track record exists is a direct, conservative response to the Stage 7 metric-gaming finding — proving the system is resistant to behavioral gaming before reducing the level of human review applied to it.

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
