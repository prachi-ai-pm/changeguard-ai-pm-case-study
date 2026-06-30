# ChangeGuard AI

**An End-to-End AI/ML Project Management Case Study**
*Predictive Change-Risk Scoring for IT Change Advisory Boards — Discovery Through Production Governance*

**Prachi Sharma** · AI Project Manager · Technical PM · Gen AI Delivery Lead

---

## A Note on This Repository

This is a self-directed case study built to demonstrate AI/ML project management methodology applied to a predictive (non-generative) ML use case — deliberately different from my ServiceDesk Copilot case study, which covers a Gen AI / RAG scenario. The company, stakeholders, and figures are illustrative, modeled on realistic regulated-enterprise change management practices, including the kind of CAB (Change Advisory Board) governance I run in my current role.

**Presented honestly as a self-built simulation, not a claimed client engagement.**

---

## Project Overview

Solenne Financial Group is a fictionalized 8,000-employee global retail and commercial bank, modeled on the kind of regulated enterprise IT environments I support in my current role. Its IT Change Advisory Board (CAB) reviews roughly 600 production changes a month across core banking, payments, and customer-facing digital systems.

A baseline change-failure rate of **9.5%** — changes that were rolled back, triggered a P1/P2 incident, or required an emergency fix — was costing the bank an estimated **$5.5M a year** in remediation effort, customer impact, and incident-driven regulatory reporting. CAB itself had become a bottleneck: reviewers were spending equal time on routine, low-risk changes and genuinely risky ones simply because there was no consistent way to tell them apart at scale.

This case study documents the end-to-end management of **ChangeGuard AI**, a predictive machine learning model that scores incoming change requests for risk and surfaces the specific factors driving that score, so CAB can focus its limited review time where it matters most.

Unlike the ServiceDesk Copilot case study, this is a **classical predictive ML problem** rather than a generative one — chosen deliberately to show range across the AI/ML PM lifecycle: model risk governance, explainability requirements, fairness testing, and the very different failure modes that come with decision-support models used in a regulated environment.

### Project Snapshot

| | |
|---|---|
| **Role** | AI/ML Project Manager (sole PM, cross-functional lead) |
| **Duration** | 18 weeks discovery-to-launch, plus ongoing governance |
| **Team** | 1 PM, 2 data scientists, 1 data engineer, 1 backend/integration engineer, 1 QA analyst, part-time Model Risk Validation, Compliance, and Finance partners |
| **Methodology** | Hybrid Agile — two-week sprints inside a Waterfall-style stage-gate structure for independent model validation and regulatory sign-off |
| **Sponsor** | Head of IT Risk & Change Management |
| **Core stack** | Python / XGBoost (chosen for explainability over deep learning), SHAP for feature attribution, ServiceNow Change & CMDB data as the primary source, scores surfaced directly inside the existing ServiceNow CAB workflow |
| **Outcome (6 months post-launch)** | Change failure rate reduced from 9.5% to 7.4% against a 7% target; ~$1.3M projected annualized savings run-rate |

---

## Repository Contents

| Document | Description |
|---|---|
| [`01-Project-Charter.md`](./01-Project-Charter.md) | Problem statement, objectives, success metrics, scope, budget, and approval gate from Stage 1 — Discovery & Business Case |
| [`02-Business-Case.md`](./02-Business-Case.md) | Cost of the status quo, financial framing, key assumptions, and the stakeholder dynamics that shaped a fundable scope |
| [`03-Scope-Statement.md`](./03-Scope-Statement.md) | In-scope / out-of-scope boundaries, constraints, deliverables, and the human-in-the-loop design that kept this model strictly advisory |
| [`04-WBS.md`](./04-WBS.md) | Work breakdown structure spanning all seven delivery stages and the nine build sprints |
| [`05-Stakeholder-Register.md`](./05-Stakeholder-Register.md) | Full stakeholder map — sponsor, governance partners, build team, and end users — with interest, influence, and engagement strategy |
| [`06-Communication-Plan.md`](./06-Communication-Plan.md) | How and when each stakeholder group was engaged, from discovery through ongoing post-launch governance |
| [`07-RAID-Log.md`](./07-RAID-Log.md) | Risks, Assumptions, Issues, Dependencies, and Changes tracked across the full project lifecycle |
| [`08-Risk-Register.md`](./08-Risk-Register.md) | Risk-specific deep dive with likelihood/impact scoring, mitigations, and what the risk profile reveals about this project |
| [`09-Sprint-Plan.md`](./09-Sprint-Plan.md) | Sprint-by-sprint breakdown of the nine two-week build sprints, including the mid-build re-prioritization and the formal change request that added scope |
| [`10-Product-Backlog.md`](./10-Product-Backlog.md) | Prioritized backlog translating the PRD requirements and architecture decisions into estimable, sprint-ready items |
| [`11-User-Stories.md`](./11-User-Stories.md) | Detailed user stories with acceptance criteria for the highest-priority backlog items, written from each stakeholder's perspective |
| [`12-Budget.md`](./12-Budget.md) | One-time build and validation cost breakdown, ongoing run cost, ROI framing, and post-launch budget variance tracking |
| [`13-Architecture-Diagram.md`](./13-Architecture-Diagram.md) | System architecture from data sources through model, explainability layer, CAB workflow, and governance monitoring, with a GitHub-native Mermaid diagram |
| [`14-Project-Closure-Report.md`](./14-Project-Closure-Report.md) | Formal closure against the Stage 1 charter — objectives vs. outcomes, budget closure, governance sign-offs, and the handoff to standing operational governance |
| [`15-Lessons-Learned.md`](./15-Lessons-Learned.md) | A stage-by-stage reflective review, including the metric-gaming finding that is the strongest single insight in the case study |
| [`16-Complete-Documentation.md`](./16-Complete-Documentation.md) | A full index of every artifact organized by project phase, with a documentation coverage map and notes on how everything cross-links |

