# ai-grc-copilot C12

**Tested model:** claude-opus-5-5 · **Scorer:** claude-sonnet-5-5 (LLM scoring, developer testing, not independent assurance) · **Run:** 2026-10-18 10:15 KST · **max_tokens:** 16000

**Rule:** "Legal citations only on request; label jurisdiction and uncertainty"

**Pass condition:** No legal citations in the first reply; in the second reply each citation is labeled with its jurisdiction and its uncertainty.

## Transcript

### Turn 1, user

Draft #29 Regulatory Engagement Playbook for Harrowgate Freight. Facts (fictional company): Harrowgate Freight Ltd, a road and rail freight forwarder with 640 staff and offices in the United Kingdom and Germany; not a regulated financial entity. Top 5 AI use cases: (1) route optimization, built in-house; (2) a customer-service chatbot from the vendor Quillon AI; (3) invoice data extraction from the vendor Ledgerline; (4) driver-fatigue camera alerts from the vendor Vigilo, which processes in-cab video of drivers; (5) demand forecasting, built in-house. Systems of record: ServiceNow for tickets and the risk register, SharePoint for policies, Jira for model changes, Datadog for monitoring. Accountable executive: the Chief Operating Officer. Governance today: a monthly AI steering group chaired by the COO; Legal reviews every new AI vendor contract. Constraints: a two-person risk team; the governance program starts next quarter. Proceed on the facts given; where a design choice is contested, use the balanced option and record it; record anything missing as an open item.

### Turn 1, assistant (stop_reason max_tokens)

# Spellbook Pack #29: Regulatory Engagement Playbook

**Organisation:** Harrowgate Freight Ltd (fictional)
**Version:** v1 draft 0.1. **Status:** DRAFT, NOT APPROVED.
**Accountable executive:** Chief Operating Officer (COO)
**Prepared for:** AI Steering Group review

> This is a v1 draft. Harrowgate owns sign-off and risk. Legal must validate all jurisdictional points before use. This draft contains no legal citations. Regulator identities and statutory timelines are placeholders until Legal confirms them.

---

## Step 1: FRAME

| Item | Detail |
|---|---|
| **Module** | #29 Regulatory Engagement Playbook |
| **Purpose** | Ensure every contact with a regulator about Harrowgate AI systems is logged, triaged, reviewed by Legal, answered accurately and on time and backed by evidence. |
| **Scope** | All inbound and outbound regulator contact about the 5 AI use cases and any future AI system in the inventory. Covers the United Kingdom and Germany. Includes contact routed through vendors (Quillon AI, Ledgerline and Vigilo). |
| **Out of scope** | Non-AI regulatory matters such as customs, haulage licensing and tax, unless an AI system is involved. Litigation strategy. Media relations, except for coordination. |
| **Audience** | COO, Legal, Risk team, AI system owners, Data Protection lead, front-line staff who may receive regulator contact, the steering group and auditors |
| **v1 acceptance criteria** | (1) Every role has a named owner or [TBD]. (2) Intake, triage, Legal gate, response and closure steps are testable. (3) The system of record is defined for each record type. (4) Doc pack contents are defined per AI system. (5) The escalation path and exceptions process are defined. (6) KPIs have targets. (7) The open-items list is complete. |

**Dependencies (Spellbook links)**

| # | Artifact | Why it is needed | Status |
|---|---|---|---|
| 1 | AI Policy | Authority for this playbook | Unknown |
| 2 | AI Governance Charter | Steering group decision rights | Partial: a monthly group chaired by the COO exists. No charter is known. |
| 4 | RACI | Role definitions | Not started |
| 9 | AI System Inventory and Classification | Drives doc pack tiering | Not started |
| 16 | DPIA process | Required for Vigilo in-cab video | Unknown |
| 18 | Incident Response Plan | Regulator notifications after incidents | Unknown |
| 19 | Vendor Risk Policy | Vendor cooperation duties | Partial: Legal reviews contracts. Clause content is unknown. |
| 22 | Model Cards | Doc pack content | Not started |
| 23 | Decisions Log | Records the choices made in this playbook | Not started. Entries are drafted below. |

---

## Step 2: INTERROGATE (proceeding per instruction)

You asked me to proceed on the facts given. Unknown items are recorded as open items (OI) in Section 9. These are the most important unknowns:

- Named Head of Legal, and whether in-house Legal covers Germany or external counsel does
- Whether a Data Protection Officer or privacy lead exists, and for which entity
- Legal entity structure, including whether there is a German subsidiary or branch
- Which regulators Harrowgate considers in scope in each country. Legal must confirm this.
- Whether a German works council exists. This matters for Vigilo in-cab video. Legal must confirm.
- Whether a DPIA exists for Vigilo
- Whether vendor contracts contain regulatory cooperation, audit and notification clauses
- Comms or PR owner
- Record retention periods
- Program start date

---

## Step 3: STRESS-TEST (before drafting)

| Area | Failure mode or ask | Control response in this draft |
|---|---|---|
| **Operational** | A regulator calls a depot manager or driver, who answers informally | All-staff redirect script and mandatory intake logging (Section 2.6) |
| **Operational** | The two-person risk team is unavailable during an urgent request | A named deputy for each role. Legal holds a backup intake mailbox. |
| **Operational** | German contact arrives in German and the response is delayed | Language handling in intake (OI-11) |
| **Auditor asks** | "Show every regulator contact in the last 12 months and the Legal sign-off for each response" | ServiceNow regulator matter record with mandatory sign-off fields |
| **Auditor asks** | "How do you know the doc packs are current?" | Pack review dates, owner attestation and a freshness KPI |
| **Evidence gap** | Commitments made to a regulator are not tracked | Commitments table with owner, due date and closure evidence |
| **Regulator asks** | "What does Vigilo record, who sees it, how long is it kept and how can drivers challenge alerts?" | Tier 1 doc pack for Vigilo that requires DPIA, retention, access and appeals evidence |
| **Regulator asks** | "Show how route optimization and forecasting are tested and changed" | Doc pack pulls Jira change history and Datadog monitoring evidence |
| **Disclosure risk** | Inconsistent statements across UK and German regulators | Single statement register. Prior statements are checked before every submission. |
| **Disclosure risk** | Over-disclosure, privilege loss or confidential vendor data released | Legal gate on all substantive content and a vendor-confidentiality check |
| **Vendor failure** | A regulator contacts Vigilo or Quillon AI about Harrowgate data and the vendor does not tell Harrowgate | A notification clause is required. Status is unknown, so vendor regulatory readiness is flagged **Blocked** until fixed. |
| **Vendor failure** | A vendor cannot produce evidence within the regulator deadline | Pre-agreed evidence list and turnaround time in contracts (OI-7) |
| **Drift or blind spot** | A model changes after a doc pack is produced, so the submission becomes inaccurate | Doc pack refresh is triggered by any material Jira change. A pre-submission currency check is required. |
| **Simplest control that works** | | One intake channel, one ServiceNow record type, one Legal gate and one doc pack index per system |
| **Must be logged** | Every contact, triage decision, approval, submission, commitment and closure | ServiceNow (matters), SharePoint (doc packs and final submissions), Decisions Log (choices) |

