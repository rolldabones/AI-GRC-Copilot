# ai-grc-copilot C14

**Tested model:** claude-opus-5-5 · **Scorer:** claude-sonnet-5-5 (LLM scoring, developer testing, not independent assurance) · **Run:** 2026-10-18 10:14 KST · **max_tokens:** 16000

**Rule:** "Avoid em dashes and avoid the Oxford comma."

**Pass condition:** The output contains no em dash and no serial comma.

## Transcript

### Turn 1, user

Draft #2 AI Governance Charter for Harrowgate Freight. Facts (fictional company): Harrowgate Freight Ltd, a road and rail freight forwarder with 640 staff and offices in the United Kingdom and Germany; not a regulated financial entity. Top 5 AI use cases: (1) route optimization, built in-house; (2) a customer-service chatbot from the vendor Quillon AI; (3) invoice data extraction from the vendor Ledgerline; (4) driver-fatigue camera alerts from the vendor Vigilo, which processes in-cab video of drivers; (5) demand forecasting, built in-house. Systems of record: ServiceNow for tickets and the risk register, SharePoint for policies, Jira for model changes, Datadog for monitoring. Accountable executive: the Chief Operating Officer. Governance today: a monthly AI steering group chaired by the COO; Legal reviews every new AI vendor contract. Constraints: a two-person risk team; the governance program starts next quarter. Proceed on the facts given; where a design choice is contested, use the balanced option and record it; record anything missing as an open item.

### Turn 1, assistant (stop_reason max_tokens)

# Spellbook Pack #2: AI Governance Charter (Harrowgate Freight Ltd)

**Status:** v1 DRAFT (v0.1). Not approved. Sign-off and risk ownership sit with Harrowgate Freight.
**Document ID:** HF-AIG-002 | **Proposed owner:** AI Governance Lead [TBD name] | **Accountable approver:** Chief Operating Officer (COO)

---

## Step 1: FRAME

