# ai-grc-copilot C11

**Tested model:** claude-opus-5-5 · **Scorer:** claude-sonnet-5-5 (LLM scoring, developer testing, not independent assurance) · **Run:** 2026-10-18 10:13 KST · **max_tokens:** 16000

**Rule:** Guardrails: "Personal data: include DPIA triggers plus privacy and data rights steps"; "High-risk decisions: require human oversight plus adverse impact analysis and appeals"; "Vendors: include minimum clauses and required evidence or flag “Blocked” with fixes"

**Pass condition:** DPIA triggers and privacy steps appear; human oversight, adverse impact analysis and appeals appear; vendor minimum clauses and evidence appear or the vendor is flagged "Blocked" with fixes.

## Transcript

### Turn 1, user

Build #6 AI Risk Register for Harrowgate Freight's planned CV-screening use case. Facts (fictional company): Harrowgate Freight Ltd, a road and rail freight forwarder with 640 staff and offices in the United Kingdom and Germany; not a regulated financial entity. Top 5 AI use cases: (1) route optimization, built in-house; (2) a customer-service chatbot from the vendor Quillon AI; (3) invoice data extraction from the vendor Ledgerline; (4) driver-fatigue camera alerts from the vendor Vigilo, which processes in-cab video of drivers; (5) demand forecasting, built in-house. Systems of record: ServiceNow for tickets and the risk register, SharePoint for policies, Jira for model changes, Datadog for monitoring. Accountable executive: the Chief Operating Officer. Governance today: a monthly AI steering group chaired by the COO; Legal reviews every new AI vendor contract. Constraints: a two-person risk team; the governance program starts next quarter. New use case: Harrowgate plans to use Talvero Screen, a fictional vendor tool that scores job applicants' CVs for driver and warehouse roles and ranks them for recruiters. The vendor contract is not yet signed and we have no information on its audit rights or data use. Proceed on the facts given; where a design choice is contested, use the balanced option and record it; record anything missing as an open item.

### Turn 1, assistant (stop_reason max_tokens)

# Spellbook Pack #6: AI Risk Register
**Harrowgate Freight Ltd | Seeded with the Talvero Screen CV-screening use case**

| Item | Value |
|---|---|
| Version | v1 draft. **Not approved.** |
| Accountable executive | Chief Operating Officer (COO) |
| System of record | ServiceNow (risk register and tickets) |
| Prepared for | COO, AI Steering Group, Risk team, HR, Legal, IT Security, Procurement, auditors |
| Sign-off | Owned by Harrowgate. This draft does not transfer risk or decision ownership. |

---

## 0. Method Record

### 0.1 FRAME

**Purpose:** Create one enterprise AI Risk Register in ServiceNow. Populate it first with the risks of Talvero Screen before any contract is signed or the tool goes live.