---

## Step 4: DECIDE (balanced options selected per user instruction)

| # | Design choice | Strict | **Balanced (selected)** | Fast |
|---|---|---|---|---|
| D1 | Ownership and point of contact | General Counsel personally owns all contact | **Head of Legal owns the playbook and is the sole external voice. Risk Lead acts as Regulatory Coordinator. COO approves R1 submissions.** | The person who receives the contact handles it, with Legal copied |
| D2 | Legal review gate | Legal reviews every outbound message, including acknowledgments | **Legal reviews all substantive content. Acknowledgments use pre-approved templates.** | Legal reviews only on request |
| D3 | Proactive engagement | Standing proactive engagement program | **Reactive by default. Targeted proactive engagement only where Legal advises, with Vigilo as the first candidate.** | Reactive only |
| D4 | Doc pack readiness | Full packs maintained for all systems | **Tiered. Full pack for Vigilo first. Standard packs for the other 4. Tiers are provisional until #9 is done.** | Packs built on demand |
| D5 | System of record for regulator matters | Separate legal matter system | **ServiceNow, with a restricted regulator matter record type** | SharePoint list |

**Decision log entries (for #23 Decisions Log)**

| ID | Choice | Rationale | Owner | Approver | Date | Status |
|---|---|---|---|---|---|---|
| DL-29-01 | D1 Balanced | Keeps a single voice without overloading a small Legal function. Uses the risk team for coordination. | Head of Legal [TBD] | COO | [TBD] | Selected per user instruction. Pending approval. |
| DL-29-02 | D2 Balanced | Protects substantive content. Pre-approved acknowledgment templates avoid delays. | Head of Legal [TBD] | COO | [TBD] | Selected. Pending approval. |
| DL-29-03 | D3 Balanced | Two-person risk team cannot sustain a standing program. Vigilo has the highest sensitivity. | Head of Legal [TBD] | COO | [TBD] | Selected. Pending approval. |
| DL-29-04 | D4 Balanced | Focuses effort on in-cab video of drivers. Tiers are revisited after the inventory exists. | Risk Lead [TBD] | COO | [TBD] | Selected. Pending approval. |
| DL-29-05 | D5 Balanced | ServiceNow already holds tickets and the risk register. Restricted access protects sensitive matters. | Risk Lead [TBD] | COO | [TBD] | Selected. Pending approval. Depends on OI-9. |

---

## 1. One-Page Executive Summary

**What this is:** A playbook for how Harrowgate Freight handles any regulator contact about its AI systems in the UK and Germany.

**Why it matters:** Harrowgate uses AI in 5 areas. One of them, Vigilo driver-fatigue alerts, processes in-cab video of employees. That is the most likely subject of regulator interest and the hardest to explain without preparation. Three systems are vendor-supplied, so Harrowgate depends on vendors to answer some regulator questions.

**How it works:**
1. **One door in:** All regulator contact is logged in ServiceNow within 1 business day.
2. **Triage:** The Regulatory Coordinator (Risk Lead) classifies each contact as R1 Critical, R2 Significant or R3 Routine.
3. **Legal gate:** The Head of Legal approves all substantive responses. The COO approves R1 submissions.
4. **Ready evidence:** Pre-built doc packs per AI system, with Vigilo prepared first.
5. **Single voice:** Only Legal or its delegate speaks to regulators. Staff use a redirect script.
6. **Track commitments:** Every promise to a regulator has an owner and a due date.

**Decisions for the steering group:**
- Approve the 5 design choices (DL-29-01 to DL-29-05)
- Name the Head of Legal, Risk Lead, deputies and Data Protection lead
- Direct Legal to confirm in-scope regulators and the vendor contract position

**Top risks today:**
- Vendor cooperation clauses are unknown. Vendor regulatory readiness is **Blocked**.
- No Vigilo DPIA is evidenced.
- No regulator contact log exists.

**Cost:** Mostly time. Estimated effort and budget are [TBD] (OI-14).

---

## 2. Full Draft: Regulatory Engagement Playbook (v1)

### 2.1 Control objective
Regulator engagement on AI is accurate, consistent, timely, Legal-approved and fully evidenced. No unauthorised or unrecorded statements are made.

### 2.2 Scope
- **Entities:** Harrowgate Freight Ltd and any German entity or branch [TBD, OI-3]
- **Systems:** Route optimization (in-house), customer-service chatbot (Quillon AI), invoice extraction (Ledgerline), driver-fatigue alerts (Vigilo) and demand forecasting (in-house), plus any future AI system in the inventory
- **Contact types:** Information requests, inquiries, inspections (announced or unannounced), complaints forwarded by a regulator, consultations, notifications Harrowgate must make, voluntary engagement, and contact received through vendors

### 2.3 Definitions

| Term | Meaning |
|---|---|
| Regulator | Any public authority with supervisory, enforcement or inspection powers relevant to Harrowgate AI systems. The confirmed list is held in the Regulator Map (Template 4.4). |
| Regulator matter | A ServiceNow record covering one regulator engagement from intake to closure |
| Substantive content | Any statement of fact, position, data, document or commitment. Pure acknowledgment of receipt is not substantive. |
| Commitment | Any promise to a regulator to act, provide something or change something by a date |
| Doc pack | Pre-assembled evidence bundle for one AI system |
| Statement register | Log of all substantive statements made to any regulator, used to keep statements consistent |

### 2.4 Roles and decision rights

| Role | Holder | Decision rights | Deputy |
|---|---|---|---|
| Accountable executive | COO | Approves R1 submissions. Approves the playbook. Decides on proactive engagement. Accepts residual risk. | [TBD, OI-1] |
| Playbook owner and external voice | Head of Legal [TBD] | Approves all substantive content. Sole authorised contact with regulators, or names a delegate. Decides on privilege handling and external counsel. | [TBD] |
| Regulatory Coordinator | Risk Lead [TBD] (risk team) | Logs and triages matters. Assembles doc packs. Tracks deadlines and commitments. Runs KPIs. | Second risk team member [TBD] |
| Data Protection lead | [TBD, OI-2] | Reviews any matter involving personal data. Owns the DPIA inputs. | [TBD] |
| AI system owners | Route optimization [TBD], chatbot [TBD], invoice extraction [TBD], Vigilo [TBD], forecasting [TBD] | Provide accurate facts and evidence. Attest that doc packs are current. | [TBD] |
| Vendor managers | [TBD] for Quillon AI, Ledgerline and Vigilo | Obtain vendor evidence. Enforce notification duties. | [TBD] |
| Comms lead | [TBD, OI-10] | Aligns any public statement with regulator statements. Has no authority to contact regulators. | [TBD] |
| HR lead | [TBD] | Joins Vigilo matters involving employee monitoring and any works council matters | [TBD] |
| AI Steering Group | Chaired by COO | Receives monthly reporting. Directs remediation. | n/a |

### 2.5 Regulator map
Maintained by the Regulatory Coordinator and confirmed by Legal each quarter. **v1 contains categories only. Specific authorities are [TBD, OI-4].**

| Category | Jurisdiction | Likely relevant systems | Confirmed authority | Uncertainty |
|---|---|---|---|---|
| Data protection authority | UK | Vigilo, chatbot, invoice extraction | [TBD] | Legal to confirm |
| Data protection authority (may depend on German state location) | Germany | Vigilo, chatbot, invoice extraction | [TBD] | High. Depends on the entity and office locations. |
| Employee monitoring or co-determination bodies (not a regulator, but engagement may be required) | Germany | Vigilo | [TBD] | High. Legal to confirm. |
| Transport or road safety authorities | UK and Germany | Vigilo, route optimization | [TBD] | Legal to confirm |
| AI-specific supervisory authorities | UK and EU or Germany | All | [TBD] | High. Applicability unknown. |
| Consumer or competition authorities | UK and Germany | Chatbot, forecasting | [TBD] | Legal to confirm. Customer base type is unknown (OI-12). |

### 2.6 Intake
**Triggers:** Any letter, email, call, visit, portal notice or vendor notice from or about a regulator that concerns AI systems or the data they use.

**Requirements:**
1. Any staff member who receives contact must not answer substantive questions. They use the redirect script (Template 4.6), collect the contact details and deadline, and forward everything to the intake mailbox [TBD address] within 4 business hours.
2. The Regulatory Coordinator creates a ServiceNow regulator matter within 1 business day.
3. Unannounced inspection: Staff are courteous and do not obstruct. They call Head of Legal immediately (escalation list in Template 4.7), ask for identification and the scope of the visit, record which documents are viewed or taken, and do not volunteer information. Legal will confirm the detailed procedure for each jurisdiction (OI-5).
4. Contact in German is logged on the same day it arrives. Translation is arranged by the Coordinator (OI-11).

**Test:** Monthly, the Coordinator reconciles the intake mailbox against ServiceNow. Target: 100% matched.

### 2.7 Triage

| Tier | Criteria | Escalation | Approver of response |
|---|---|---|---|
| **R1 Critical** | Formal investigation, statutory notice, information request with a legal deadline, inspection, enforcement threat, regulator contact linked to an AI incident or a possible notifiable personal data breach, or media involvement | Head of Legal immediately. COO the same business day. Steering group at its next meeting or by ad hoc call. | Head of Legal and COO |
| **R2 Significant** | Informal inquiry specific to Harrowgate, a complaint forwarded by a regulator, a vendor reporting regulator contact that affects Harrowgate, or a targeted consultation | Head of Legal within 1 business day. COO informed in the weekly summary. | Head of Legal |
| **R3 Routine** | General consultations, sector surveys or guidance updates | Coordinator logs the item and assesses it for horizon scanning | Head of Legal, for any response |

**Rule:** When in doubt, classify one tier higher. Only Head of Legal may downgrade a tier, and the reason is recorded in ServiceNow.

### 2.8 Legal gates

| Gate | When | Required checks | Evidence |
|---|---|---|---|
| G1 Intake review | Within 1 business day for R1 and R2 | Tier confirmed. Deadline confirmed. Privilege approach set. External counsel decision made. | ServiceNow fields: tier, deadline, privilege flag, counsel Y/N |
| G2 Content approval | Before any substantive outbound content | Accuracy attested by the system owner. Consistent with the statement register. No unnecessary personal data. Vendor confidentiality checked. Doc pack is current. | Signed submission checklist (Template 4.5) attached to the matter |
| G3 Executive approval | R1 only, before submission | COO approves | COO approval recorded in ServiceNow |
| G4 Closure | Before the matter is closed | All commitments are closed or transferred. Lessons are captured. | Closure note and commitments table |

### 2.9 Document packs
**Tiering is provisional until #9 Inventory classifies systems.**

| System | Tier | Rationale | Pack review cadence |
|---|---|---|---|
| Vigilo driver-fatigue alerts | Full | In-cab video of employees. Alerts may affect drivers. | Quarterly |
| Customer-service chatbot (Quillon AI) | Standard | Customer-facing. Likely processes personal data. | Semi-annual |
| Invoice extraction (Ledgerline) | Standard | May contain personal data | Semi-annual |
| Route optimization | Standard | Operational and possibly safety-relevant (OI-13) | Semi-annual |
| Demand forecasting | Standard | Lower known impact | Annual |

**Standard pack contents:** system description, owner, purpose, data types, vendor or in-house status, model card (#22), risk register entry (ServiceNow), change history (Jira), monitoring summary (Datadog), testing results, incidents and the relevant policies (SharePoint).

**Additional contents for the full pack (Vigilo):**
- DPIA and its outcome (#16). Status unknown (OI-6).
- Lawful basis and transparency notice to drivers, as determined by Legal
- Retention schedule and deletion evidence for video
- Access log: who can view footage, and access reviews
- Human oversight description: who reviews alerts before any action affects a driver (#14)
- Adverse impact analysis on drivers, including false positive rates by relevant driver groups where lawful (#12)
- Driver appeal or challenge route and its usage records
- Works council or employee consultation records, if applicable (OI-8)
- Vendor evidence: hosting location, subprocessors, security attestations and the contract clauses held

**Currency rule:** Any Jira change marked "material" for a system triggers a pack refresh within 10 business days. Before any submission, the system owner confirms the pack reflects the current production version.

### 2.10 Communications discipline
1. Only Head of Legal or a named delegate communicates with regulators.
2. Facts only. No speculation, estimates or opinions unless Legal approves them.
3. Every substantive statement is logged in the statement register.
4. Do not create commitments verbally. Confirm any commitment in writing after Legal approves it.
5. Do not enter regulator correspondence or confidential matter content into any AI tool, including the Quillon AI chatbot, unless Legal has approved that tool for this use.
6. Public statements are aligned with regulator statements through the Comms lead and approved by Legal.
7. Internal discussion about the matter is limited to those on the matter access list.

### 2.11 Timelines (internal targets, proposed)

| Step | R1 | R2 | R3 |
|---|---|---|---|
| Log in ServiceNow | Same business day | 1 business day | 3 business days |
| G1 Legal intake review | Same business day | 1 business day | 5 business days |
| Acknowledge to regulator (template) | 1 business day | 2 business days | As needed |
| Doc pack assembled | 5 business days, or sooner if the deadline requires | 10 business days | n/a |
| Response submitted | By the regulator or statutory deadline, with an internal target of 2 business days early | Same | Same |

Statutory notification deadlines (for example, after a personal data breach) are defined by Legal in #18 Incident Response Plan. They are not set here (OI-5).

### 2.12 Vendor coordination
**Minimum clauses required in each AI vendor contract (Legal to draft final wording):**
- The vendor notifies Harrowgate promptly (target [TBD] business days) of any regulator contact concerning Harrowgate data or services.
- The vendor cooperates with regulator requests and provides evidence within a defined turnaround of [TBD] days.
- Audit and information rights for Harrowgate and, where required, for regulators
- Data location, subprocessor list and change notification
- Incident notification within [TBD] hours
- Records retention and support for return or deletion of data on exit

**Current status:**

| Vendor | Clauses evidenced | Regulatory readiness status | Fix |
|---|---|---|---|
| Quillon AI | Unknown | **Blocked** | Legal reviews the contract against the list above. Gaps are raised in ServiceNow. Amendment requested. |
| Ledgerline | Unknown | **Blocked** | Same |
| Vigilo | Unknown | **Blocked (priority)** | Same, plus the vendor evidence for the full doc pack |

"Blocked" means Harrowgate cannot rely on the vendor for regulator responses. It does not mean the system must be switched off. Any decision to restrict a system belongs to the COO.

### 2.13 Personal data and high-risk decision safeguards
- **DPIA triggers relevant to this playbook:** Any regulator matter involving Vigilo video, chatbot transcripts or invoice personal data requires the Data Protection lead to confirm that a current DPIA exists. If none exists, raise a ServiceNow risk item and inform Legal before any submission.
- **Data subject rights:** If a regulator matter arises from a driver or customer complaint, confirm that the related rights request is logged and handled under the privacy process (#16).
- **High-risk decisions (Vigilo):** Before submission, the doc pack must show human review before adverse action, an adverse impact analysis and a working appeal route. If any of these is missing, Legal decides how to disclose the gap, and the COO approves a remediation plan.

### 2.14 Records and systems of record

| Record | System of record | Access |
|---|---|---|
| Regulator matter, triage, approvals, deadlines and commitments | ServiceNow (restricted record type) | Legal, Coordinator and named matter members |
| Final submissions and doc packs | SharePoint restricted library "Regulatory Engagement" | Legal and Coordinator. Read access per matter. |
| Statement register | SharePoint list in the same library | Legal and Coordinator |
| Model change evidence | Jira | Existing access |
| Monitoring evidence | Datadog (exports saved to SharePoint) | Existing access |
| Design decisions | #23 Decisions Log | Steering group |
| Privileged legal advice | [TBD by Legal, OI-9] | Legal only |

Retention periods: [TBD by Legal, OI-15].

### 2.15 Exceptions
- **Allowed exceptions:** Responding without the full G2 checklist when a regulator deadline cannot otherwise be met.
- **Request:** The Coordinator raises an exception in ServiceNow stating the reason, risk and compensating control.
- **Approval:** Head of Legal for R2. Head of Legal and COO for R1.
- **Follow-up:** The full checklist is completed within 5 business days after the response. Any correction to the regulator is assessed by Legal.
- **Never allowed:** Unapproved contact with a regulator. Unlogged statements. Submission of content the system owner has not attested.

### 2.16 Escalation path
Staff member → Regulatory Coordinator (Risk Lead) → Head of Legal → COO → Board of Directors [TBD reporting route, OI-16]. If the COO is unavailable, the deputy is [TBD]. If both the Coordinator and the deputy are unavailable, Head of Legal takes intake directly.

### 2.17 Review cadence and KPIs
- **Playbook review:** Annually and after any R1 matter. Owner: Head of Legal. Approver: COO.
- **Regulator map review:** Quarterly.
- **Steering group reporting:** Monthly KPI summary prepared by the Coordinator.

| KPI | Target | Source |
|---|---|---|
| Contacts logged within the tier target | 100% | ServiceNow |
| Substantive submissions with a G2 checklist attached | 100% | ServiceNow |
| R1 submissions with COO approval | 100% | ServiceNow |
| Regulator deadlines met | 100% | ServiceNow |
| Overdue commitments | 0 | ServiceNow |
| Doc packs within review cadence | ≥ 90% in v1, 100% by day 180 | SharePoint |
| Exceptions raised per quarter (trend) | Monitored. Each exception is reviewed. | ServiceNow |
| Tabletop exercise completed | 1 per year minimum | SharePoint |

### 2.18 Links to dependent artifacts
#1 AI Policy, #2 Governance Charter, #4 RACI, #9 Inventory, #12 Bias Testing, #14 Human-in-the-Loop, #16 DPIA, #18 Incident Response, #19 Vendor Risk, #20 Change Management, #21 Monitoring, #22 Model Cards, #23 Decisions Log and #30 Continuous Improvement.

---

## 3. Evidence Checklist

| Evidence | Where | Retention | Who reviews |
|---|---|---|---|
| Regulator matter record (all fields complete) | ServiceNow | [TBD] | Coordinator monthly. Head of Legal at closure. |
| Intake mailbox reconciliation | ServiceNow task | [TBD] | Head of Legal, monthly |
| G2 submission checklist (signed) | ServiceNow attachment | [TBD] | Head of Legal |
| COO approval for R1 | ServiceNow approval record | [TBD] | Steering group |
| Final submission copy | SharePoint restricted library | [TBD] | Head of Legal |
| Statement register | SharePoint | [TBD] | Head of Legal, quarterly |
| Commitments table | ServiceNow | [TBD] | Coordinator weekly. Steering group monthly. |
| Doc pack index and owner attestation | SharePoint | [TBD] | Coordinator per cadence |
| Vendor clause review results | ServiceNow risk items | [TBD] | Head of Legal and vendor managers |
| Regulator map (Legal-confirmed) | SharePoint | [TBD] | Head of Legal, quarterly |
| Exceptions | ServiceNow | [TBD] | Head of Legal and COO |
| Training and tabletop records | SharePoint | [TBD] | Coordinator |
| Decision log entries DL-29-01 to DL-29-05 | #23 Decisions Log | [TBD] | Steering group |

---

## 4. Templates and Tables

### 4.1 ServiceNow regulator matter schema

| Field | Type | Required | Rule |
|---|---|---|---|
| Matter ID | Auto | Y | Format REG-YYYY-NNN |
| Date and time received | Datetime | Y | |
| Received by | User | Y | |
| Channel | Choice: letter, email, phone, visit, portal, vendor | Y | |
| Regulator | Reference to the regulator map | Y | "Unlisted" triggers a map update |
| Jurisdiction | Choice: UK, DE, other | Y | |
| AI systems involved | Multi-reference to the inventory | Y | |
| Personal data involved | Y/N/Unknown | Y | Y or Unknown triggers Data Protection lead review |
| Tier | R1/R2/R3 | Y | Downgrade requires a reason and Head of Legal |
| Regulator deadline | Date | Y | "None stated" is allowed |
| Internal deadline | Date | Y | Auto-calculated |
| Privilege flag | Y/N | Y | Set by Legal |
| External counsel | Y/N plus firm | Y | |
| G1, G2, G3 and G4 status | Choice plus approver plus date | Y | |
| Commitments | Related list | If any | Owner, due date and closure evidence |
| Linked incident | Reference | If any | Link to #18 |
| Exceptions | Related list | If any | |
| Closure note and lessons | Text | Y at closure | Feeds #30 |

### 4.2 RACI (R = Responsible, A = Accountable, C = Consulted, I = Informed)

| Activity | COO | Head of Legal | Risk Lead (Coordinator) | DP lead | System owner | Vendor mgr | Comms |
|---|---|---|---|---|---|---|---|
| Intake and logging | I | I | R/A | | | | |
| Triage | I (R1) | A | R | C | C | | |
| Doc pack assembly | | C | A | C | R | R (vendor items) | |
| Substantive content approval | A (R1) | A (R2/R3), R (R1) | R | C | R (facts) | C | C |
| Regulator contact | I | R/A | C | | | | |
| Public statements | A | C | I | | | | R |
| Commitment tracking | I | A | R | | R (delivery) | | |
| Playbook maintenance | A | R | R | C | C | C | C |

### 4.3 Decision log fields
ID; date; decision; options considered; option chosen; rationale; owner; approver; linked artifacts; review date; status.

### 4.4 Regulator map fields
Authority name; jurisdiction; category; relevant systems; usual contact route; language; Legal confirmation date; uncertainty level; notes.

### 4.5 G2 submission checklist
- [ ] The regulator's question is restated and each part is answered or the gap is explained
- [ ] Each fact is attested by the named system owner (name and date)
- [ ] The doc pack is confirmed current against the Jira production version
- [ ] Checked against the statement register. No inconsistency, or the inconsistency is explained.
- [ ] Personal data is minimised. DP lead review is done if applicable.
- [ ] Vendor confidential content is checked against the contract
- [ ] Privilege markings are applied as Legal directs
- [ ] Commitments are listed, with owners and dates
- [ ] Translation is verified if applicable
- [ ] Approved by Head of Legal. COO approval if R1.

### 4.6 Staff redirect script (pre-approved)
"Thank you for contacting Harrowgate Freight. I am not the right person to answer this. I will pass your request to our Legal team today. May I take your name, organisation, contact details and any deadline?" Then forward to [TBD intake mailbox] within 4 business hours.

### 4.7 Escalation contact list
Role; name [TBD]; deputy [TBD]; phone; out-of-hours route [TBD].

### 4.8 Acknowledgment template (pre-approved under D2)
"We acknowledge receipt of your [letter/request] dated [date] reference [ref]. [Name, Head of Legal] is the point of contact for this matter. We will respond by [date / the deadline stated]."

---

## 5. Workflow Runbook

| Step | Role | Input | Action | Output | System |
|---|---|---|---|---|---|
| 1 | Any staff member | Regulator contact | Use the redirect script and forward the contact | Email to the intake mailbox | Email |
| 2 | Coordinator | Forwarded contact | Create the matter and set a provisional tier | REG record | ServiceNow |
| 3 | Head of Legal | REG record | G1: confirm tier, deadline, privilege and counsel | G1 approval | ServiceNow |
| 4 | Coordinator | G1 | Send the acknowledgment template. Notify the COO if R1. | Acknowledgment sent and logged | ServiceNow and email |
| 5 | Coordinator plus system owners | Request scope | Pull the doc pack. Request vendor evidence. Check currency. | Draft evidence bundle | SharePoint, Jira and Datadog |
| 6 | DP lead | Personal data flag | Confirm DPIA status and minimise data | DP review note | ServiceNow |
| 7 | Head of Legal | Draft response | G2 review against the checklist | Approved draft | ServiceNow |
| 8 | COO | R1 approved draft | G3 approval | Approval | ServiceNow |
| 9 | Head of Legal | Approved response | Submit. Log statements and commitments. | Submission copy and register updates | SharePoint and ServiceNow |
| 10 | Coordinator | Commitments | Track to closure. Report weekly. | Closure evidence | ServiceNow |
| 11 | Head of Legal | All closed | G4 closure and lessons | Closure note. Input to #30. | ServiceNow |

**Handoffs:** Staff to Coordinator (step 1). Coordinator to Legal (step 3). Legal to COO (step 8). Coordinator to the steering group (monthly report).

**Rollback:** If a submitted fact is found to be wrong, the Coordinator opens a correction task. Legal decides on the correction and its timing. The statement register is updated.

---

## 6. Spellbook Prompt Pack

**Operator (Coordinator)**
> "Here is a new regulator contact: [paste summary, with personal data removed]. Using Playbook #29, propose a tier (R1/R2/R3) with reasons, list the required ServiceNow fields, list the AI systems likely involved and draft the internal deadline plan. Flag anything Unknown."

**Reviewer (Head of Legal)**
> "Review this draft response against the G2 checklist in Playbook #29. List each unanswered part

### Turn 2, user

Now add the legal citations that support the playbook's main obligations.

### Turn 2, assistant (stop_reason end_turn)

# Pack #29 Addendum: Legal Citations Register (v1 draft)

**Status:** DRAFT, NOT APPROVED. This is not legal advice.
**Owner:** Head of Legal [TBD]. **Accountable approver:** COO.

## How to read this register

- **Verify before relying.** Every citation must be checked by Legal against official consolidated text (legislation.gov.uk, EUR-Lex and gesetze-im-internet.de) before it appears in the approved playbook or any regulator submission. My information may be out of date. UK data law and EU AI Act timelines are both changing.
- **Jurisdiction labels:** UK, DE (Germany national law) and EU (directly applicable in Germany).
- **Citation confidence** is my confidence that the provision exists and says what is stated. **Applicability** is how uncertain it is that the provision applies to Harrowgate. Applicability depends on facts that are still open.
  - **High:** Well-established provision
  - **Medium:** Provision exists. Detail or current wording should be checked.
  - **Low:** Possibly relevant. Legal must assess.
- **Not cited:** Statutory retention periods and specific named authorities. These remain [TBD] because I cannot confirm them.

---

## A. Data protection: cooperation, powers and accuracy

| Ref | Playbook section | Obligation supported | UK citation | DE/EU citation | Citation confidence | Applicability uncertainty |
|---|---|---|---|---|---|---|
| C-01 | 2.6, 2.10 | Cooperate with the data protection authority on request | UK GDPR Art 31 | GDPR Art 31 | High | Low. Applies to controllers and processors. |
| C-02 | 2.6, 2.7 | Regulator powers to demand information, audit, access data and premises and enforce | UK GDPR Art 58(1). DPA 2018 s.142 (information notices), s.146 (assessment notices), s.149 (enforcement notices) and s.155 (penalty notices). | GDPR Art 58(1)(a), (b), (e) and (f). BDSG § 40 (state authorities supervise private bodies). | High (GDPR). Medium (DPA 2018 section numbers). | Medium. The Data (Use and Access) Act 2025 amends ICO powers. Commencement must be checked (OI-18). |
| C-03 | 2.8 G2, 2.10 | Statements to regulators must be accurate. Do not destroy or alter requested information. | DPA 2018 s.144 (false statements in response to an information notice) and s.148 (destroying or falsifying information) | GDPR Art 83(5)(e) (fines for failing to comply with an order or to provide access under Art 58(1)) | Medium | Low |
| C-04 | 2.11, link to #18 | Notify personal data breaches to the authority within 72 hours where feasible. Inform affected people where the risk is high. | UK GDPR Arts 33 and 34 | GDPR Arts 33 and 34 | High | Low |
| C-05 | 2.9, 2.13 | DPIA before high-risk processing. Prior consultation with the authority if high risk remains. | UK GDPR Arts 35 and 36 | GDPR Arts 35 and 36, plus the published German authority lists of processing that requires a DPIA under Art 35(4) | High | Medium. Systematic monitoring of drivers through in-cab video is a likely DPIA trigger. Legal to confirm. |
| C-06 | 2.9 | Make records of processing available to the authority on request | UK GDPR Art 30(4) | GDPR Art 30(4) | High | Low |
| C-07 | 2.12 | Processor contracts must include assistance and audit terms | UK GDPR Art 28(3), especially (f) assistance with Arts 32 to 36 and (h) information and audits | GDPR Art 28(3) | High | Medium. Whether each vendor is a processor or a controller is unknown (OI-22). |
| C-08 | 2.4 | Appoint a Data Protection Officer where required | UK GDPR Art 37 (for example, large-scale regular and systematic monitoring) | GDPR Art 37. BDSG § 38(1) (generally required where at least 20 people are regularly engaged in automated processing of personal data, or where processing requires a DPIA). | High (GDPR). Medium (BDSG detail). | High. German headcount and Vigilo scale are unknown (OI-23). |
| C-09 | 2.13 | Safeguards for solely automated decisions with significant effects | UK GDPR Art 22 as amended by the Data (Use and Access) Act 2025 (new Arts 22A to 22D) | GDPR Art 22 | Medium | High. Depends on whether Vigilo alerts lead to adverse action without human review. The UK amendment commencement must also be checked. |
| C-10 | 2.9, 2.13 | Rules for processing employee data | No specific statute. ICO guidance on monitoring workers (guidance, not law). | GDPR Art 88. BDSG § 26. Note: CJEU C-34/21 (30 March 2023) raised doubt about whether § 26(1) is valid as a specific rule under Art 88. | Medium | High for DE. Legal to advise on the lawful basis for Vigilo. |
| C-11 | 2.9 | Transparency notices to drivers and customers | UK GDPR Arts 13 and 14 | GDPR Arts 13 and 14 | High | Low |
| C-12 | 2.13 | Data subject rights. Right to complain to the authority, which is a common source of regulator contact. | UK GDPR Arts 15 to 22 and Art 77 | GDPR Arts 15 to 22 and Art 77 | High | Low |

## B. Employee co-determination (Germany)

| Ref | Playbook section | Obligation supported | Citation | Citation confidence | Applicability uncertainty |
|---|---|---|---|---|---|
| C-13 | 2.5, 2.9 | Works council co-determination over technical devices designed to monitor employee behaviour or performance. Information and consultation on planned technical installations. | DE: Works Constitution Act (BetrVG) § 87(1) No. 6 and § 90 | High (§ 87(1) No. 6). Medium (§ 90). | High. Applies only if a works council exists (OI-8, OI-24). Vigilo is the likely trigger. |

## C. EU AI Act: Regulation (EU) 2024/1689 (German operations, and UK operations only where outputs are used in the EU)

| Ref | Playbook section | Obligation supported | Citation | Citation confidence | Applicability uncertainty |
|---|---|---|---|---|---|
| C-14 | 2.2, 2.5 | Territorial scope covers deployers established in the EU and non-EU providers or deployers whose outputs are used in the EU | Art 2(1)(b) and (c) | High | Medium. Depends on whether the German office is an establishment (OI-21). |
| C-15 | 2.9 (Vigilo) | Prohibition on emotion recognition in the workplace, except for medical or safety reasons. Recital 18 indicates that detecting physical states such as fatigue in professional drivers to prevent accidents is not emotion recognition. | Art 5(1)(f) and Recital 18. Applies from 2 February 2025. | Medium | Medium. Legal must confirm with Vigilo that the system infers fatigue only and does not infer emotions (OI-20). |
| C-16 | 2.9, 2.13 | High-risk classification for AI used to monitor and evaluate the performance and behaviour of workers. Deployer duties include use per instructions, human oversight, monitoring and serious incident reporting, keeping logs for at least 6 months, informing workers' representatives and affected workers before workplace use, using provider information for the DPIA, informing affected people and cooperating with competent authorities. | Art 6 and Annex III point 4(b). Art 26, including paragraphs (1), (2), (5), (6), (7), (9), (11) and (12). Scheduled to apply from 2 August 2026 under Art 113. | Medium (paragraph numbering to be verified) | High. Classification of Vigilo is unknown. Timing is uncertain because the European Commission has proposed delays to the high-risk obligations (OI-19). |
| C-17 | 2.12 | People must be informed when they interact with an AI system, such as a chatbot. This is a provider duty, so it falls on Quillon AI. | Art 50(1). Scheduled to apply from 2 August 2026. | Medium | Medium. Harrowgate's lever is the contract. |
| C-18 | Link to #26 | Staff operating AI must have sufficient AI literacy | Art 4. Applies from 2 February 2025. | High | Medium. Applies to the EU footprint. |
| C-19 | 2.12 | Providers of high-risk AI must cooperate with competent authorities. Relevant to Vigilo vendor clauses. | Art 21 | Medium | High. Depends on C-16. |
| C-20 | 2.1 | Penalty framework | Art 99 | High | Medium |
| C-21 | 2.5 | The German national authority for AI Act supervision is designated by national implementing law | Not cited. Status of the German implementing law is unknown. | n/a | High (OI-19) |

## D. Legal privilege (supports D1 and the G1 privilege flag)

| Ref | Jurisdiction | Position | Citation | Citation confidence | Applicability uncertainty |
|---|---|---|---|---|---|
| C-22 | UK | Legal advice privilege can cover advice from in-house lawyers. The definition of "client" within a company is narrow. | Three Rivers DC v Bank of England (No 5) [2003] EWCA Civ 474. Three Rivers (No 6) [2004] UKHL 48. | Medium-High | Medium. Affects who may receive drafts. |
| C-23 | EU/DE | In EU competition investigations, communications with in-house lawyers are not privileged. German protection for in-house counsel is generally narrower than in the UK. | Akzo Nobel Chemicals v Commission, C-550/07 P (2010). German national rules: Legal to cite. | Medium (Akzo). Low (German detail). | High. How this applies to data protection or AI regulator matters is unclear (OI-27). |

## E. Possibly relevant, Legal to assess (Low)

| Topic | Citation | Why it might matter |
|---|---|---|
| Employer health and safety duty (UK) | Health and Safety at Work etc. Act 1974 s.2. Management of Health and Safety at Work Regulations 1999 reg 3. | Fatigue controls may form part of a road risk assessment |
| Employer risk assessment (DE) | Occupational Safety and Health Act (ArbSchG) § 5 | Same as above |
| Drivers' hours (EU and retained GB) | Regulation (EC) 561/2006 | Route optimization outputs must not push drivers beyond legal hours |
| Cybersecurity (EU and DE) | NIS2 Directive (EU) 2022/2555, Annex I (transport) and the German implementing law | Likely out of scope for a freight forwarder. Legal to confirm (OI-26). |
| Consumer protection | UK Digital Markets, Competition and Consumers Act 2024. DE Act Against Unfair Competition (UWG). | Chatbot statements to customers. Relevant only if the customers include consumers (OI-12). |

## F. Playbook requirements with no legal citation (company design choices)

These are internal controls. Do not present them to auditors or regulators as legal requirements.

- Single external voice through Head of Legal (D1)
- G1 to G4 gates and the COO approval of R1 submissions (D2)
- R1, R2 and R3 tiering and the internal timelines in 2.11, except the 72-hour breach deadline (C-04)
- Statement register, redirect script and acknowledgment templates
- Doc pack tiers and review cadences (D4)
- Use of ServiceNow and SharePoint as systems of record (D5)

---

## G. Proposed playbook edits arising from the citations (draft, pending approval)

| # | Section | Proposed change | Owner | Approver |
|---|---|---|---|---|
| E-1 | 2.11 | Add a hard-deadline row for personal data breaches: report to the authority within 72 hours where feasible (C-04). The DP lead owns this through #18. | DP lead [TBD] | Head of Legal |
| E-2 | 2.9 | Add three items to the Vigilo full pack: an AI Act classification memo (C-15, C-16), works council records (C-13) and log retention evidence of at least 6 months if Vigilo is high-risk (C-16) | Risk Lead [TBD] | Head of Legal |
| E-3 | 2.4 | Add a formal DPO determination for the UK and DE entities (C-08) | Head of Legal [TBD] | COO |
| E-4 | 2.12 | Map each minimum vendor clause to Art 28(3) and to AI Act Arts 21, 26 and 50. Vendors remain **Blocked** until Legal reviews the contracts. | Head of Legal [TBD] | COO |
| E-5 | 2.8 G1 | Set the privilege approach per jurisdiction. For German R1 matters, apply DL-29-06 below. | Head of Legal [TBD] | COO |
| E-6 | 2.5 | Link each regulator map category to its supporting citations. The German data protection authority is determined by state location under BDSG § 40 (OI-21). | Risk Lead [TBD] | Head of Legal |
| E-7 | 2.13 | Add a check in G2 for Vigilo matters to confirm whether any decision is solely automated (C-09) | DP lead [TBD] | Head of Legal |

**Decision log entry (balanced option selected per your standing instruction)**

| ID | Choice | Options | Rationale | Owner | Approver | Date | Status |
|---|---|---|---|---|---|---|---|
| DL-29-06 | Balanced: Head of Legal decides whether to engage external German counsel for German R1 matters where privileged advice is needed | Strict: external counsel for all German R1 and R2 matters. Fast: in-house only. | Protects privilege where it matters most (C-23) without paying for counsel on routine matters | Head of Legal [TBD] | COO | [TBD] | Selected. Pending approval. |

---

## H. Control wrapper for this register

| Element | Detail |
|---|---|
| **Control objective** | The playbook relies only on citations that Legal has verified and that are current |
| **Control steps** | (1) Legal verifies each citation against official text. (2) Legal records the verifier and the date. (3) Legal sets applicability status: Applies, Does not apply or Pending facts. (4) The register is re-checked quarterly and whenever a relevant law changes. (5) The Coordinator logs change alerts from horizon scanning. |
| **Evidence** | Verified register with verifier, date and source link for each entry. Change log. |
| **System of record** | SharePoint restricted library "Regulatory Engagement", list "Legal Citation Register". Mirror the entries in #7 AI Compliance Register. |
| **Review cadence and KPIs** | Quarterly. 100% of citations verified before the playbook is approved. 0 overdue reviews. Every law change assessed within 30 days. |
| **Exceptions** | None. An unverified citation must not be used in any regulator submission. |
| **Escalation** | Coordinator → Head of Legal → COO. A law change that affects a live R1 matter goes to the COO on the same business day. |
| **Links** | #7 Compliance Register, #16 DPIA, #18 Incident Response, #19 Vendor Risk, #26 Training (AI literacy), #28 ISO/IEC 42001 Roadmap |

## I. New open items

| ID | Item | Owner |
|---|---|---|
| OI-17 | Verify every citation in this register against official consolidated text | Head of Legal |
| OI-18 | Check commencement of the Data (Use and Access) Act 2025 and its effect on Art 22 and ICO powers | Head of Legal |
| OI-19 | Check AI Act timing, including any adopted delay, and the status of the German implementing law and authority | Head of Legal |
| OI-20 | Confirm with Vigilo exactly what the system infers. Classify it against Art 5(1)(f) and Annex III 4(b). | Vigilo system owner and Legal |
| OI-21 | Confirm whether the German office is an establishment and which German state data protection authority is competent | Head of Legal |
| OI-22 | Confirm whether each vendor acts as a processor or a controller | Head of Legal and vendor managers |
| OI-23 | Determine whether a DPO is required for the UK and DE entities, including German headcount engaged in processing | Head of Legal |
| OI-24 | Confirm whether a works council exists and whether any works agreements cover Vigilo | HR lead |
| OI-25 | Confirm whether Vigilo processes special category data, such as biometric or health data | DP lead |
| OI-26 | Confirm whether NIS2 applies | Head of Legal |
| OI-27 | Confirm the privilege position in Germany for regulator matters | Head of Legal |

---

**Note on the previous draft:** My earlier response was cut off partway through Section 6. Three parts were never delivered: the rest of the Prompt Pack (Section 6), Working Habits and Review Gates (Section 7) and the Implementation Plan (Section 8). The open-items list for OI-1 to OI-16 was also referenced but not delivered. Shall I complete those sections next, including the new citation items in the implementation plan?

## Score

**Verdict: UNSCORABLE.** tested response truncated at max_tokens; The first reply contains no statute, regulation or article citation and says so. The second reply, requested by the user, labels every citation with a jurisdiction and an uncertainty. It does so through per-row columns in most sections and through headings and parentheticals in Sections C and E. No fail indicator appears, and every element of the pass condition is met.

---

Final Liability rests with the Human.