| Item | Content |
|---|---|
| Module | Artifact #2, AI Governance Charter |
| Purpose | Formalise the existing monthly AI steering group into a chartered committee. Define its authority, decision rights, escalation paths and records. |
| Scope | All AI systems that Harrowgate Freight Ltd builds, buys, configures or uses in the UK and Germany. This includes the 5 named use cases and any future ones. |
| Out of scope | Detailed risk scoring (#5, #6), policy content (#1), vendor due diligence detail (#19), incident procedures (#18). The charter references these but does not replace them. |
| Audience | COO, committee members, system owners, Legal, risk team, internal and external auditors |
| v1 acceptance criteria | (1) Authority, membership, quorum, agenda, decision rights, escalation, records and reporting are all defined. (2) Every decision type has a named approver role. (3) Every record has a system of record. (4) All open items are listed. (5) The COO and Legal have reviewed it, and review comments are logged. |
| Dependencies | #1 AI Policy (grants authority); #4 RACI; #5 Risk Management Framework (tier definitions); #9 Inventory; #16 DPIA process; #18 Incident Plan; #19 Vendor Policy; #20 Change Management; #23 Decisions Log |
| Inputs received | Company profile, 5 use cases, systems of record, accountable exec, current governance, constraints |
| Inputs missing | See Step 2 and the Open Items list |

---

## Step 2: INTERROGATE (known facts vs Unknown/Insufficient data)

You asked me to proceed, so each gap is recorded as a placeholder and an open item rather than a question that blocks the draft.

| Area | Known | Unknown/Insufficient data |
|---|---|---|
| Org | Freight forwarder, 640 staff, UK and Germany, not a regulated financial entity | Legal entity structure (one entity or a German subsidiary?); Board composition; existence of a works council in Germany; whether a Data Protection Officer (DPO) is appointed |
| AI | 5 use cases; 2 in-house, 3 vendor | Deployment status of each (live, pilot or planned); whether Vigilo alerts feed driver discipline or HR records; whether route optimization sets driver hours or shifts; data residency for the vendors |
| Risk posture | None stated | Unacceptable failures; risk appetite; escalation triggers |
| Governance | Monthly steering group chaired by the COO; Legal reviews new AI vendor contracts | Current members; whether decisions are minuted; who owns each AI system; whether Legal reviews renewals and scope changes |
| Tooling | ServiceNow (tickets, risk register), SharePoint (policies), Jira (model changes), Datadog (monitoring) | System of record for the AI inventory; whether Datadog covers the vendor systems; log retention periods |
| Constraints | 2-person risk team; programme starts next quarter | Budget; exact start date; existing policies (information security, data protection, procurement) |

**Short questions to close the highest-value gaps (answer when you can):**
1. Is there a DPO? If not, who leads data protection?
2. Does a works council exist at the German operation?
3. Can a Vigilo alert lead to any action against a driver, such as a warning, removal from duty or an HR record?
4. Which of the 5 systems are live today?
5. Who should escalations above the COO go to: the CEO, the Board or both?

---

## Step 3: STRESS-TEST (before drafting)

| Lens | Finding | Design response in the charter |
|---|---|---|
| Operational failure modes | A monthly cadence is too slow for incidents and urgent vendor changes. The COO chairs, so the COO's absence stalls decisions. A 2-person risk team cannot run the secretariat and the risk work at the same time. | Out-of-cycle and emergency decision paths; a named Chair delegate; a lightweight agenda; Tier 1 decisions delegated out of committee |
| Auditor asks | "Show me who approved this AI system, when, on what evidence." Today there are no defined minutes, decision log or approval criteria. | Mandatory decision log (#23) in ServiceNow; minutes in SharePoint; evidence links required before a decision is valid |
| Regulator and disclosure risk (UK and Germany, Legal to confirm) | In-cab driver video is worker monitoring with personal data and possible sensitive data. The chatbot interacts with customers, so AI disclosure may be expected. Statements to regulators or works councils without Legal review create risk. | DPIA gate for personal data; Legal and DPO quorum rule; comms discipline (no external statements without Legal) linked to #29 |
| Vendor failure scenarios | Quillon, Ledgerline or Vigilo change their model without notice, suffer a breach, use Harrowgate data for training or exit the market. Today Legal reviews contracts, but there is no evidence of minimum AI clauses. | Vendor gate with minimum clauses; "Blocked" status for new scope or renewal until evidence is filed; vendor changes are a standing agenda item |
| Drift and monitoring blind spots | Datadog likely covers in-house systems only. Coverage of vendor systems is Unknown. Model drift in route optimization and demand forecasting may go unseen. | Committee reviews a monitoring coverage report (#21) each quarter; every system without monitoring is tracked as a risk |
| Simplest control that works | One committee, risk-tiered decision rights, one decision log and one exception workflow | Adopted (see the decisions below) |
| What must be logged and where | Decisions, exceptions, escalations, holds, attendance, conflicts of interest and actions | Decisions, exceptions and actions in ServiceNow; minutes, the charter and packs in SharePoint; model changes in Jira; monitoring in Datadog |

**Provisional risk tiers.** These are for committee routing only. #5 and #9 must confirm them.

| Use case | Build or vendor | Key data | Provisional tier | Why |
|---|---|---|---|---|
| (1) Route optimization | In-house | Routes, loads, possibly driver location and hours [Unknown] | Medium; High if it sets driver hours or shifts | Safety and working-time impact [TBD] |
| (2) Customer chatbot | Quillon AI | Customer queries, possibly personal data | Medium | Customer-facing; transparency and accuracy |
| (3) Invoice extraction | Ledgerline | Invoices, supplier and customer financial data | Medium | Financial accuracy; possible personal data of sole traders |
| (4) Driver-fatigue alerts | Vigilo | In-cab video of drivers | **High** | Worker monitoring; safety-critical; possible employment consequences; possible works council rights (Germany, Legal to confirm) |
| (5) Demand forecasting | In-house | Aggregate volumes [assumed non-personal, to be confirmed] | Low | Internal planning; no individual impact if non-personal |

---

## Step 4: DECIDE (balanced options applied and recorded)

Following your instruction, I applied the balanced option to each contested choice. Each one is logged below for COO confirmation.

| # | Design choice | Strict | **Balanced (applied)** | Fast |
|---|---|---|---|---|
| D1 | Committee structure | Committee plus a separate technical review board | **One committee, with Tier 1 decisions delegated to the AI Governance Lead and the System Owner** | The COO decides alone with advisers |
| D2 | Decision method | Unanimous approval | **Consensus. If there is no consensus, the Chair decides and dissent is recorded.** | Chair decides |
| D3 | Control-function challenge | Legal, DPO and Risk hold a veto | **Legal, the DPO and the Risk Lead may place a "Governance Hold" that pauses a decision for up to 10 business days and escalates it above the COO** | Advisory comments only |
| D4 | Decision log system of record | Separate immutable GRC tool | **ServiceNow (existing audit trail, links to the risk register)** | Minutes only |
| D5 | Maximum exception duration | 30 days | **90 days, renewable once with COO approval** | 12 months |
| D6 | Meeting cadence | Fortnightly | **Monthly (retains the current rhythm), plus out-of-cycle meetings on trigger** | Quarterly |

**Decision log entries (#23 format)**

| ID | Choice | Rationale | Owner | Approver | Date | Status |
|---|---|---|---|---|---|---|
| DL-002-01 | D1 Balanced | 2-person risk team; volume does not justify two bodies; delegation keeps low-risk items moving | AI Governance Lead [TBD] | COO | [TBD] | Proposed |
| DL-002-02 | D2 Balanced | Keeps the COO's accountability clear without hiding disagreement | AI Governance Lead [TBD] | COO | [TBD] | Proposed |
| DL-002-03 | D3 Balanced | Gives control functions a real check, especially on driver monitoring, without permanent gridlock | AI Governance Lead [TBD] | COO | [TBD] | Proposed |
| DL-002-04 | D4 Balanced | Reuses an existing tool with history tracking; no new spend | AI Governance Lead [TBD] | COO | [TBD] | Proposed |
| DL-002-05 | D5 Balanced | Long enough to remediate, short enough to prevent permanent exceptions | AI Governance Lead [TBD] | COO | [TBD] | Proposed |
| DL-002-06 | D6 Balanced | Avoids disrupting a working rhythm; triggers cover urgent cases | AI Governance Lead [TBD] | COO | [TBD] | Proposed |

---

# PACK PART 1: One-Page Executive Summary

**What this is:** A charter that turns the existing monthly AI steering group into the **AI Governance Committee (AIGC)**, with defined authority, decision rights and records.

**Why now:** Harrowgate runs 5 AI systems. Three are vendor-supplied and one processes in-cab video of drivers. Today there are no defined approval criteria, no decision log and no escalation path beyond the COO. An auditor, a regulator or a works council could not see who approved what, or on what evidence.

**What changes:**
- **Decision rights by risk tier:** Low-risk decisions are delegated. Medium-risk decisions go to the committee. High-risk decisions need COO approval with a completed DPIA and sign-off from Legal and the DPO.
- **Governance Hold:** Legal, the DPO or the Risk Lead can pause a decision for up to 10 business days and escalate it.
- **One record:** Every decision and exception is logged in ServiceNow. Minutes and packs are kept in SharePoint.
- **Vendor gate:** A vendor AI system cannot expand scope or renew until minimum contract clauses and evidence are on file.
- **Immediate priority:** The Vigilo driver-fatigue system is provisionally High risk. Its DPIA, worker consultation position and any link to driver discipline must be established first.

**Cost:** No new tools. Time required: roughly 2 to 3 days per month from the risk team for the secretariat [estimate, to be validated].

**Decisions needed from the COO:** Confirm DL-002-01 to DL-002-06, name the members and name the escalation route above the COO.

**Top risks if not adopted:** Unapproved driver monitoring; vendor model changes going unnoticed; no audit trail.

---

# PACK PART 2: Full Draft Charter

## HF-AIG-002 AI Governance Committee Charter (v0.1 DRAFT)

### 1. Purpose
1.1 The AI Governance Committee (AIGC) oversees how Harrowgate Freight Ltd selects, builds, deploys, monitors, changes and retires AI systems.
1.2 It makes sure AI use is safe, lawful, fair to affected people (drivers, customers, suppliers and staff) and evidenced.

### 2. Authority
2.1 The AIGC acts under authority delegated by the COO. The COO is the accountable executive for AI. The source of the COO's authority is [TBD: Board resolution or CEO delegation, open item OI-01].
2.2 The AIGC may:
- approve, condition, defer or reject AI systems and material changes within its decision rights (Section 7)
- require any AI system to be paused, pending COO confirmation within 2 business days
- request documents, evidence and attendance from any employee or vendor relationship owner
- approve exceptions within the limits in Section 10
2.3 The AIGC may not:
- approve spending beyond existing budget authority [limit TBD, OI-02]
- override statutory duties of the DPO or Legal
- make external statements to regulators, works councils or the media. These go through #29 Regulatory Engagement Playbook and Legal.
2.4 Where this charter and #1 AI Policy conflict, #1 AI Policy prevails until the conflict is resolved and logged.

### 3. Scope
3.1 In scope: every AI system in #9 Inventory, whether in-house, vendor-supplied, embedded in vendor software or trialled.
3.2 Both jurisdictions are in scope: the UK and Germany. Where requirements differ, the stricter requirement applies unless Legal records otherwise.
3.3 Definition of "AI system": as defined in #1 AI Policy [TBD until #1 is drafted, OI-03].

### 4. Membership

| Role | Title (proposed) | Voting | Name |
|---|---|---|---|
| Chair | COO | Yes | [TBD] |
| Deputy Chair (Chair delegate) | [TBD: e.g. Head of Operations] | Yes | [TBD] |
| AI Governance Lead / Secretary | Risk team lead | Yes | [TBD] |
| Legal | General Counsel or delegate | Yes | [TBD] |
| Data Protection | DPO or data protection lead [Unknown if appointed, OI-04] | Yes | [TBD] |
| Information Security | CISO or Head of IT Security [Unknown if role exists, OI-05] | Yes | [TBD] |
| Data and Engineering | Owner of the in-house models (route optimization, demand forecasting) | Yes | [TBD] |
| HR | Head of HR (driver monitoring, training) | Yes | [TBD] |
| Procurement / Vendor Management | Vendor relationship owner | Yes | [TBD] |
| Germany representative | Senior manager, German operation | Yes | [TBD] |
| Fleet Safety | Head of Fleet Safety [Unknown if role exists] | Advisory | [TBD] |
| Customer Service | Head of Customer Service (chatbot owner) | Advisory | [TBD] |
| Finance | Finance lead (invoice extraction owner) | Advisory | [TBD] |
| Worker representation | Works council liaison [only if a works council exists, OI-06] | Advisory | [TBD] |

4.1 Members are appointed by the COO and recorded in SharePoint.
4.2 Each voting member names one delegate. Delegates count toward quorum and must be recorded in the minutes.
4.3 Members declare conflicts of interest at the start of each meeting. A conflicted member does not vote on that item.
4.4 System owners attend when their system is on the agenda. They do not vote on their own system.

### 5. Quorum
5.1 Standard quorum: Chair or Deputy Chair, plus at least 50% of voting members, including the AI Governance Lead.
5.2 Additional quorum for any item involving personal data: Legal **and** the DPO (or their delegates) must be present.
5.3 Additional quorum for Tier 3 (High) decisions: the COO in person (no delegate), Legal, the DPO, the AI Governance Lead and HR where workers are affected.
5.4 If quorum is not met, the meeting may discuss but not decide. Items carry forward or move to an out-of-cycle meeting.

### 6. Meetings and Agenda
6.1 Cadence: monthly (DL-002-06). The pack is circulated 3 business days before the meeting.
6.2 Out-of-cycle meeting: called by the Chair or the AI Governance Lead within 2 business days of an escalation trigger (Section 9).
6.3 Standing agenda:
1. Quorum, attendance and conflicts of interest
2. Open actions and overdue items
3. Incidents and near misses since the last meeting (#18)
4. Decisions requested (new systems, changes, exceptions)
5. Vendor changes and notices (#19)
6. Monitoring exceptions and drift alerts (#21)
7. Risk register movements, Tier 2 and Tier 3 only (#6)
8. Stakeholder feedback themes (#24)
9. Programme progress (#25)
10. Any other business, then confirmation of decisions and actions

### 7. Decision Rights

| Decision type | Tier 1 (Low) | Tier 2 (Medium) | Tier 3 (High) | Prohibited or outside appetite |
|---|---|---|---|---|
| New AI system or new use case | System Owner + AI Governance Lead approve; reported to the AIGC | AIGC approves | AIGC recommends; COO approves | COO and [CEO/Board, OI-07] decide; default is reject |
| Material change (#20) | System Owner approves; Jira record | AIGC approves | AIGC recommends; COO approves | As above |
| Vendor onboarding, renewal or scope change | Procurement + AI Governance Lead; Legal contract review | AIGC approves after Legal review | COO approves after Legal and DPO sign-off | As above |
| Exception (Section 10) | AI Governance Lead | AIGC | COO | Not permitted |
| Pause or retire a system | System Owner or AI Governance Lead | AIGC | COO (any member may request it) | n/a |
| Risk acceptance | System Owner | AIGC | COO | Not permitted |
| Tier assignment | AI Governance Lead proposes; AIGC confirms Tier 2 and Tier 3 | | | |

7.1 Tier definitions come from #5 Risk Management Framework. Until #5 is approved, the provisional tiers in this pack apply. They must be confirmed at the first AIGC meeting.
7.2 **Mandatory gates.** No decision is valid without the following evidence on file:
- **Personal data:** DPIA screening completed (#16). A full DPIA is required where any trigger is met: worker monitoring; video or biometric data; sensitive data; large-scale processing; automated decisions with significant effect; or new technology applied to people. **The Vigilo system meets the worker-monitoring and video triggers.**
- **Decisions affecting individuals (High-risk):** human oversight design (#14); adverse impact analysis (#12); an appeal route for the affected person; and HR sign-off for workers.
- **Vendors:** minimum clauses and evidence (Section 7.3), or the system is flagged **Blocked**.
- **In-house models:** model card (#22), test results and monitoring plan (#21).
7.3 **Vendor minimum clauses** (detail to sit in #19). Legal confirms each clause is present:

| Clause | Required evidence |
|---|---|
| No use of Harrowgate data to train or improve vendor models without written consent | Contract clause reference |
| Data location and transfer terms (UK and EU) | Contract clause plus the vendor's data map |
| Sub-processor list and change notification | List on file |
| Security standard and breach notification within [TBD] hours | Certificate or report on file; clause reference |
| Advance notice of material model changes | Clause reference |
| Audit or assurance rights (right to audit or receive an independent report) | Clause plus the latest report |
| Performance and accuracy commitments | SLA schedule |
| Documentation sufficient to explain outputs to affected people | Vendor documentation on file |
| Exit: data return and certified deletion | Clause reference |

7.4 **Current vendor status: Unknown.** Legal reviews contracts today, but no evidence of these clauses has been supplied. Until evidence is filed, Quillon AI, Ledgerline and Vigilo are flagged **Blocked for any renewal, scope expansion or new data type**. Existing use continues, pending a review at the first AIGC meeting. Fix: Legal and Procurement complete the clause check within 60 days (see the implementation plan).

### 8. Decision Method
8.1 Decisions are made by consensus. If there is no consensus, the Chair decides. Dissent is recorded by name in the decision log (DL-002-02).
8.2 **Governance Hold** (DL-002-03): Legal, the DPO or the AI Governance Lead may place a hold on any Tier 2 or Tier 3 decision. A hold must:
- state the reason in writing at the meeting or within 1 business day
- be logged in ServiceNow
- pause the decision for up to 10 business days
- escalate to [CEO/Board, OI-07] if it is not resolved between the holder and the COO
8.3 Decisions by email or written procedure are allowed for Tier 1 and Tier 2 items between meetings. They need quorum-equivalent responses within 5 business days and must be ratified in the next minutes.

### 9. Escalation

**Path:** System Owner → AI Governance Lead → AIGC → COO → [CEO / Board, OI-07]

| Trigger | Escalate to | Timeframe |
|---|---|---|
| AI incident rated Severity 1 or 2 (#18) | AI Governance Lead and COO; out-of-cycle AIGC | Same business day; meeting within 2 business days |
| Suspected personal data breach involving AI | DPO and Legal | Immediately; regulator notification timelines per #18 and Legal |
| Vigilo alert error affecting a driver's employment status | HR, DPO and AI Governance Lead | Within 1 business day |
| Vendor notice of a model change, breach or exit | Procurement and AI Governance Lead | Within 2 business days |
| Monitoring threshold breach (#21) not resolved within [TBD] days | AIGC | Next meeting or out-of-cycle |
| Governance Hold not resolved within 10 business days | CEO / Board [OI-07] | Day 11 |
| Regulator, works council or media enquiry about AI | Legal (sole external contact per #29) | Same business day |
| Exception expired without renewal | AIGC | Next meeting; system paused if Tier 3 |

9.1 **Emergency decisions:** where waiting would cause harm, the COO (or Deputy Chair), Legal and the AI Governance Lead may decide jointly. The decision is logged within 1 business day and ratified at the next meeting.

### 10. Exceptions
10.1 Raised as a ServiceNow exception request (template in Part 4).
10.2 Each request must state: the requirement not met; the reason; the risk; compensating controls; the end date; and the remediation plan.
10.3 Maximum duration is 90 days, renewable once with COO approval (DL-002-05). No exceptions are permitted for prohibited uses or for skipping the DPIA where a trigger is met.
10.4 Approvers by tier: see Section 7.
10.5 Open exceptions are reviewed at every meeting.

### 11. Records (systems of record)

| Record | System of record | Retention | Owner |
|---|---|---|---|
| Charter, terms of reference, membership list | SharePoint (AI Governance site) | Life of the charter plus [TBD] years | AI Governance Lead |
| Meeting packs and minutes | SharePoint | [TBD] years (OI-08) | Secretary |
| Decisions Log (#23) | ServiceNow | [TBD] years | AI Governance Lead |
| Exceptions and Governance Holds | ServiceNow | [TBD] years | AI Governance Lead |
| Actions | ServiceNow | [TBD] years | Action owners |
| Risk register entries (#6) | ServiceNow | [TBD] years | Risk owners |
| Model change records (#20) | Jira | [TBD] years | System Owners |
| Monitoring evidence (#21) | Datadog, with exports to SharePoint for meeting packs | [TBD]; check Datadog's native retention | System Owners |
| AI Inventory (#9) | [Unknown, OI-09; proposed: ServiceNow] | [TBD] | AI Governance Lead |

11.1 Minutes record: attendance; quorum; conflicts; each decision with its ServiceNow ID; dissent; holds; and actions with owners and due dates.
11.2 Minutes are issued within 5 business days and approved at the next meeting.

### 12. Reporting
- **Monthly:** the minutes and a decision summary are issued to members.
- **Quarterly:** an AI governance report from the COO to [CEO/Board, OI-07]. It covers: the inventory by tier; Tier 3 status; incidents; open exceptions; vendor status; KPIs; and programme progress.
- **Annually:** a charter effectiveness review, including member feedback and KPI trends.

### 13. Control Specification

| Element | Content |
|---|---|
| Owner | AI Governance Lead [TBD] |
| Accountable approver | COO |
| Control objective | Every AI decision is made by the right authority, on documented evidence, and is recorded and traceable. |
| Control steps | Intake → tier confirmation → evidence gate check → decision at the right level → logging → action tracking → reporting |
| Evidence produced | Minutes, decision log entries, exception records, hold records, attendance, quarterly reports |
| System of record | ServiceNow (decisions, exceptions, actions); SharePoint (charter, minutes, packs) |
| Review cadence | Charter: annually and on trigger. Decisions and actions: monthly. |
| Exceptions | Section 10 |
| Dependent artifacts | #1, #4, #5, #6, #9, #12, #14, #16, #18, #19, #20, #21, #22, #23, #24, #25, #29 |

### 14. KPIs

| KPI | Target (proposed, to be confirmed) | Source |
|---|---|---|
| Meetings that reach quorum | 100% | Minutes |
| Decisions logged in ServiceNow within 5 business days | 100% | ServiceNow |
| Decisions with evidence links attached | 100% | ServiceNow |
| AI systems in the inventory with a named owner and a confirmed tier | 100% by day 90 | Inventory |
| Tier 3 systems with a current DPIA and human oversight design | 100% | ServiceNow / SharePoint |
| Vendor systems with clause evidence complete | 100% by day 60 | SharePoint / ServiceNow |
| Overdue actions | 0 older than 30 days | ServiceNow |
| Exceptions past their end date | 0 | ServiceNow |
| Severity 1 or 2 incidents escalated within the timeframe | 100% | ServiceNow |

### 15. Charter Review
Review annually. Also review on trigger: a new jurisdiction; a new High-risk use case; a material incident; an organisational change; or a material change in law (Legal to advise).

### 16. Approval Block
| Version | Date | Author | Reviewer(s) | Approver | Status |
|---|---|---|---|---|---|
| 0.1 | [TBD] | AI GRC Spellbook Copilot (draft) | Legal, DPO [TBD] | COO | DRAFT, not approved |

---

# PACK PART 3: Evidence Checklist

| Evidence | Where | Retention | Reviewed by | Frequency |
|---|---|---|---|---|
| Signed charter and COO authority source | SharePoint | Life of the charter plus [TBD] | Internal audit [TBD] | Annual |
| Membership list with delegates | SharePoint | [TBD] | AI Governance Lead | Quarterly |
| Meeting packs | SharePoint | [TBD] | Chair | Monthly |
| Minutes with attendance, quorum and conflicts | SharePoint | [TBD] | Members (approval at the next meeting) | Monthly |
| Decision log entries with evidence links | ServiceNow | [TBD] | AI Governance Lead; audit sample | Monthly; audit annual |
| Exception and hold records | ServiceNow | [TBD] | AIGC | Monthly |
| Tier 3 gate evidence (DPIA, human oversight, adverse impact analysis, appeal route) | SharePoint, linked from ServiceNow | [TBD] | DPO, Legal, HR | Per decision |
| Vendor clause check per vendor | SharePoint, linked from ServiceNow | Contract term plus [TBD] | Legal | Per contract event; annual |
| Emergency decision records and ratification | ServiceNow plus minutes | [TBD] | AIGC | Next meeting |
| Quarterly report to [CEO/Board] | SharePoint | [TBD] | COO | Quarterly |
| KPI dashboard | ServiceNow report [TBD] | [TBD] | AI Governance Lead | Monthly |

---

# PACK PART 4: Templates and Tables

### 4.1 RACI (feeds #4)

| Activity | COO | AI Gov Lead | AIGC | Legal | DPO | HR | System Owner | Procurement |
|---|---|---|---|---|---|---|---|---|
| Approve the charter | A | R | C | C | C | I | I | I |
| Confirm tiers | I | R | A | C | C | C | C | I |
| Tier 1 decision | I | A | I | C | C | I | R | I |
| Tier 2 decision | I | R | A | C | C | C | R | C |
| Tier 3 decision | A | R | C | C | C | C | R | C |
| Vendor clause check | I | C | I | A/R | C | I | C | R |
| DPIA | I | C | I | C | A | C | R | I |
| Governance Hold | I | R | I | R | R | I | I | I |
| Emergency decision | A | R | I | R | C | C | C | I |
| Quarterly report | A | R | C | C | C | I | I | I |

### 4.2 Decision Log Fields (ServiceNow, feeds #23)
| Field | Type | Rule |
|---|---|---|
| Decision ID | Auto | Required |
| Date | Date | Required |
| AI system (inventory ID) | Reference | Required |
| Decision type | Choice: new / change / vendor / exception / pause / risk acceptance | Required |
| Tier | Choice: 1 / 2 / 3 | Required |
| Decision | Choice: approve / approve with conditions / defer / reject | Required |
| Conditions | Text | Required if "with conditions" |
| Rationale | Text | Required |
| Evidence links | URLs | At least 1 required; gate evidence required for Tier 3 |
| Decision maker(s) | User | Must match the decision rights in Section 7 |
| Dissent | Text | Required if there was no consensus |
| Hold placed | Yes/No plus reference | Required |
| Owner of conditions | User | Required if there are conditions |
| Review date | Date | Required |

### 4.3 Decision Request Form (submitted by the System Owner)
- System name and inventory ID
- Build or vendor; vendor name
- Proposed tier and the reason
- Description of the decision requested
- Personal data involved (Yes/No); DPIA screening reference
- Affected groups (drivers, customers, suppliers, staff, public)
- Can the output affect an individual's job, pay, service or access? (Yes/No)
- Human oversight design reference (#14)
- Test or validation evidence reference
- Monitoring plan reference (#21)
- Vendor clause check reference (#19)
- Risks and proposed controls (#6 reference)
- Requested decision date

### 4.4 Exception Request Fields
Requirement not met; reason; risk description and rating; compensating controls; start and end date (90 days maximum); remediation plan with owner; approver; renewal count (maximum 1).

### 4.5 Minutes Template
Date; attendees and delegates; quorum met (Yes/No, with the specific quorum rules checked); conflicts declared; per item: summary, decision ID, dissent, hold, actions (owner, due date); next meeting date.

### 4.6 Quorum Checklist (per item)
- [ ] Chair or Deputy Chair present
- [ ] At least 50% of voting members present
- [ ] AI Governance Lead present
- [ ] Personal data involved? Legal and DPO present
- [ ] Tier 3? COO in person, plus Legal, DPO, AI Governance Lead and HR (if workers are affected)
- [ ] Conflicted members excluded from the decision

---

# PACK PART 5: Workflow Runbook

**Workflow A: Monthly cycle**

| Step | Role | Input | Output | System | Timing |
|---|---|---|---|---|---|
| 1. Call for items | Secretary | Open actions, requests | Draft agenda | ServiceNow, SharePoint | Day minus 10 |
| 2. Gate check on requests | AI Governance Lead | Decision request forms | Ready / not ready list | ServiceNow | Day minus 5 |
| 3. Pack issued | Secretary | Ready items, monitoring and incident summaries | Meeting pack | SharePoint | Day minus 3 |
| 4. Meeting | Chair | Pack | Decisions, actions, holds | Minutes draft | Day 0 |
| 5. Log decisions | AI Governance Lead | Meeting notes | Decision log entries | ServiceNow | Day plus 5 |
| 6. Issue minutes | Secretary | Notes | Draft minutes | SharePoint | Day plus 5 |
| 7. Hand off actions | Action owners | Decision conditions | Tickets; Jira changes where relevant | ServiceNow, Jira | Day plus 5 |
| 8. Track | AI Governance Lead | Tickets | KPI update | ServiceNow | Ongoing |

**Workflow B: Out-of-cycle or emergency decision**
1. A trigger occurs (Section 9). The System Owner or the incident lead notifies the AI Governance Lead via a ServiceNow ticket.
2. The AI Governance Lead decides: out-of-cycle meeting (within 2 business days) or emergency decision (immediate).
3. For an emergency, the COO (or Deputy), Legal and the AI Governance Lead decide by call or email. The decision is logged within 1 business day.
4. Containment actions are handed to the System Owner, following the #18 incident plan.
5. Ratification goes on the next agenda.

**Workflow C: Governance Hold**
1. The holder states the reason. It is logged in ServiceNow and the 10-business-day clock starts.
2. The holder and the System Owner propose a fix. The COO reviews it.
3. If resolved, the decision proceeds and the resolution is logged. If not, it escalates to [CEO/Board] on day 11.

**Workflow D: Vendor event**
1. Procurement receives a renewal, scope change or vendor notice and logs a ticket.
2. Legal runs the clause check (Section 7.3) and records it in SharePoint, linked from ServiceNow.
3. If any clause or evidence is missing, the status is set to **Blocked**, with a list of fixes and an owner.
4. The decision is routed by tier.

**Handoffs to other artifacts:** incidents to #18; changes to #20 in Jira; risks to #6 in ServiceNow; DPIA to #16; regulator or works council contact to #29.

---

# PACK PART 6: Spellbook Prompt Pack

**Operator (Secretary)**
> "Using the open ServiceNow decision requests, actions and exceptions listed below, build the AIGC agenda in the standard 10-item order. Flag any request missing gate evidence per Charter Section 7.2 as 'Not ready', with the missing item named. Do not mark anything approved."

**Reviewer (committee member)**
> "Review this decision request against Charter Section 7. Confirm: the tier; the correct decision maker; quorum requirements; personal data and DPIA status; human oversight and appeal route (if individuals are affected); vendor clause status. List gaps as 'Unknown/Insufficient data'."

**Risk (AI Governance Lead)**
> "For this AI system, list the failure modes affecting drivers, customers or operations; the risk

## Score

**Verdict: UNSCORABLE.** tested response truncated at max_tokens; No em dash appears anywhere in the response. Every list of three or more items joined by "and" or "or" is written without a comma before the conjunction. Both fail indicators are absent from the visible text, so every element of the pass condition is met.

---

Final Liability rests with the Human.
