# Communication Plan

**ChangeGuard AI — Predictive Risk Scoring for Change Advisory Board Decisioning**

> See the [Stakeholder Register](./05-Stakeholder-Register.md) for the full stakeholder map this plan is built around. See the [README](./README.md) for full project context.

---

## Ongoing Project Communications (Discovery Through Build)

| Audience | Channel | Content | Cadence | Owner |
|---|---|---|---|---|
| Sponsor (Head of IT Risk & Change Management) | Status meeting | Sprint progress, RAID log review, schedule/budget variance | Weekly, across all 9 build sprints | PM |
| Model Risk Validation | Working sessions | Architecture options, requirement clarification, change-request scoping | As needed, at each stage gate | PM |
| CAB Chair | Discovery interview → working sessions | Problem confirmation, display/UX design input, rollout readiness | Discovery stage; recurring through design and rollout | PM |
| Data Science Lead & build team | Sprint planning & backlog grooming | Feature engineering backlog, sprint goals, mid-sprint findings | Each sprint (9 total) | PM |
| Compliance, Finance | Approval gate reviews | Charter and business case sign-off; budget framing | At Stage 1 approval gate | PM / Sponsor |

## Stage-Gate Communications

| Gate | Audience | Purpose |
|---|---|---|
| Charter & Business Case approval | Sponsor, Model Risk Validation | Commit budget; confirm advisory-only scope is acceptable |
| PRD & Data Readiness sign-off | Model Risk Validation, SRE leads | Confirm failure taxonomy and explainability requirements are precise enough to build to |
| Architecture Decision Record review | Model Risk Validation, Procurement | Confirm chosen model architecture has a viable validation path before build begins |
| Independent Model Validation sign-off | Independent Model Validation Lead, Sponsor, Compliance | Formal go/no-go for production use |
| Phase gate reviews (rollout) | Sponsor, Model Risk Validation, CAB Chair | Confirm success criteria met before expanding rollout scope |

---

## Rollout Communications Plan (Stage 6)

| Audience | Channel | Message | Timing |
|---|---|---|---|
| CAB members (pilot domain) | Working session + live walkthrough | How to read the score and explanation, and what the divergence field is for | 1 week before pilot |
| Affected technology teams | Direct briefing | What the score is, what it isn't, and the written commitment it won't be used in performance evaluation | Before pilot expansion to their domain |
| IT Risk & Change leadership | Weekly override-pattern summary | Early signal on over-trust or under-trust behavior | Weekly through Phase 1 and 2 |
| All CAB members | Short survey | Feedback on usefulness ahead of full rollout decision | End of Phase 2 |

---

## Post-Launch Governance Communications (Stage 7, Ongoing)

| Audience | Channel | Content | Cadence | Owner |
|---|---|---|---|---|
| Head of IT Risk & Change Management | Monitoring report | Change-failure rate trend vs. target | Monthly | PM / Data Science Lead |
| Model Risk Validation | Disparity report | Quarterly fairness/disparity monitoring across business units | Quarterly | Model Risk Validation |
| CAB Chair | Compliance summary | Override-rationale compliance rate | Weekly, ongoing | CAB Chair |
| PM + Data Science Lead (internal) | Behavioral review | Metric-gaming / behavioral adaptation review against actual incident trend | Quarterly | PM + Data Science Lead |
| Independent Model Validation | Revalidation package | Full model revalidation | Annual, or on significant drift | Independent Model Validation |

---

## Key Communication Principles Applied on This Project

- **Bring Risk and Compliance into the conversation at discovery, not after a solution is chosen.** This shaped what was fundable from the start rather than creating rework later.
- **Frame the tool as protecting reviewer judgment, not replacing it.** This framing — developed with Internal Comms — was deliberately chosen ahead of the pilot to avoid CAB members perceiving the tool as adversarial.
- **Escalate emerging concerns immediately rather than waiting for the scheduled review.** When a small group of reviewers showed an over-trust pattern in week one of the pilot, it was flagged to the CAB Chair within days, not held for the next scheduled checkpoint.
- **Put schedule and scope impacts in front of the sponsor with the underlying reason, not just the new date.** When feature engineering slipped due to data quality issues, the revised timeline was communicated along with why — not presented as an unexplained delay.
- **Treat compliance-driven scope additions as formal change requests, not informal absorption.** When Model Risk Validation asked for expanded bias testing mid-build, that request went through a documented change-request process with sponsor approval for the schedule impact.

---

*Part of the [ChangeGuard AI](./README.md) case study by Prachi Sharma.*