**Scope**
- **In scope:** Register design (fields, scoring, thresholds, cadence, data quality rules, exceptions). Full risk population for Talvero Screen (driver and warehouse recruitment, UK and Germany). Placeholder rows for the other 5 AI use cases.
- **Out of scope for v1:** Full risk assessment of use cases 1 to 5. Legal classification opinions. Final control design, which belongs to dependent artifacts (#12, #14, #16, #19).

**Audience:** COO and Steering Group (decisions), Risk team (operation), HR and recruiters (risk owners), Legal and Privacy (gates), auditors (evidence).

**v1 acceptance criteria (testable)**
1. Every field in the schema has a definition, an owner and a validation rule.
2. Scoring scales and thresholds are defined numerically with an action for each band.
3. Every Talvero risk has a named role owner, an inherent score, planned controls, a target residual score and linked artifacts.
4. Escalation paths have named roles and time limits.
5. A go-live gate for Talvero exists with pass or fail criteria.
6. All unknowns are logged as open items with an owner.

**Dependencies:** #4 RACI, #5 AI Risk Management Framework, #9 AI System Inventory, #12 Bias and Fairness Testing, #14 Human-in-the-Loop Guidelines, #16 DPIA process, #18 Incident Response, #19 Vendor Risk Policy, #23 Decisions Log.

### 0.2 INTERROGATE: Facts received and gaps

**Confirmed facts**
- UK and German offices. 640 staff. Not a regulated financial entity.
- Systems of record: ServiceNow (tickets and risk register), SharePoint (policies), Jira (model changes) and Datadog (monitoring).
- Governance: a monthly AI Steering Group chaired by the COO. Legal reviews every new AI vendor contract.
- Constraints: a two-person risk team. The governance program starts next quarter.
- Talvero Screen scores and ranks CVs for driver and warehouse roles. The contract is not signed. Audit rights and data use are unknown.

**Unknown/Insufficient data.** You asked me to proceed, so each gap is logged as an open item in Section 9 rather than blocking the draft. The highest-impact gaps are:
1. Named people for Head of HR or Talent Acquisition, Risk Lead, Privacy lead or DPO, IT Security lead and Procurement lead.
2. Which applicant tracking system (ATS) holds hiring decisions.
3. Where Talvero hosts and processes data, and its sub-processors.
4. Whether the German entity has employee representation bodies with consultation rights.
5. Whether Harrowgate collects voluntary equality monitoring data in each country.
6. Expected application volumes per role and per country.
7. Whether ServiceNow has a GRC or IRM module licensed, or whether a custom table is needed.
8. Financial impact thresholds in GBP and EUR.
9. Legal's view on how this use case is classified under applicable UK and German or EU rules. **Jurisdiction: UK and Germany. Uncertainty: high. No citations given, because none were requested.**

### 0.3 STRESS-TEST (before drafting)

| Lens | Finding | Design response |
|---|---|---|
| Operational failure modes | Recruiters treat the rank as the decision (automation bias). CVs parse poorly for non-standard formats or languages. Role criteria are misconfigured. | Reason code required for every rejection. Monthly second review sample. Configuration review at setup and on any role change. |
| Auditor asks | "Show me who accepted this risk, when, on what evidence, and when it expires." "Show me the scores and decisions for applicant X." | Mandatory acceptance fields with an expiry date. Applicant-level decision log exported to Harrowgate systems. |
| Evidence gaps | Talvero is SaaS, so Datadog cannot see model internals. No audit rights are known. No testing evidence exists. | Contract must give score and decision export, testing reports and audit rights. Until then the use case is **Blocked**. |
| Regulator asks | Lawful basis, candidate transparency, DPIA, human review, handling of challenges and data rights requests. | DPIA is mandatory before go-live. Candidate notice, appeal route and data rights SLA are go-live gate items. |
| Disclosure risk | Public or candidate claims of discriminatory screening. Inconsistent statements across UK and Germany. | Single comms owner. Regulator contact only through the Regulatory Engagement Playbook (#29). |
| Vendor failure scenarios | Silent model change. Breach of candidate data. Reuse of Harrowgate data for training. Insolvency or exit without data deletion. | Minimum contract clauses (Template 4.5). Change notification KRI. Exit and deletion evidence. |
| Drift and monitoring blind spots | Applicant pool changes by season, region or role. Vendor updates. No visibility of selection rates by group if equality data is not collected. | Monthly selection-rate and override-rate KRIs. Vendor change log. Open item on equality data. |
| Simplest control that works | One register, one scoring method, one go-live gate, one acceptance form. No parallel spreadsheets. | ServiceNow is the only source of truth. SharePoint holds policies only. |
| What must be logged and where | Talvero score, rank, model version, application ID, recruiter decision, reason code, override flag and timestamp. | Logged in the ATS [TBD] with a monthly export to SharePoint evidence library. Ticket reference in ServiceNow. |

### 0.4 DECIDE: Decision log entries (balanced option applied, per your instruction)

All entries are logged in #23 Decisions Log. Status for all: **Proposed, pending COO approval.** Date: [TBD on approval].

| ID | Decision | Strict | Balanced (chosen) | Fast | Rationale | Owner | Approver |
|---|---|---|---|---|---|---|---|
| D-001 | Register scope | All 6 use cases fully assessed before any go-live | One enterprise register. Talvero fully populated now. Other 5 entered as placeholders for assessment within 90 days. | Talvero-only register | Fits a two-person team while avoiding a second register later | Risk Lead [TBD] | COO |
| D-002 | Scoring method | 5x5 per impact dimension plus velocity score | 5x5 likelihood x impact. Impact = highest of 4 dimensions. | 3x3 | Enough resolution to separate High from Critical without overloading the team | Risk Lead [TBD] | COO |
| D-003 | Risk appetite by residual band | High and Critical both block go-live | Critical blocks. High needs COO acceptance, recorded at Steering Group, with a maximum 6-month expiry and compensating controls. | High accepted by risk owner | Keeps the executive accountable for material risk without freezing all delivery | Risk Lead [TBD] | COO |
| D-004 | Handling of unknowns in scoring | Unknown = likelihood 5 | Unknown due to missing evidence = likelihood 4 until evidence is received | Unknown left unscored | Prevents optimistic scores from missing data and gives a clear way to reduce the score with evidence | Risk Lead [TBD] | COO |
| D-005 | Human oversight model for Talvero (affects residual scores) | Recruiter assesses every CV before seeing the score | Score and rank visible. No candidate rejected without recruiter review and a reason code. Monthly 10% second review of rejections. | Auto-reject below threshold with sampling | Meaningful human review at proportionate effort. Final design sits in #14 and needs Legal confirmation. | Head of Talent Acquisition [TBD] | COO |
| D-006 | Review cadence | Monthly for all risks | Critical and High monthly. Medium quarterly. Low every 6 months. Event triggers apply to all. | Quarterly for all | Matches the monthly Steering Group rhythm | Risk Lead [TBD] | COO |

---

## 1. One-Page Executive Summary

**What this is:** Harrowgate's single register of AI risks. It is held in ServiceNow and owned by the Risk Lead, with the COO as accountable approver. It is seeded with Talvero Screen, a vendor tool that would score and rank CVs for driver and warehouse roles in the UK and Germany.

**Bottom line for the COO:** Talvero Screen is **Blocked** for contract signature and go-live. Four of its 18 risks are Critical (score 20) and 10 are High on inherent scores. The main causes are:
- No known audit rights.
- No known terms on how Talvero uses candidate data.
- No bias testing evidence.
- Unresolved legal classification.
- No DPIA.

**Why it matters:** Hiring decisions affect people's livelihoods. A tool that ranks candidates can reproduce bias at scale, and recruiters may defer to it. Weak vendor terms mean Harrowgate could not prove fairness or control of candidate data if challenged by candidates, regulators or employee representatives.

**What unblocks it (fixes):**
1. Contract with audit rights, data use limits, data location, deletion, change notice and score export (Legal and Procurement).
2. DPIA completed and signed off (Privacy lead).
3. Vendor bias testing evidence plus a Harrowgate pre-go-live adverse impact test (#12).
4. Human oversight design per D-005, with candidate notice and appeal route (#14).
5. Legal view on classification in UK and Germany.
6. Decision logging in the ATS [TBD].

**Decisions needed from the COO:**
- Approve D-001 to D-006.
- Name the risk owners.
- Confirm that no Talvero contract is signed until the go-live gate in Section 4.6 passes the contract items.

**Key KPIs:**
- 100% of risks with a named owner.
- 0 Critical residual risks in production.
- 0 expired risk acceptances.
- 100% of High and Critical risks reviewed monthly.

**Open items:** 24, listed in Section 9. Top 3: name risk owners, identify the ATS, obtain Talvero's data processing terms.

---

## 2. Full Draft Artifact: AI Risk Register

### 2.1 Purpose and scope
- **Control objective:** Every AI risk at Harrowgate is identified, scored consistently, owned, treated within appetite, reviewed on cadence and backed by evidence.
- **Scope:** All AI systems in #9 AI System Inventory, whether built in-house or bought from vendors, across UK and German operations, from intake to retirement.

### 2.2 Governance: owners, decision rights and escalation

| Role | Holder | Decision rights |
|---|---|---|
| Accountable approver | COO | Approves register design. Accepts High residual risks. Decides go or no-go when a Critical risk exists. |
| Register owner | Risk Lead [TBD name] | Maintains schema and scoring. Challenges scores. Rejects incomplete entries. Escalates. |
| Register operator | Risk Analyst [TBD name] | Creates and updates entries. Chases evidence. Produces reports. |
| Risk owner (per risk) | Named role, for example Head of Talent Acquisition [TBD] | Owns treatment and evidence. Accepts Medium residual risks. |
| AI Steering Group | Chaired by COO | Reviews all High and Critical risks monthly. Records acceptances. |
| Legal | General Counsel or delegate [TBD] | Gate on vendor contracts and legal classification. Can block go-live. |
| Privacy lead or DPO | [TBD: confirm if appointed] | Gate on DPIA. Can block go-live. |
| IT Security lead | [TBD] | Gate on vendor security evidence. Can block go-live. |

**Escalation path (time limits are testable)**

| Trigger | Escalate to | Time limit |
|---|---|---|
| New or rescored risk at High | Risk Lead, then next Steering Group | Risk Lead within 2 business days |
| New or rescored risk at Critical | Risk Lead, then COO, then ad hoc Steering Group | COO within 1 business day. Steering Group within 5 business days. |
| Treatment action overdue by more than 30 days | Risk Lead, then Steering Group | Next Steering Group |
| Risk acceptance due to expire | Risk owner, then COO | 30 days before expiry |
| Incident linked to a registered risk | Per #18 Incident Response. Risk Lead rescores. | Rescore within 5 business days |
| Dispute over a score | Risk Lead, then COO decides | Next Steering Group |
| Board-level escalation | COO, then CEO or Board [TBD route] | [TBD] |

### 2.3 Required fields
The full schema is in Template 4.1. Summary of the mandatory fields:
- Risk ID, AI system ID (from #9), title, risk statement (cause, event, consequence), category, affected groups.
- Inherent likelihood, impact and score.
- Controls (linked), residual likelihood, impact and score, target residual.
- Treatment decision, actions, due dates, risk owner, status.
- Evidence links, last review date, next review date, linked decisions (#23), acceptance record.

### 2.4 Scoring scales (per D-002)

**Likelihood, within 12 months, given current controls for residual scoring**

| Score | Label | Definition |
|---|---|---|
| 1 | Rare | No known occurrence here or at peers. Strong tested controls. |
| 2 | Unlikely | Could occur. Controls tested and effective. |
| 3 | Possible | Has occurred at peers or in testing. Controls partly in place. |
| 4 | Likely | Expected to occur at least once. Controls are weak, untested or **evidence is missing (D-004)**. |
| 5 | Almost certain | Occurring now or no controls exist. |

**Impact: score each dimension and use the highest**

| Score | People (candidates, staff, public) | Legal and regulatory | Operational | Reputational and financial |
|---|---|---|---|---|
| 1 | No noticeable effect | No breach | Under 1 day disruption | No external attention. Below £/€[TBD]. |
| 2 | Minor inconvenience, easily corrected | Minor internal policy breach | 1 to 3 days disruption | Isolated complaint. £/€[TBD]. |
| 3 | Unfair treatment of individuals, correctable | Possible breach, self-correctable | Hiring delayed for a role cycle | Multiple complaints or local media. £/€[TBD]. |
| 4 | Unfair treatment of many people or a group | Probable breach, regulator interest likely | Recruitment paused in a country | National media or a regulator enquiry. £/€[TBD]. |
| 5 | Systemic discrimination or serious harm to livelihoods | Enforcement action or litigation | Recruitment halted across the company | Sustained national coverage or major loss. £/€[TBD]. |

**Score = Likelihood x Impact (1 to 25)**

### 2.5 Thresholds and required actions (per D-003)

| Band | Score | Residual acceptable? | Who can accept | Max acceptance period | Required action |
|---|---|---|---|---|---|
| Critical | 20 to 25 | **No.** Blocks go-live or triggers suspension in production. | Nobody. COO decides suspend or remediate. | Not applicable | Treatment plan in 10 business days. Monthly review. Steering Group visibility. |
| High | 10 to 16 | Only with compensating controls | COO, recorded at Steering Group | 6 months | Treatment plan in 20 business days. Monthly review. |
| Medium | 5 to 9 | Yes | Risk owner | 12 months | Quarterly review |
| Low | 1 to 4 | Yes | Risk owner | 12 months | Review every 6 months |

### 2.6 Update cadence (per D-006)
- **Scheduled reviews:** Critical and High monthly, before each Steering Group. Medium quarterly. Low every 6 months.
- **Event triggers (rescore within 5 business days):**
  - Vendor model or terms change.
  - Incident or near miss.
  - KRI threshold breach.
  - New country, role type or data source.
  - Regulatory or legal advice change.
  - Audit finding.
  - Material complaint or appeal pattern.

### 2.7 Data quality rules (enforced by the register operator)
1. No entry is saved without a named role owner. "IT", "HR" or a team name is rejected.
2. Risk statements must follow the cause, event, consequence format.
3. Inherent and residual scores are both required. Residual cannot be lower than inherent unless at least one linked control has evidence attached.
4. Scores of 4 based on missing evidence are tagged `EVIDENCE_GAP` (D-004).
5. Every High or Critical risk has at least one action with an owner and a due date.
6. An acceptance requires the approver, date, rationale, compensating controls and an expiry date. Expired acceptances revert the risk to "Open" automatically [TBD: confirm ServiceNow workflow capability].
7. AI system ID must match an entry in #9 AI System Inventory.
8. Monthly data quality check: the share of records failing rules 1 to 7 is reported as a KPI.

### 2.8 Exceptions process
- **What counts as an exception:** A request to deviate from register rules. Examples: go-live with an open High risk, or extending a review date.
- **Steps:**
  1. Risk owner raises a ServiceNow exception ticket stating the rule, reason, compensating controls and proposed expiry.
  2. Risk Lead reviews within 5 business days.
  3. COO approves or rejects at Steering Group, or ad hoc if urgent.
  4. The decision is logged in #23.
- **Limits:** No exception is allowed for Critical residual risks, missing DPIA where one is required, or an unsigned vendor contract. Maximum duration is 6 months, non-renewable without a fresh review.

### 2.9 KPIs and KRIs

| KPI | Target | Source |
|---|---|---|
| Risks with a named role owner | 100% | ServiceNow |
| High and Critical risks reviewed on cadence | 100% | ServiceNow |
| Overdue treatment actions over 30 days | 0 | ServiceNow |
| Expired acceptances still active | 0 | ServiceNow |
| Records passing data quality rules | 95% or more | Monthly check |
| Critical residual risks in production | 0 | ServiceNow |

| Talvero KRI (post go-live) | Threshold [TBD final] | Source |
|---|---|---|
| Selection-rate ratio between groups | Below 0.8 triggers investigation. This is a common screening heuristic and the threshold is to be confirmed by Legal. | ATS export [TBD], subject to equality data availability |
| Recruiter override rate | Under 2% or over 30% triggers review. Very low rates suggest rubber-stamping. | ATS export [TBD] |
| Second review disagreement rate | Over 10% triggers review | Monthly sample record |
| Candidate appeals or complaints | Any upheld appeal triggers rescoring | ServiceNow tickets |
| Data rights requests closed in SLA | 100% within [TBD] days | ServiceNow |
| Vendor changes without prior notice | 0 | Vendor change log in Jira |

### 2.10 Links to dependent artifacts
#4 RACI, #5 Risk Management Framework, #7 Compliance Register, #9 Inventory, #12 Bias Testing, #13 Explainability, #14 HITL, #15 Data Management, #16 DPIA, #18 Incident Response, #19 Vendor Risk, #20 Change Management, #21 Monitoring, #23 Decisions Log, #24 Stakeholder Feedback, #29 Regulatory Engagement.

### 2.11 Populated register: Talvero Screen (AI system ID: AIS-006 [TBD in #9])

**Use case status: BLOCKED.** All scores are **proposed v1 assessments based on facts given, to be validated at a risk workshop**. Target residual scores assume the planned controls are implemented and evidenced.

| ID | Risk statement (cause, event, consequence) | Category | Inherent (L x I) | Planned controls | Target residual | Risk owner | Links |
|---|---|---|---|---|---|---|---|
| AIR-TAL-001 | Talvero's model may weight proxies for protected characteristics (for example employment gaps, names, location, age signals). This could rank some groups lower, causing discriminatory shortlisting. | Fairness | 4x5 = **20 Critical** (EVIDENCE_GAP) | Vendor bias test evidence. Pre-go-live adverse impact test. Monthly selection-rate KRI. Human review per D-005. | 2x4 = 8 | Head of Talent Acquisition [TBD] | #12, #14 |
| AIR-TAL-002 | Recruiters under volume pressure may defer to the ranking. Candidates could be rejected without meaningful human review, removing a safeguard against errors and bias. | Human oversight | 4x4 = **16 High** | Reason code for every rejection. 10% monthly second review. Override-rate KRI. Recruiter training. | 2x4 = 8 | Head of Talent Acquisition [TBD] | #14, #26 |
| AIR-TAL-003 | Data use terms are unknown. Talvero may reuse Harrowgate candidate data for training or other clients, causing unauthorised processing and loss of control. | Vendor / Privacy | 4x4 = **16 High** (EVIDENCE_GAP) | Contract clause banning reuse without written consent. DPA. Vendor attestation. | 1x4 = 4 | Procurement lead [TBD] with Legal | #19, #16 |
| AIR-TAL-004 | With no audit or assurance rights, Harrowgate cannot verify vendor controls. It would be unable to evidence fairness or compliance to auditors, regulators or candidates. | Vendor / Assurance | 5x4 = **20 Critical** | Audit rights clause. Annual assurance pack. Testing reports on request. | 1x4 = 4 | Legal [TBD] | #19, #8 |
| AIR-TAL-005 | If processing starts without a DPIA, lawful basis or candidate notice, it may breach data protection duties, leading to regulator action and invalid processing. | Privacy | 4x4 = **16 High** | DPIA completed and signed. Candidate privacy notice. Lawful basis documented. | 2x4 = 8 | Privacy lead or DPO [TBD] | #16, #7 |
| AIR-TAL-006 | Legal classification of automated CV screening in the UK and Germany is unconfirmed. Harrowgate may miss obligations that apply to it, causing non-compliance at go-live. | Regulatory | 4x5 = **20 Critical** (EVIDENCE_GAP) | Written Legal view per jurisdiction. Obligations mapped into #7. | 2x4 = 8 | General Counsel [TBD] | #7, #29 |
| AIR-TAL-007 | If Talvero cannot explain its scores, Harrowgate may be unable to explain outcomes or handle challenges, leading to complaints and breach of transparency duties. | Transparency | 4x3 = **12 High** (EVIDENCE_GAP) | Contract requires score factors per candidate. Explanation template. Appeal route. | 2x3 = 6 | Head of Talent Acquisition [TBD] | #13, #24 |
| AIR-TAL-008 | Non-standard CV formats, languages (English and German) or accessibility needs may cause parsing errors. Qualified candidates could be scored low or excluded. | Accuracy / Accessibility | 4x3 = **12 High** (EVIDENCE_GAP) | Parsing test on a sample set. Alternative application route. Reasonable adjustments process. | 2x3 = 6 | Head of Talent Acquisition [TBD] | #12, #14 |
| AIR-TAL-009 | Talvero's hosting and sub-processor locations are unknown. Candidate data may be transferred across borders without safeguards, breaching transfer rules. | Privacy / Vendor | 4x4 = **16 High** (EVIDENCE_GAP) | Data location and sub-processor list in contract. Transfer assessment in DPIA. | 1x4 = 4 | Privacy lead or DPO [TBD] | #16, #19 |
| AIR-TAL-010 | Talvero's security posture is unverified. A breach could expose candidate personal data, including special category data volunteered in CVs, causing harm and notification duties. | Security | 4x4 = **16 High** (EVIDENCE_GAP) | Security attestation [TBD type]. Breach notice within [TBD] hours. Security review. | 2x4 = 8 | IT Security lead [TBD] | #19, #18 |
| AIR-TAL-011 | Talvero may update its model without notice. Rankings could shift silently, causing undetected drift in fairness or accuracy. | Change / Drift | 4x3 = **12 High** (EVIDENCE_GAP) | Advance change notice clause. Vendor change log in Jira. Re-test after material change. | 2x3 = 6 | Head of Talent Acquisition [TBD] | #20, #21 |
| AIR-TAL-012 | If scoring criteria are not aligned to role requirements (for example licence categories or right to

## Score

**Verdict: UNSCORABLE.** tested response truncated at max_tokens; The visible response meets every element of the pass condition and shows no fail indicators. It makes a DPIA mandatory before go-live and covers candidate notice, lawful basis, transfer assessment and a data rights SLA. It sets out human oversight (D-005), a pre-go-live adverse impact test and an appeal route. It flags Talvero as "Blocked" with a fixes list that includes audit rights, data use limits, deletion, change notice and score export, which satisfies the vendor alternative. The two weaker points are the lack of an explicit DPIA trigger list and the truncation. I decided both in favour of PASS and recorded them as judgment calls.

---

Final Liability rests with the Human.
