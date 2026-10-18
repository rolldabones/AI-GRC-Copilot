# ai-grc-copilot C9

**Tested model:** claude-opus-5-5 · **Scorer:** claude-sonnet-5-5 (LLM scoring, developer testing, not independent assurance) · **Run:** 2026-10-18 10:12 KST · **max_tokens:** 16000

**Rule:** "For each of the 30 canonical artifacts, produce a “Spellbook Pack”" (eight parts: one-page executive summary; full draft artifact; evidence checklist; templates or tables; workflow runbook; Spellbook prompt pack; working habits and review gates; implementation plan)

**Pass condition:** All eight parts appear, or the instrument says which parts are deferred and why.

## Transcript

### Turn 1, user

Build the full Spellbook Pack for #23 Decisions Log for Harrowgate Freight. Facts (fictional company): Harrowgate Freight Ltd, a road and rail freight forwarder with 640 staff and offices in the United Kingdom and Germany; not a regulated financial entity. Top 5 AI use cases: (1) route optimization, built in-house; (2) a customer-service chatbot from the vendor Quillon AI; (3) invoice data extraction from the vendor Ledgerline; (4) driver-fatigue camera alerts from the vendor Vigilo, which processes in-cab video of drivers; (5) demand forecasting, built in-house. Systems of record: ServiceNow for tickets and the risk register, SharePoint for policies, Jira for model changes, Datadog for monitoring. Accountable executive: the Chief Operating Officer. Governance today: a monthly AI steering group chaired by the COO; Legal reviews every new AI vendor contract. Constraints: a two-person risk team; the governance program starts next quarter. Proceed on the facts given; where a design choice is contested, use the balanced option and record it; record anything missing as an open item.

### Turn 1, assistant (stop_reason max_tokens)

# Spellbook Pack #23: AI Decisions Log
**Organisation:** Harrowgate Freight Ltd (fictional)
**Version:** v1 DRAFT. Not approved. Sign-off and risk ownership sit with Harrowgate Freight.
**Prepared for:** Chief Operating Officer (accountable executive), AI Steering Group, Risk team, Legal, Engineering, Internal or external auditors

---

## 0. Frame, Interrogate, Stress-Test, Decide

### 0.1 Frame

| Item | Content |
|---|---|
| **Module** | #23 AI Decisions Log (register plus operating workflow) |
| **Purpose** | Create one trusted record of every material decision about Harrowgate's AI systems: who decided, under what authority, on what evidence, with what conditions and when it will be revisited |
| **In scope** | Governance decisions about AI systems: go-live, vendor onboarding and renewal, risk acceptance, policy exceptions, material changes, threshold changes, incident decisions, regulatory engagement, retirement and decisions about the governance programme itself |
| **Out of scope** | Runtime outputs of AI systems, such as individual route recommendations or fatigue alerts. These belong to #21 Performance and Reliability Monitoring and #14 Human-in-the-Loop Guidelines. Routine Tier 3 changes are recorded in Jira or ServiceNow and link back to a parent decision |
| **Audience** | COO, steering group members, AI system owners, Risk, Legal, Privacy, Engineering, auditors |
| **Systems in play** | ServiceNow (log and risk register), SharePoint (policies, minutes, supporting documents), Jira (model changes), Datadog (monitoring evidence) |

**v1 acceptance criteria:**
1. Mandatory field schema defined and buildable in ServiceNow.
2. Decision tiers and decision rights defined, with a named accountable approver role per tier.
3. Escalation path defined for every failure point.
4. Exceptions process defined.
5. Evidence checklist with system of record per item. Retention marked [TBD] pending Legal.
6. A baseline entry template for each of the 5 current AI systems.
7. KPIs with proposed targets and a review cadence.
8. All contested design choices recorded as decision log entries.
9. Open items list complete.

**Dependencies:** See Section 2.10. Most upstream artifacts do not exist yet. This pack includes interim rules so the log can operate before they do.

### 0.2 Interrogate: status of required inputs

You asked me to proceed on the facts given. Items below marked **Unknown/Insufficient data** are carried as open items (Section 9). They are not guessed.

