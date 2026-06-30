# Scope Statement

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> Drawn from the **Project Charter** (Stage 1) and refined through **Solution Design & Architecture** (Stage 3). See the [README](./README.md) for full project context.

---

## In Scope (v1)

Risk scoring and explanation for changes across:

- Core banking systems
- Payments systems
- Customer-facing digital systems

The score is surfaced **directly inside the existing ServiceNow CAB workflow** — reviewers do not need to use a separate tool to see a change's risk score and explanation.

### Functional Scope

| Capability | Detail |
|---|---|
| Risk score per change | Low / Medium / High classification for every submitted change in scope |
| Explainability | Per-prediction SHAP-based feature attribution, in plain language, surfaced as the top 3 contributing factors |
| Display design | Top three contributing factors shown **by default**, not hidden behind an extra click — a deliberate design choice to reduce rubber-stamping risk |
| Divergence tracking | CAB reviewers record a one-line rationale whenever their decision diverges from the model's score, in either direction |
| Auditability | Every score, its inputs, and the reviewer's final decision are logged and retrievable |

### Phased Rollout Scope

| Phase | Scope | Duration |
|---|---|---|
| 1 — Pilot | Core banking change domain, ~150 changes/month | 3 weeks |
| 2 — Expanded pilot | Payments and digital channel domains, ~250 changes/month | 3 weeks |
| 3 — Full rollout | All remaining in-scope domains, ~200 changes/month | Phased over 4 weeks |

Each phase has an explicit success gate to proceed — the project did not assume a clean rollout, and was designed to be stopped or rolled back at each gate if needed.

---

## Out of Scope (v1)

- **Autonomous approval or rejection of any change.** The model produces an advisory score and explanation only. A human reviewer always makes the final decision.
- **Use of the model outside the CAB workflow.** This is a CAB decision-support tool, not a general-purpose risk-scoring service.
- **Any feature derived directly from submitting-team identity.** Excluded as both a direct feature and — following the Stage 5 fairness review — checked for indirect/proxy influence as well.
- **Auto-fast-tracking very-low-risk changes with lighter review.** Explicitly deferred to a future version, pending a longer production track record (see Forward Roadmap below).

---

## Key Constraints

- No use of submitting-team identity as a direct model feature.
- Independent model validation required before production use.
- The model must remain advisory only in v1 — it cannot approve or block a change itself.
- Latency requirement: score must be generated within 1 hour of change submission (not real-time-critical, since scores need only be ready before the relevant CAB session).

## Human-in-the-Loop Design (Carried Into Scope From Stage 3)

- The model never approves or blocks a change; it produces an advisory score and explanation only.
- The top three contributing factors are shown by default alongside the risk score.
- CAB reviewers are required to record a one-line rationale when their decision diverges from the model's score, in either direction — designed specifically to surface both over-trust and under-trust patterns post-launch.
- Every score, its inputs, and the reviewer's final decision are logged for audit and for ongoing fairness monitoring.

---

## Scope Changes During Delivery

Scope discipline mattered as much as the original boundary. Two scope-relevant events occurred during build, both handled explicitly rather than absorbed silently:

- **Mid-build finding on timing-related risk:** Changes submitted on weekends or immediately before public holidays showed a substantially higher failure rate, independent of the change's technical content. This was a strong, generalizable signal, and the backlog was re-prioritized to incorporate it into the feature set rather than deferring it to a later release.
- **Expanded bias testing request:** Model Risk Validation requested expanded bias testing across business units partway through build, beyond what was originally scoped in the requirements document. This was logged as a **formal change request**, scoped with data science, and approved by the sponsor for its schedule impact — rather than treated as a compliance ask to just absorb informally.

---

## Forward Roadmap (Explicitly Deferred Items)

Identified during post-launch governance as candidates for a future version, not committed to v1:

- Extend scoring to additional technology domains not in the original in-scope list, pending their own data readiness assessment.
- Explore a feedback loop where CAB override rationale is used to periodically retrain and refine the model, with the same fairness testing rigor applied to every retrain.
- Evaluate, with Model Risk Validation, whether a future version could support fast-tracking very-low-risk changes with lighter review rather than full CAB review.

---

*Document scope drawn from the Project Charter (Stage 1) and the Architecture Decision Record (Stage 3). Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
