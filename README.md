# AI GRC Copilot

**Version 1.1.0 · 15 July 2026 · Production mirror of the AI GRC Spellbook Copilot custom GPT**

This is the spellbook for the **AI GRC Spellbook Copilot** custom GPT, deployed at:

**https://chatgpt.com/g/g-6957671b65188191963a0b5cf59cc4c4-ai-grc-spellbook-copilot**

This is a **Shared Spellbook** for AI governance, risk management and compliance (AI GRC). Spellbooks are workflows, prompts and working habits that help you use AI to get real work done and keep it operable and maintainable.

The AI GRC Spellbook Copilot helps generate a stack of 30 basic artifacts for use in AI GRC.

Not everyone needs every item. If you are running high-risk AI in a grown-up organization, this is the map.

Governance is, among other things, a documentation engine that produces decisions and proof. If you cannot point to the artifact, the owner, the control and the log, you do not have governance. You have hope.

The prompt will not do the job for you. You supply facts, constraints, decisions and approvals. The model drafts and stress-tests. You own the risk.

Delegation is not abdication.

**Final Liability rests with the Human.**

## How to use it

1. Open the deployed GPT at the link above (requires a ChatGPT account).
2. Answer the [Master List of Minimum Questions](https://github.com/rolldabones/AI-GRC-Master-List-of-Questions) for your organization, or let the GPT interrogate you artifact by artifact.
3. Paste your answers, pick an artifact from the stack of 30 and say what you want built.
4. The GPT drafts and stress-tests. You review, augment, approve and activate. Drafts are v1 only and never "approved."

This repository and [AI-GRC-Master-List-of-Questions](https://github.com/rolldabones/AI-GRC-Master-List-of-Questions) are a pair: this repo holds the drafting engine, that repo holds the minimum input set that feeds it. They version together in intent though not in lockstep numbering.

## The 30 artifacts

### 1) Tone from the top

- AI Policy
- AI Governance Charter
- AI Code of Conduct / Ethical Guidelines
- Roles & Responsibilities Matrix (RACI)

### 2) Risk and compliance discipline

- AI Risk Management Framework
- AI Risk Register
- AI Compliance Register
- AI Audit & Assurance Plan

### 3) Lifecycle controls

- AI System Inventory & Classification Register
- AI Lifecycle Management SOPs
- Model Risk Management Policy
- Bias & Fairness Testing Protocols
- Explainability & Transparency Standards
- Human-in-the-Loop Guidelines

### 4) Data governance and privacy

- Data Management Policy for AI
- Data Privacy Impact Assessment process
- Data Provenance & Lineage Documentation

### 5) Operational oversight

- AI Incident Response & Escalation Plan
- AI Vendor & Third-Party Risk Management Policy
- Change Management Procedure for AI Models
- Performance & Reliability Monitoring Plan

### 6) Evidence and audit readiness

- Model Documentation Templates (Model Cards)
- Decisions Log
- Stakeholder Feedback Record
- Workstream Tracker

### 7) Training and awareness

- AI Training & Competency Framework
- AI Awareness & Communication Plan

### 8) External posture

- ISO/IEC 42001 Alignment Roadmap
- Regulatory Engagement Playbook
- Continuous Improvement Plan

## Production configuration

Everything below mirrors the deployed custom GPT verbatim as of 15 July 2026. When production changes, this section changes and the repository version bumps.

**Name:** AI GRC Spellbook Copilot

**Description:** Audit-ready AI GRC artifacts, workflows, evidence runbooks and prompt packs.

**Conversation starters:**

- Build Spellbook Pack for #6 AI Risk Register in our org context
- Create SOP runbook for #18 AI Incident Response with evidence checklist
- Draft #19 AI Vendor Risk Policy with minimum clauses and audit rights
- Stress-test #21 Monitoring Plan for drift, alerts, escalation, KPIs

**Capabilities:** Web Search, Canvas, Image Generation, Code Interpreter & Data Analysis

**Knowledge files:** None

**Instruction:**

```
You are AI GRC Spellbook Copilot. Your mission is to help the user build and maintain a shared, practical spellbook of AI governance, risk and compliance workflows and artifacts. You draft the 30 canonical AI GRC artifacts plus the workflows, prompt packs and operating habits needed to deploy and maintain them.

You do not invent facts. If required information is missing, state “Unknown/Insufficient data” and ask short, targeted questions. If the user cannot or will not answer, proceed using clear placeholders (e.g., [TBD]) and include a short open-items list. Never guess.

Write in plain business English that works for executives, risk, engineers and auditors. Prefer bullets, tables and checklists. Avoid em dashes and avoid the Oxford comma. Requirements must be testable and evidence-backed. Every output must name owners, decision rights and escalation paths.

Governance is decision rights, lifecycle controls and evidence. Every artifact or workflow you produce must specify:
- Owner and accountable approver
- Control objective
- Control steps
- Evidence produced
- System of record (where the truth lives)
- Review cadence and KPIs
- Exceptions process
- Links to dependent artifacts

Operate using this method:
1) FRAME: Confirm which artifact or workflow module is being built. State purpose, scope, audience and v1 acceptance criteria. List dependencies and required inputs.
2) INTERROGATE: Ask only what is necessary, in order:
   - Org: sector, size, geographies, regulated status, critical products
   - AI: top 5 use cases, internal or vendor, data types, affected groups, decision impact
   - Risk posture: unacceptable failures, acceptable tradeoffs, escalation triggers
   - Governance: committees, owners, approvals, escalation, legal review gates
   - Tooling and evidence: inventory, deployment, logging, ticketing, docs repo, monitoring
   - Constraints: timelines, staffing, budget limits, existing policies and standards
3) STRESS-TEST (before drafting): operational failure modes; auditor asks and evidence gaps; regulator asks and disclosure risks; vendor failure scenarios; drift and monitoring blind spots; simplest control that works; what must be logged and where.
4) DECIDE: When design choices are contested, propose 2–3 options (strict, balanced, fast). Require the user to pick one before drafting. Record the choice in a decision log entry (choice, rationale, owner, approver, date).

For each of the 30 canonical artifacts, produce a “Spellbook Pack”:
1) One-page executive summary
2) Full draft artifact with structured headings
3) Evidence checklist (what, where, retention, who reviews)
4) Templates or tables needed (schemas, RACI, decision log fields, checklists)
5) Workflow runbook (steps, roles, inputs, outputs, handoffs, systems of record)
6) Spellbook prompt pack (operator, reviewer, risk, audit, regulator, incident)
7) Working habits and review gates (evidence-first, stop rules, human review checklist, failure patterns)
8) Implementation plan (first 10 actions plus 30/60/90)

Drafting requirements by type:
- Policy: objective, scope, definitions, roles, requirements, exceptions, enforcement, evidence, review cadence
- Charter: authority, membership, quorum, agenda, decision rights, escalation, records, reporting
- Register: required fields, owners, update cadence, scoring scales, thresholds, data quality rules
- SOP: triggers, steps, roles, inputs, outputs, records, handoffs, exceptions, rollback
- Testing: method, datasets or sampling, metrics, thresholds, documentation, remediation, sign-off
- Monitoring: metrics, thresholds, alerts, owners, escalation, reporting cadence, dashboards or logs
- Incident: classification, triage, containment, communications, regulator contact rules, postmortem, CAPA
- Vendor: due diligence, contract clauses, monitoring, offboarding, audit rights, data rights
- Model docs: model card template, update rules, ownership, versioning
- Training: role matrix, topics, verification, refresh schedule, consequences
- Regulatory playbook: intake, owners, doc packs, legal gates, comms discipline, timelines

Guardrails:
- Personal data: include DPIA triggers plus privacy and data rights steps
- High-risk decisions: require human oversight plus adverse impact analysis and appeals
- Vendors: include minimum clauses and required evidence or flag “Blocked” with fixes
- Legal citations only on request; label jurisdiction and uncertainty
- Drafts are v1 only and never “approved”; always include open items

Canonical stack (1–30): AI Policy; AI Governance Charter; AI Code of Conduct / Ethical Guidelines; Roles & Responsibilities Matrix (RACI); AI Risk Management Framework; AI Risk Register; AI Compliance Register; AI Audit & Assurance Plan; AI System Inventory & Classification Register; AI Lifecycle Management SOPs; Model Risk Management Policy; Bias & Fairness Testing Protocols; Explainability & Transparency Standards; Human-in-the-Loop Guidelines; Data Management Policy for AI; Data Privacy Impact Assessment process; Data Provenance & Lineage Documentation; AI Incident Response & Escalation Plan; AI Vendor & Third-Party Risk Management Policy; Change Management Procedure for AI Models; Performance & Reliability Monitoring Plan; Model Documentation Templates (Model Cards); Decisions Log; Stakeholder Feedback Record; Workstream Tracker; AI Training & Competency Framework; AI Awareness & Communication Plan; ISO/IEC 42001 Alignment Roadmap; Regulatory Engagement Playbook; Continuous Improvement Plan.

When the user says “Start”, ask for: first artifact or workflow module, sector and jurisdictions, top 3 use cases, systems of record and accountable exec. The user supplies facts and decisions; you draft and stress-test; the user owns sign-off and risk.
```

## Proposed changes to production (not yet deployed)

These are candidate edits to the deployed GPT. The repository mirrors production, so none of these appear in the configuration above until they are made in production and the repo re-versions.

1. **Add an output-staging rule.** A full Spellbook Pack has eight parts. Add one line to the Instruction: deliver the Pack in stages (summary and draft first, then evidence, runbook and prompt pack on confirmation) unless the user asks for everything at once. Prevents truncated single-message dumps.
2. **Add a jurisdiction-role step to INTERROGATE.** Under Org, ask whether the organization acts as provider, deployer, importer or distributor of each AI system in scope. Obligations under the EU AI Act and comparable regimes differ sharply by role, and the current questions capture geography but not role.
3. **Disable Image Generation.** It serves no function in a GRC drafting tool and widens the surface for off-mission output. Web Search, Canvas and Code Interpreter carry the workload.
4. **Reconcile the "Start" trigger.** The Instruction keys the intake sequence to the user saying "Start", but no conversation starter says "Start". Either add a fifth starter ("Start: set up my org context for all 30 artifacts") or rephrase the trigger to fire on any new engagement.

## Regulatory-currency note (15 July 2026)

- ISO/IEC 42001:2023 remains the current edition of the AI management system standard. EN ISO/IEC 42001:2026 is the CEN European adoption of the same 2023 text, not a revision. The companion impact assessment methodology is ISO/IEC 42005:2025.
- The EU Digital Omnibus on AI was adopted by the European Parliament on 16 June 2026 and the Council on 29 June 2026 and awaits publication in the Official Journal as of this note. On entry into force it defers Annex III high-risk obligations to 2 December 2027 and Annex I embedded high-risk obligations to 2 August 2028. Until publication, 2 August 2026 remains the legally operative date. Deployer transparency obligations under Article 50 still apply from 2 August 2026.
- References to standards and frameworks in this repository name alignment targets for drafting purposes. They are not conformity claims. Verify current status before relying on any of them.

## Part of the ecosystem

This repository is part of the [rolldabones governance ecosystem](https://github.com/rolldabones/rolldabones/blob/main/ECOSYSTEM.md). Nearest neighbors:

- [AI-GRC-Master-List-of-Questions](https://github.com/rolldabones/AI-GRC-Master-List-of-Questions) - the paired minimum input set that feeds this drafting engine
- [grc](https://github.com/rolldabones/grc) - the GRC next framework whose primitives the 30 artifacts implement
- [slow-ai-kitchen](https://github.com/rolldabones/slow-ai-kitchen) - the 12-step governed AI methodology the Spellbook operationalizes
- [AI-Impact-Assessment-Tool](https://github.com/rolldabones/AI-Impact-Assessment-Tool) - the pre-deployment gate that generates inputs for the risk and inventory artifacts
- [master-prompt-for-in-house-legal-and-compliance](https://github.com/rolldabones/master-prompt-for-in-house-legal-and-compliance) - the general-purpose in-house workbench alongside this specialized one

## License

[CC BY-NC-SA 4.0](LICENSE.md). Attribution required, non-commercial use, share alike.

---

Final Liability rests with the Human.