| Area | Known | Unknown/Insufficient data |
|---|---|---|
| Org | Freight forwarder, 640 staff, UK and Germany, not a regulated financial entity | Board reporting line for AI. Whether internal audit exists. Whether a German works council exists |
| AI | 5 use cases, build or vendor status, Vigilo processes in-cab driver video | Whether each system is live, piloting or planned. Data types for the chatbot, invoices, routing and forecasting. Whether Vigilo alerts are used in any disciplinary or employment decision |
| Risk posture | None stated | Risk appetite, scoring scale and acceptance thresholds (needed from #5) |
| Governance | Monthly AI steering group chaired by the COO. Legal reviews every new AI vendor contract | Steering group membership, quorum and terms of reference (#2). Named DPO or privacy lead. Whether Legal reviews renewals and amendments as well as new contracts |
| Tooling | ServiceNow, SharePoint, Jira, Datadog | Whether a ServiceNow GRC module is licensed. ServiceNow admin capacity. Whether an AI system inventory exists (#9) |
| Constraints | Two-person risk team. Programme starts next quarter | Budget. Exact programme start date. Existing policies |

### 0.3 Stress-test (before drafting)

| Lens | Finding | Design response in this pack |
|---|---|---|
| **Operational failure modes** | Decisions get made in Teams, email or corridors and never logged | Monthly reconciliation of Jira, ServiceNow, Legal contract reviews and steering minutes against the log. Late-entry rule |
| | Log becomes a graveyard of stale approvals | Mandatory review dates. Risk acceptances and exceptions expire automatically |
| | Two-person risk team becomes a bottleneck | Tiering keeps routine changes out of the log. System owners draft entries. Risk only checks completeness |
| | Tier gaming: proposers downgrade a decision to avoid the steering group | Risk Lead sets the final tier. Disputes escalate to the COO |
| | Backfill invents rationale after the fact | Rule: unknown historical rationale is recorded as "Unknown". It is never reconstructed |
| | Broken evidence links from SharePoint permission changes or moved files | Quarterly link-validity sampling. Evidence stored in a controlled SharePoint library with locked structure |
| | Duplication with the risk register | The log records the decision. The risk register records the risk. Both cross-reference by ID |
| **Auditor asks** | "Show me who approved Vigilo go-live and whether they had authority" | Approver role and authority source are mandatory fields. Approval is captured in the ServiceNow audit trail |
| | "How do you know the log is complete?" | Monthly reconciliation evidence (Section 3) |
| | "Can entries be changed after approval?" | Entries lock on approval. Substantive change requires a superseding entry. Edit history is retained |
| | "Give me the population for sampling" | ServiceNow report of all entries by tier, status and date |
| **Regulator asks** (data protection authorities in the UK or Germany, uncertain which would lead) | "Why did you decide to process in-cab video, and what safeguards did you require?" | Personal data, DPIA reference and high-impact flags are mandatory. Personal data entries cannot be approved while the DPIA status is "Unknown" |
| | **Disclosure risk:** candid free-text rationale is discoverable | Writing standard: factual, evidence-referenced, no speculation. Privileged legal advice is held by Legal. The log carries only a restricted reference |
| **Vendor failure scenarios** | Quillon changes its underlying model without notice. Ledgerline extraction accuracy degrades. Vigilo has a breach or adds subprocessors | Vendor-triggered changes are Tier 1 or Tier 2 decisions (continue, restrict, suspend or exit). Vendor decisions without Legal review evidence are set to **Blocked** |
| **Drift and monitoring blind spots** | Datadog alert thresholds changed silently, so conditions on an approval become meaningless | Threshold changes on any Tier 1 system are Tier 2 decisions. Approval conditions reference specific Datadog monitors |
| **Simplest control that works** | One ServiceNow table, mandatory fields, one approval workflow, monthly reconciliation, quarterly QA sample | Adopted as the balanced design |
| **What must be logged and where** | See tier matrix (Section 4.2) and evidence checklist (Section 3) | |

### 0.4 Decide: contested design choices

Per your instruction, the **balanced** option is selected each time. Each choice is recorded below as a decision log entry. These become the first real entries in the log once it is built.

| ID | Question | Strict | **Balanced (selected)** | Fast |
|---|---|---|---|---|
| D-01 | System of record | Dedicated GRC module with immutable records | **ServiceNow custom table with approval workflow and audit history. Documents in SharePoint, linked by URL** | SharePoint list |
| D-02 | Logging scope | Every AI decision, including routine changes | **Tier 1 and Tier 2 in the log. Tier 3 stays in Jira or ServiceNow with a mandatory parent decision ID** | Steering group decisions only |
| D-03 | Amendment rule | No edits after approval. Every correction needs a new entry | **Locked on approval. The administrator may correct clerical errors with a recorded reason. Substantive change needs a superseding entry** | Editable with history |
| D-04 | Backfill of existing systems | Full evidenced reconstruction of all historical decisions | **One retrospective baseline entry per in-use system. Unknowns recorded as Unknown. Forward ratification decision within 90 days** | No backfill. Log forward only |
| D-05 | Review cadence | All entries reviewed annually, plus Tier 1 quarterly | **Tier 1 review date of 12 months or less. Risk acceptances expire at 12 months or less. Exceptions expire at 90 days or less. Tier 2 reviewed at 12 months or on trigger** | Review on trigger only |
| D-06 | Urgent decisions between monthly meetings | No urgent route. Convene an extraordinary meeting | **COO may decide alone. Entry logged within 2 business days. Ratified at the next steering group** | System owner decides |

**Decision log entries (meta):**

| ID | Choice | Rationale | Owner | Approver | Date | Status |
|---|---|---|---|---|---|---|
| D-01 | ServiceNow custom table plus SharePoint evidence | Uses the existing ticketing and risk register platform. Keeps the audit trail. Avoids new licence cost (GRC module licensing Unknown) | Risk Lead [TBD name] | COO | [TBD] | Proposed |
| D-02 | Tiered scope (Tier 1 and 2 logged, Tier 3 linked) | A two-person team cannot curate every change. Traceability is preserved through the parent ID | Risk Lead [TBD] | COO | [TBD] | Proposed |
| D-03 | Lock on approval. Clerical fixes allowed. Supersede for substance | Gives auditors integrity without blocking typo fixes | Risk Lead [TBD] | COO | [TBD] | Proposed |
| D-04 | Baseline retrospective entries plus ratification within 90 days | Covers live systems quickly without fabricating history | Risk Lead [TBD] | COO | [TBD] | Proposed |
| D-05 | Expiry and review dates by tier and type | Prevents stale approvals at low effort | Risk Lead [TBD] | COO | [TBD] | Proposed |
| D-06 | COO urgent authority with 2-day logging and ratification | Monthly cadence is too slow for incidents. Ratification keeps the steering group in control | Risk Lead [TBD] | COO, ratified by steering group | [TBD] | Proposed |

---

## 1. One-Page Executive Summary

**What this is:** A single record in ServiceNow of every material decision Harrowgate makes about its AI systems. It shows who decided, under what authority, on what evidence, with what conditions and when the decision will be revisited.

**Why it matters for Harrowgate:**
- **Vigilo** processes in-cab video of drivers in the UK and Germany. If a regulator, employee or driver representative asks why and on what safeguards, the answer must exist in writing, dated and approved.
- **Three vendors** (Quillon AI, Ledgerline, Vigilo) can change their models without notice. Decisions to continue, restrict or exit must be traceable.
- **Two in-house models** (route optimisation and demand forecasting) change through Jira. Each change must trace to an approved decision.
- **Today** governance decisions live in steering group discussion and Legal contract reviews. Nothing proves completeness.

**How it works:**
- **Tier 1** (steering group or COO approves): go-live, new vendors, risk acceptance, policy exceptions, any use of AI output in decisions about individuals, retirement, major incidents and regulator contact.
- **Tier 2** (Risk Lead approves): moderate changes, threshold changes, short exceptions and risk acceptance within appetite.
- **Tier 3** (not in the log): routine changes in Jira or ServiceNow. Each must reference a parent decision ID.
- Entries lock on approval. Changes need a superseding entry. Risk acceptances expire within 12 months and exceptions within 90 days.
- A monthly reconciliation checks Jira, ServiceNow, Legal reviews and minutes against the log.

**Decisions needed from the COO:** Approve D-01 to D-06. Name the Risk Lead as Log Owner. Name an owner for each of the 5 AI systems. Confirm the privacy lead or DPO.

**Effort:** Estimated build of 3 to 5 ServiceNow admin days (Unknown: admin capacity, so open item OI-03). About 2 to 4 hours per month of Risk Analyst time once running.

**Top risks if not done:** No defensible record for driver video processing. Stale or unauthorised approvals. Audit findings on completeness and authority.

**Key open items:** Retention period (Legal). Whether Vigilo alerts feed disciplinary decisions. Works council consultation in Germany (uncertain, Legal to confirm). Risk appetite thresholds. Live status of each system.

---

## 2. Full Draft Artifact: AI Decisions Log Standard (Register)

### 2.1 Owner and accountable approver
- **Artifact owner (Log Owner):** Risk Lead [TBD name]
- **Log Administrator:** Risk Analyst [TBD name]. Must not approve entries, to keep duties separate
- **Accountable approver of this standard:** COO
- **Ratifying body:** AI Steering Group

### 2.2 Control objective
Every material AI governance decision at Harrowgate is:
- recorded completely and on time
- approved by a person or forum with documented authority
- traceable to supporting evidence
- linked to affected systems, risks and changes
- revisited by a set date

This lets Harrowgate show any reviewer what was decided, by whom, why and on what evidence.

### 2.3 Definitions

| Term | Definition |
|---|---|
| Decision | A choice that commits Harrowgate to a course of action on an AI system, vendor, risk, policy or governance process |
| Decision ID | Unique identifier in the format DEC-YYYY-NNN |
| Decision owner | The person who proposes the decision and is responsible for its conditions |
| Accountable approver | The person or forum with authority to make the decision under Section 2.5 |
| Condition | A requirement attached to an approval, with an owner and a due date |
| Superseding entry | A new entry that replaces an earlier decision. The earlier entry stays visible with status "Superseded" |
| Retrospective entry | An entry recording a decision made before the log existed |
| High-impact flag | Set when an AI output may affect an individual's employment, discipline, pay, safety or access to service |

### 2.4 Required fields (schema)

M = mandatory at approval. C = conditional.

| # | Field | Type | Rule | M/C |
|---|---|---|---|---|
| 1 | Decision ID | Auto | DEC-YYYY-NNN | M |
| 2 | Title | Text, 120 characters max | Starts with a verb, e.g. "Approve go-live of..." | M |
| 3 | Tier | 1 or 2 | Set by Risk Lead. Disputes escalate per Section 2.8 | M |
| 4 | Decision type | Picklist | Go-live. Vendor onboard or renew. Material change. Threshold change. Risk acceptance. Policy exception. Incident decision. Regulatory engagement. Retirement or exit. Governance design | M |
| 5 | AI system(s) | Reference | Inventory ID from #9. Interim: system name from Section 4.6 | M |
| 6 | Lifecycle stage | Picklist | Idea, Design, Build, Test, Pilot, Live, Change, Retire | M |
| 7 | Decision statement | Text | The question being decided, in one sentence | M |
| 8 | Options considered | Text | At least 2 options for Tier 1, including "do nothing" where relevant | M for Tier 1 |
| 9 | Decision made | Text | The chosen option, stated exactly | M |
| 10 | Rationale | Text | Factual. References evidence. No speculation | M |
| 11 | Risks accepted | Reference | ServiceNow risk register IDs (#6) | C: if risk is accepted |
| 12 | Conditions | Child table | Each condition has an owner, due date and evidence of closure | C |
| 13 | Personal data involved | Yes, No, Unknown | "Unknown" blocks approval | M |
| 14 | DPIA status and reference | Picklist plus link | Not required, Screening done, DPIA in progress, DPIA complete. Link to #16 record | C: if personal data is Yes |
| 15 | High-impact flag | Yes, No, Unknown | "Unknown" blocks approval | M |
| 16 | Human oversight reference | Link | #14 HITL design | C: if high-impact |
| 17 | Adverse impact analysis reference | Link | #12 testing result | C: if high-impact |
| 18 | Appeal or challenge route | Text plus link | How an affected person contests the outcome | C: if high-impact |
| 19 | Vendor | Picklist | Quillon AI, Ledgerline, Vigilo, Other | C |
| 20 | Legal contract review reference | Link | Evidence of Legal review | C: if a vendor is involved |
| 21 | Decision owner | User | Cannot be the same person as the approver | M |
| 22 | Accountable approver | User or forum | Must match Section 2.5 | M |
| 23 | Authority source | Reference | Section of #2 Charter or this standard | M |
| 24 | Forum and meeting reference | Link | Steering group minutes in SharePoint | C: Tier 1 |
| 25 | Quorum met | Yes or No | Per #2 Charter. Interim: [TBD] | C: Tier 1 |
| 26 | Consulted | Multi-select | Legal, Privacy, IT Security, HR, Engineering, Works council [TBD], Vendor management | M |
| 27 | Dissent recorded | Text | Name, role and the substance of any objection | C |
| 28 | Evidence links | Multi-link | SharePoint, Jira, Datadog, ServiceNow | M |
| 29 | Date proposed, decided, effective | Dates | Decided date is the approval timestamp | M |
| 30 | Review or expiry date | Date | Per Section 2.7 | M |
| 31 | Status | Picklist | See Section 2.6 | M |
| 32 | Supersedes or superseded by | Reference | Two-way link | C |
| 33 | Retrospective flag | Yes or No | Yes for backfilled entries | M |
| 34 | Late entry flag | Auto | Set if the entry is created more than 5 business days after the decided date | Auto |
| 35 | Restricted or privileged | Yes or No | Yes: minimal metadata only. Content held by Legal | M |
| 36 | Linked Jira or ServiceNow tickets | Reference | Child Tier 3 changes | C |

### 2.5 Decision rights and segregation

| Decision | Tier | Proposer | Accountable approver | Must consult | Gate |
|---|---|---|---|---|---|
| New AI system go-live | 1 | AI system owner | Steering group (COO chairs) | Risk, Legal, Privacy, IT Security | DPIA complete if personal data. HITL and appeals in place if high-impact |
| New vendor or renewal | 1 | Vendor owner | Steering group | Legal (mandatory), Privacy, IT Security | Legal review evidence or status is **Blocked** |
| Use of AI output in decisions about individuals (e.g. Vigilo in any HR process) | 1 | AI system owner plus HR | Steering group | Legal, Privacy, HR, Works council [TBD] | HITL, adverse impact analysis and appeal route are all mandatory |
| Risk acceptance above appetite | 1 | Risk owner | COO | Risk Lead | Thresholds [TBD from #5] |
| Policy exception (more than 90 days or high-impact) | 1 | Requester | COO | Risk, Legal | |
| Material model change (in-house) | 1 | Engineering lead | Steering group | Risk | Definition of material [TBD from #20] |
| Severity 1 or 2 incident decisions (suspend, notify, restart) | 1 | Incident manager | COO (urgent route) | Legal, Privacy | Regulator contact per #29 |
| Regulator engagement | 1 | Legal | COO | Risk | |
| Retirement or vendor exit | 1 | AI system owner | Steering group | Legal, IT, Privacy (data return or deletion) | |
| Non-material change, threshold change on a Tier 1 system | 2 | AI system owner | Risk Lead | Engineering | |
| Risk acceptance within appetite | 2 | Risk owner | Risk Lead | | |
| Policy exception of 90 days or less, not high-impact | 2 | Requester | Risk Lead | Legal if contractual | |
| Governance programme design choices | 1 | Risk Lead | COO | | |

**Segregation rules:**
- A proposer cannot approve their own decision.
- If the Risk Lead is the proposer of a Tier 2 decision, the COO approves.
- The Log Administrator cannot approve any entry.

### 2.6 Status lifecycle

| Status | Meaning | Who sets it |
|---|---|---|
| Draft | Being written | Proposer |
| Proposed | Complete and submitted for approval | Proposer, after the Administrator's completeness check |
| Blocked | A stop rule is hit (Section 7.2). The fix is stated in the entry | Administrator or Risk Lead |
| Approved | Decision made and entry locked | Approver, via ServiceNow workflow |
| Approved with conditions | Approved. Open conditions are tracked | Approver |
| Rejected | Not approved. Reason recorded | Approver |
| Deferred | Postponed. A revisit date is mandatory | Approver |
| Superseded | Replaced by a newer entry | Administrator, on approval of the new entry |
| Expired | Review or expiry date passed without renewal | Automatic |
| Withdrawn | Proposer withdrew before decision | Proposer |

### 2.7 Review and expiry rules (per D-05)

| Entry type | Maximum period before review or expiry |
|---|---|
| Tier 1 go-live or vendor decision | 12 months, or the vendor renewal date if sooner |
| Risk acceptance | 12 months, then the entry expires |
| Policy exception | 90 days, then the entry expires |
| Tier 2 decisions | 12 months, or on trigger |
| Urgent COO decision | Ratify at the next steering group, otherwise flag for escalation |

**Review triggers:**
- Datadog threshold breach linked to a condition
- Vendor model or subprocessor change notice
- Incident linked to the system
- New or changed legal requirement (#7)
- Stakeholder complaint pattern (#24)

### 2.8 Escalation paths

| Trigger | First escalation | Second escalation | Time limit |
|---|---|---|---|
| Tier dispute | Risk Lead decides | COO | 5 business days |
| Approver unavailable | Delegate named in #2 Charter [TBD] | COO | 10 business days |
| Stop rule hit and proposer disagrees | Risk Lead | COO | 5 business days |
| Legal or Privacy objection recorded as dissent | COO | Board or CEO [TBD, Unknown reporting line] | Next steering group |
| Review overdue | Decision owner | Risk Lead, then COO | Over 30 days overdue goes to COO |
| Condition overdue | Condition owner | Risk Lead, then steering group | Over 30 days overdue goes to the steering group |
| Unlogged decision found in reconciliation | Decision owner (must log within 2 business days) | Risk Lead, then COO | |
| Expired risk acceptance on a live system | Risk Lead | COO decides to renew, restrict or suspend | 5 business days |

### 2.9 Exceptions process (for this standard)
- **Late entry:** a decision logged more than 5 business days after it was made is auto-flagged and reported monthly. More than 3 late entries per quarter from the same owner escalates to the COO.
- **Deviation from schema or tier rules:** must be requested from the Risk Lead. The deviation is itself logged as a Tier 2 decision with a maximum of 90 days.
- **Restricted or privileged decisions:** Legal holds the content. The log keeps ID, title (sanitised), approver, date and the Legal reference. Approval remains mandatory.
- **ServiceNow outage:** decisions are recorded in the SharePoint fallback template (Section 4.7) and migrated within 5 business days of restoration.

### 2.10 Links to dependent artifacts

| Artifact | Relationship | Interim rule while missing |
|---|---|---|
| #1 AI Policy | Mandates use of the log | COO memo mandating the log [OI-10] |
| #2 Governance Charter | Source of authority and quorum | This standard's Section 2.5 applies. Quorum [TBD] |
| #4 RACI | Roles | Section 4.3 of this pack |
| #5 Risk Management Framework | Appetite and thresholds for tiering | Any risk acceptance is Tier 1 until thresholds exist |
| #6 Risk Register (ServiceNow) | Risk IDs referenced | Required where a risk is accepted |
| #7 Compliance Register | Obligations triggering review | Legal flags manually |
| #8 Audit and Assurance Plan | Consumes the log as a sampling population | Quarterly QA sample (Section 3) |
| #9 Inventory | System IDs | Interim system list in Section 4.6 |
| #10 Lifecycle SOPs | Gate decisions produce entries | Go-live is always Tier 1 |
| #12 Bias and Fairness Testing | Adverse impact evidence | Mandatory for high-impact entries |
| #14 HITL Guidelines | Oversight evidence | Mandatory for high-impact entries |
| #16 DPIA process | DPIA reference | Personal data entries Blocked until screening is done |
| #18 Incident Response | Incident decisions | Severity 1 and 2 decisions via the urgent route |
| #19 Vendor Risk Policy | Vendor decisions | Legal review evidence mandatory |
| #20 Change Management | Tier 3 parent links | Jira field "Parent DEC ID" mandatory |
| #21 Monitoring Plan | Conditions tied to Datadog monitors | Threshold changes are Tier 2 |
| #22 Model Cards | Model card version referenced at go-live | Link if available, else open condition |
| #24 Stakeholder Feedback | Review trigger | Manual |
| #25 Workstream Tracker | Implementation actions | Track in ServiceNow project or Jira |
| #28 ISO/IEC 42001 Roadmap | Log is evidence of documented decisions | Note in roadmap |
| #29 Regulatory Playbook | Regulator engagement decisions | Legal decides contact |
| #30 Continuous

## Score

**Verdict: UNSCORABLE.** The pass condition needs all eight Spellbook Pack parts, or an explicit statement of which are deferred and why. Only parts 1 and 2 appear, and part 2 is cut off at the end. Nothing in the text defers the rest. The output stopped at the token limit, so the transcript shows nothing about whether the instrument itself would have produced or deferred parts 3 to 8. The suite rule says a case not exercised is recorded as not run, never as passed, so I mark this case UNSCORABLE and recommend a re-run with a larger output budget or a split into several turns.

---

Final Liability rests with the Human.