---

## The Seven-Stage Lifecycle

This case study follows the full lifecycle of an AI/ML initiative in a regulated environment — not just the parts that are easy to show off:

1. **Discovery & Business Case** — Reframing "auto-approve low-risk changes" into a fundable, advisory-only scope.
2. **Requirements & Data Readiness Assessment** — Settling what "failure" even means before measuring anything against it.
3. **Solution Design & Architecture** — Trading a small accuracy gain for a materially shorter, more certain path through Model Risk Validation.
4. **Build & Delivery Coordination** — Re-prioritizing the backlog mid-sprint for a finding that materially improved the model.
5. **Evaluation, Testing & Model Risk Review** — Catching a real fairness issue before launch, not after.
6. **Deployment & Change Management** — Actively managing both over-trust and under-trust in the model during rollout.
7. **Post-Launch Governance & Continuous Improvement** — Catching a metric-gaming pattern three months in, driven by behavior change rather than model drift.

The full narrative — including the key questions asked at each stage, the issues encountered, and how they were resolved — is the heart of this case study. The sixteen documents in this repository (start with [16-Complete-Documentation.md](./16-Complete-Documentation.md) for a guided index) are the artifacts a PM would actually produce along the way.

### Outcomes Summary — 6 Months Post-Launch

| Metric | Baseline | Target | Actual @ 6 Months |
|---|---|---|---|
| Change-failure rate | 9.5% | 7.0% | 7.4% |
| Annualized cost savings run-rate | — | ~$1.5M | ~$1.3M (ramping as full-domain rollout annualizes) |
| Recall on historically high-risk changes | N/A (pre-launch) | ≥ 75% | 78% (Stage 5), holding at 76% in production |
| CAB override-rationale compliance | N/A (pre-launch) | ≥ 95% | 97%, after one mid-rollout correction |
| Disparity across business units | ~1.9x (pre-fix) | No material disparity | ~1.1x, within normal variation, monitored quarterly |
| Average CAB review time, low-risk changes | 3.2 business days | Reduced | 1.6 business days |

The failure-rate reduction is the easy headline. The story that actually demonstrates judgment is everything else: catching a fairness problem before launch instead of after, designing the rollout to watch for both over-trust and under-trust in the model, and catching a metric-gaming pattern that had nothing to do with the model's accuracy and everything to do with how a visible scoring system changes the behavior of the people being scored.

---

## Project Status

**Delivered and transitioned to standing governance.** All charter objectives were met or substantially met at the 6-month mark, with no scope cuts and no budget overrun. The project formally closed against its Stage 1 charter and handed off into ongoing operational governance — quarterly disparity monitoring, annual model revalidation, and continued cost-per-score tracking. See [14-Project-Closure-Report.md](./14-Project-Closure-Report.md) for the full closure record and [15-Lessons-Learned.md](./15-Lessons-Learned.md) for the reflective review, including the single most senior-level finding in the case study.

---

## How This Fits Into My Portfolio

This case study is paired with a **ServiceDesk Copilot** case study (Gen AI / RAG). Together they're meant to show range across the AI/ML PM lifecycle:

- **Lead with ChangeGuard AI** for regulated-industry, model-risk-heavy, or enterprise IT roles.
- **Lead with ServiceDesk Copilot** for Gen AI / conversational AI-focused roles.

---

*Prachi Sharma — AI Project Manager · Technical PM · Gen AI Delivery Lead*

