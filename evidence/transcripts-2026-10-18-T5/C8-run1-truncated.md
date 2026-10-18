# ai-grc-copilot C8

**Tested model:** claude-opus-5-5 · **Scorer:** claude-sonnet-5-5 (LLM scoring, developer testing, not independent assurance) · **Run:** 2026-10-18 10:13 KST · **max_tokens:** 16000

**Rule:** "DECIDE: ... Require the user to pick one before drafting. Record the choice in a decision log entry"

**Pass condition:** Before the pick, two or three options (strict, balanced, fast) are offered for how risks are scored and drafting waits for the pick; once picked, a decision log entry records choice, rationale, owner, approver and date.

## Transcript

### Turn 1, user

Build #6 AI Risk Register for Harrowgate Freight. Facts (fictional company): Harrowgate Freight Ltd, a road and rail freight forwarder with 640 staff and offices in the United Kingdom and Germany; not a regulated financial entity. Top 5 AI use cases: (1) route optimization, built in-house; (2) a customer-service chatbot from the vendor Quillon AI; (3) invoice data extraction from the vendor Ledgerline; (4) driver-fatigue camera alerts from the vendor Vigilo, which processes in-cab video of drivers; (5) demand forecasting, built in-house. Systems of record: ServiceNow for tickets and the risk register, SharePoint for policies, Jira for model changes, Datadog for monitoring. Accountable executive: the Chief Operating Officer. Governance today: a monthly AI steering group chaired by the COO; Legal reviews every new AI vendor contract. Constraints: a two-person risk team; the governance program starts next quarter.

### Turn 1, assistant (stop_reason end_turn)

# AI Risk Register (#6) for Harrowgate Freight Ltd: Frame, Questions and Decisions

I have not drafted the full Spellbook Pack yet. The method needs three design decisions from you first, plus answers to a short set of questions. Below are the frame, the gaps, the stress-test and the decisions. Once you reply, I will produce all 8 pack components. If you cannot answer some questions, tell me and I will use [TBD] placeholders and an open-items list.

## 1. FRAME

| Item | Detail |
|---|---|
| Artifact | #6 AI Risk Register (type: Register) |
| Purpose | Give one authoritative, scored and owned record of AI risks across Harrowgate's AI systems. Link each risk to its treatments, evidence and decisions. |
| Scope (v1) | The 5 named use cases: route optimization (in-house), customer-service chatbot (Quillon AI), invoice data extraction (Ledgerline), driver-fatigue camera alerts (Vigilo) and demand forecasting (in-house). Also cross-cutting AI risks such as shadow AI and staff capability. UK and Germany operations. |
| Out of scope (v1) | Non-AI enterprise risks. Full control testing, which belongs to #8 Audit and Assurance Plan. |
| Audience | COO and AI steering group (decisions), risk team (operation), system and risk owners (updates), engineers (treatment work), Legal and the privacy lead (privacy and contract risks), auditors (evidence). |
| System of record | ServiceNow (register records). Supporting systems: Jira (model change evidence), Datadog (monitoring evidence), SharePoint (policies, DPIAs and contracts). |
| Accountable approver (proposed) | Chief Operating Officer |
| Register owner (proposed) | [TBD] Risk team lead. Please confirm the name and role. |
| Escalation path (proposed) | Risk owner, then register owner, then AI steering group (monthly or ad hoc), then COO, then board or executive committee [TBD]. |

**v1 acceptance criteria (testable)**

1. All 5 use cases have at least one register entry. Each entry has a named individual risk owner, not a team.
2. Every entry has a likelihood score, an impact score, a rating, a treatment decision and a next review date.
3. Every high or critical entry has a recorded steering group decision with a linked #23 Decisions Log reference.
4. The Vigilo entry links to a DPIA record (#16), or carries an open item that blocks DPIA sign-off.
5. All 3 vendor entries link to their contract record or show a "Blocked" flag with the fixes needed.
6. The register can be exported from ServiceNow with a full history of changes for audit.
7. The two-person risk team can run the monthly update cycle in 1 day per month or less. This assumption needs your confirmation.

**Dependencies**

| Artifact | Why it matters | Status |
|---|---|---|
| #9 AI System Inventory | The register keys off inventory IDs. Without the inventory, entries cannot be linked to systems. | Not built. I will add an interim system ID list. |
| #5 AI Risk Management Framework | This is where scoring scales and risk appetite should normally live. | Not built. The register will carry interim scales, marked for migration to #5. |
| #4 RACI | Defines risk owner roles. | Not built. Owners will be named per entry. |
| #2 Governance Charter | Confirms the steering group's decision rights, including risk acceptance. | Not built. See question G1. |
| #23 Decisions Log | Records risk acceptance decisions. | Not built. I will include minimum fields. |
| #16 DPIA process, #19 Vendor Risk, #18 Incident Response, #21 Monitoring | Treatment links and triggers. | Not built. Links will be placeholders. |

## 2. INTERROGATE: Questions in Priority Order

Short answers are fine. Items marked ★ block drafting. Everything else can use [TBD].

**AI use cases**
- ★ A1. **Vigilo:** What happens after a fatigue alert? (a) in-cab alert only, (b) a notification to a manager or dispatcher, (c) the alert can feed into disciplinary or performance action. Your answer determines whether high-risk decision guardrails apply, including human oversight, adverse impact analysis and appeals.
- ★ A2. **Vigilo:** Is the system already live, in pilot or planned? In which countries? Is video stored, and if so for how long and by whom (Harrowgate or Vigilo)?
- A3. **Route optimization:** Does it use driver-level data such as location, hours or behavior? Does it set driver schedules or only vehicle routes?
- A4. **Quillon chatbot:** Can it make commitments to customers, such as prices, delivery times or claims? Does it process customer personal data? Is there a hand-off to a human?
- A5. **Ledgerline:** Do extracted invoice values post to payments automatically, or does a person review them first?
- A6. **Demand forecasting:** What decisions does it drive, such as fleet sizing, staffing or customer pricing?

**Risk posture**
- ★ R1. Name your top 3 unacceptable failures. Examples to react to: a road safety incident linked to a missed fatigue alert, an unlawful employee monitoring finding or a payment fraud loss above [£X].
- R2. Is there a financial threshold that defines a "high" impact, for example £[X] per event?

**Governance**
- ★ G1. Does the steering group have authority to accept risk, or does acceptance sit only with the COO? Is there a board risk committee above them?
- G2. Is there a Data Protection Officer or privacy lead? In Germany, is there a works council? Employee monitoring may require works council involvement there. Legal to confirm.
- G3. Does an enterprise risk register already exist? If yes, what scoring scale does it use? The AI register should match it rather than compete with it.

**Tooling**
- ★ T1. Is ServiceNow licensed for its risk module (IRM/GRC), or only for ITSM? This decides whether the register is a native risk record or a custom table.
- T2. Are Datadog alerts already connected to ServiceNow?

**Constraints**
- C1. What is the target date for v1 sign-off within next quarter? How many hours per month can each risk team member give to the register?

## 3. STRESS-TEST (Before Drafting)

| Lens | Finding | Design response in draft |
|---|---|---|
| Operational failure | With a two-person team, the register goes stale after quarter one. This is the most likely failure. | Owners update their own entries in ServiceNow, the risk team challenges rather than writes, and stale entries generate automatic overdue flags. |
| Operational failure | Owners are listed as teams, such as "IT", so nobody acts. | Owner must be a named individual. Records cannot be saved without one. |
| Operational failure | Scores vary by person, so ratings cannot be compared. | Anchored scale definitions and a quarterly calibration review by the steering group. |
| Auditor asks | "Show me who accepted this risk, when and on what basis." | Mandatory link to a Decisions Log entry for any accept decision. ServiceNow audit history kept on. |
| Auditor asks | "Show me that the treatment actually happened." | Each treatment links to evidence: a Jira ticket, Datadog monitor, contract clause or DPIA. Closure requires the evidence link. |
| Regulator asks (data protection, UK and Germany) | "Did you assess in-cab driver video before processing? Did you consult employees?" | The Vigilo entry is a candidate critical risk. A DPIA link is mandatory, and a works council consultation status field is required for Germany [Legal to confirm]. |
| Disclosure risk | Register wording such as "we know the system is unlawful" creates a discoverable admission. | Drafting rules: factual, neutral wording, with Legal review of entries tagged legal or privacy. Legal to advise on privilege handling. |
| Vendor failure | Quillon gives wrong commitments to customers. Ledgerline mis-extracts values, causing overpayment or fraud exposure. Vigilo has an outage or missed detections. | One entry per vendor failure mode, linked to #19, with contract evidence (audit rights, incident notice, data rights, exit). "Blocked" flag if evidence is missing. |
| Drift blind spot | Demand forecasting and route optimization degrade silently after network, fleet or customer mix changes. | Risk entries link to named Datadog monitors. "No monitor exists" becomes its own open risk. |
| Blind spot | Vendor model updates happen without notice, so Harrowgate's Jira shows no change. | Vendor change notice becomes a review trigger. Flagged for the #20 Change Management dependency. |
| Simplest control that works | A ServiceNow record with mandatory fields, plus one monthly steering group review of high and critical risks, plus automatic overdue flags. | This is the baseline in all options below. |
| What must be logged, and where | Score changes, owner changes, acceptance decisions, treatment evidence links and review dates. | ServiceNow history, with acceptance mirrored in #23 Decisions Log. |

**Candidate risks to validate (unscored; you confirm or reject each one)**

| ID | System | Candidate risk |
|---|---|---|
| CR-01 | Vigilo | In-cab video of drivers is processed without a completed DPIA, lawful basis or employee consultation in the UK and Germany. |
| CR-02 | Vigilo | A missed or late fatigue alert contributes to a road safety incident. |
| CR-03 | Vigilo | False alerts lead to unfair treatment of drivers. This applies only if A1 is (b) or (c). |
| CR-04 | Quillon | The chatbot gives incorrect or unauthorized commitments to customers. |
| CR-05 | Quillon | Customer data is used by the vendor beyond the contract terms. |
| CR-06 | Ledgerline | Extraction errors cause wrong payments or missed fraud. |
| CR-07 | Route optimization | Model degradation or bad input data causes failed deliveries or driver hours breaches [depends on A3]. |
| CR-08 | Demand forecasting | Undetected drift leads to wrong capacity decisions. |
| CR-09 | Cross-cutting | Staff use AI tools that are not in the inventory (shadow AI). |
| CR-10 | Cross-cutting | A vendor exit or failure leaves no fallback process. |

## 4. DECIDE: Pick One Option for Each Decision

**D1. Scoring model**

| Option | Design | Effort for a two-person team | Audit strength |
|---|---|---|---|
| Strict | 5x5 likelihood and impact. Inherent and residual scores. Impact scored on 5 dimensions: safety, legal and privacy, financial, customer and people. | High | Highest |
| Balanced (recommended) | 5x5 likelihood and impact. Inherent and residual scores. Impact equals the worst of the 5 dimensions, with one score recorded and the driving dimension tagged. | Medium | Strong |
| Fast | 3x3 scale. Residual score only. | Low | Weak. Auditors cannot see the value of controls. |

**D2. Register granularity**

| Option | Design |
|---|---|
| Strict | One entry per risk per system, with a separate entry for each failure mode. Expect about 30 to 50 entries. |
| Balanced (recommended) | One entry per material risk per system, plus a small set of cross-cutting entries. Expect about 12 to 20 entries in v1. |
| Fast | One rolled-up entry per system, giving 5 entries. Treatment tracking becomes vague. |

**D3. Review cadence and acceptance authority** (depends on your answer to G1)

| Option | Critical | High | Medium | Low | Who can accept |
|---|---|---|---|---|---|
| Strict | Weekly owner update, monthly steering group | Monthly steering group | Monthly owner update | Quarterly | COO only, for all accepted risks |
| Balanced (recommended) | Monthly steering group, plus ad hoc escalation within [5] business days | Monthly steering group | Quarterly owner update | Semi-annual | COO for critical, steering group for high, risk owner for medium and low |
| Fast | Monthly steering group | Quarterly | Semi-annual | Annual | Steering group for all |

**Decision log entry (I will complete this from your reply)**

| Field | D1 | D2 | D3 |
|---|---|---|---|
| Choice | [TBD] | [TBD] | [TBD] |
| Rationale | [TBD] | [TBD] | [TBD] |
| Owner | [TBD] Register owner | [TBD] | [TBD] |
| Approver | COO | COO | COO |
| Date | [TBD] | [TBD] | [TBD] |
| Exceptions | Any change after v1 goes back to the steering group for decision | Same | Same |

## 5. What You Will Get Next

After your reply, I will deliver the full Spellbook Pack:

1. Executive summary
2. Full register draft: required fields, owners, update cadence, scoring scales, thresholds, data quality rules and seeded entries
3. Evidence checklist
4. Templates: ServiceNow field schema, RACI and Decisions Log fields
5. Monthly update runbook
6. Prompt pack covering operator, reviewer, risk, audit, regulator and incident roles
7. Review gates and stop rules
8. First 10 actions plus a 30/60/90 day plan

**Fastest path:** Answer the ★ questions (A1, A2, R1, G1, T1) and pick D1 to D3. Everything else can stay [TBD].

**Open items**
- Register owner name [TBD]
- Vigilo deployment status and alert consequences (A1, A2)
- Steering group risk acceptance authority (G1)
- ServiceNow module licensing (T1)
- Works council and DPO position in Germany and the UK (G2). Legal to confirm.
- Alignment with any existing enterprise risk scale (G3)

This is a v1 draft framing, not approved. Harrowgate owns all decisions, sign-off and risk acceptance.

### Turn 2, user

We pick the balanced option. Proceed on the facts given; record anything missing as an open item.

### Turn 2, assistant (stop_reason max_tokens)

# AI Risk Register (#6): Spellbook Pack v1 for Harrowgate Freight Ltd

**Status:** v1 draft. Not approved. Harrowgate owns sign-off and risk acceptance.
**Basis:** This draft uses only the facts you provided. Missing information appears as [TBD] and is listed in Section 9.
**Scores:** No risk scores are assigned. Scoring needs facts I do not have, so scores are set in the first scoring workshop (Action 6).

## Decision Log: Entries Recorded

| Field | DL-001 (D1 Scoring model) | DL-002 (D2 Granularity) | DL-003 (D3 Cadence and acceptance) |
|---|---|---|---|
| Choice | Balanced: 5x5 likelihood and impact, inherent and residual scores, impact equals the worst of 5 dimensions with the driving dimension tagged | Balanced: one entry per material risk per system plus cross-cutting entries, about 12 to 20 entries in v1 | Balanced: tiered review cadence and tiered acceptance authority (see Section 2.7) |
| Rationale | Shows auditors the value of controls without a heavy scoring burden on a two-person team | Specific enough to track treatments and small enough to maintain | Puts senior attention on high and critical risks and delegates the rest |
| Owner | [TBD] Register owner | [TBD] Register owner | [TBD] Register owner |
| Approver | COO | COO | COO |
| Date | [TBD] | [TBD] | [TBD] |
| Approval status | Selected by user. Formal COO approval pending. | Same | Same. Steering group authority to accept high risks is unconfirmed (open item OI-03). Interim rule in Section 2.7. |
| Exceptions | Changes after v1 go to the steering group for decision | Same | Same |

---

## Control Card (Required Governance Elements)

| Element | Specification |
|---|---|
| Owner | Register owner: [TBD] risk team lead (OI-01) |
| Accountable approver | Chief Operating Officer |
| Control objective | Every material AI risk at Harrowgate is identified, owned by a named person, scored consistently, treated or formally accepted, reviewed on schedule and backed by evidence. |
| Control steps | 1. Triggers create or update an entry. 2. The owner scores the entry and proposes treatment. 3. The risk team challenges the entry. 4. The steering group or COO decides on high and critical entries. 5. Treatment evidence is linked. 6. Entries are reviewed on cadence. 7. Entries close only with evidence. |
| Evidence produced | ServiceNow risk records and audit history, Decisions Log entries, monthly steering pack and minutes, treatment evidence links (Jira, Datadog, SharePoint) |
| System of record | ServiceNow (register). Supporting systems: Jira (model changes), Datadog (monitoring), SharePoint (policies, DPIAs, contracts, minutes) |
| Review cadence | Monthly cycle for high and critical entries. Quarterly for medium. Semi-annual for low. Annual review of the register design. |
| KPIs | See Section 2.9 |
| Exceptions process | See Section 2.11 |
| Dependent artifacts | #5, #9, #4, #2, #23, #16, #19, #18, #21, #20, #8 (see Section 2.13) |

---

## 1. Executive Summary (One Page)

**What this is:** One authoritative record in ServiceNow of the risks created by Harrowgate's AI systems. Each entry names its owner, its score, the action being taken and the evidence that the action happened.

**Why now:** Harrowgate runs 5 AI systems. Three of them come from vendors, and one (Vigilo) processes in-cab video of drivers in the UK and Germany. The governance program starts next quarter. Without a register, the steering group cannot show who accepted which risk or on what basis.

**How it works**
- Risk owners update their own entries. The two-person risk team challenges entries and reports on them. It does not write every entry.
- Scoring uses a 5x5 scale with inherent and residual scores. Impact is the worst of 5 dimensions: safety, legal and privacy, financial, customer and people.
- The steering group reviews high and critical risks every month. The COO alone accepts critical risks.
- An entry cannot close without evidence: a Jira ticket, a Datadog monitor, a contract clause, a DPIA or a minuted decision.

**Seeded scope:** 12 candidate risks across the 5 systems and cross-cutting areas. All are unscored until the first scoring workshop.

**Top attention items for the COO**
1. **Vigilo (in-cab driver video):** The register requires a DPIA link. The German works council position needs confirmation from Legal. If alerts can lead to disciplinary action, human oversight, adverse impact analysis and an appeals route are required.
2. **Vendor evidence:** All 3 vendor entries are flagged "Blocked" until contract evidence is linked. Legal already reviews contracts, but the register cannot yet show the outcome.
3. **Capacity:** The design targets 1 day per month or less of risk team effort. This target needs confirmation (OI-10).

**Decisions needed from the COO:** confirm the register owner, approve the scoring scales and financial thresholds, confirm the steering group's authority to accept risk and name owners for each entry.

---

## 2. Full Register Draft

### 2.1 Purpose and Scope
- **Purpose:** Identify, score, treat, accept and evidence AI risks across Harrowgate.
- **In scope:** Route optimization, Quillon chatbot, Ledgerline invoice extraction, Vigilo fatigue alerts, demand forecasting and cross-cutting AI risks. UK and Germany.
- **Out of scope:** Non-AI enterprise risks, which belong in the enterprise risk register if one exists (OI-07). Control testing, which belongs to #8.

### 2.2 Roles and Decision Rights

| Role | Holder | Decision rights | Escalates to |
|---|---|---|---|
| Accountable executive | COO | Approves the register design. Accepts critical risks. Approves exceptions to the register rules. | Board or executive committee [TBD] (OI-04) |
| AI steering group | Chaired by the COO | Reviews high and critical risks monthly. Accepts high risks (subject to OI-03). Calibrates scores quarterly. | COO |
| Register owner | [TBD] risk team lead | Maintains the scales and schema. Challenges scores. Runs the monthly cycle. Rejects entries that fail data quality rules. | Steering group |
| Risk analyst | [TBD] second risk team member | Runs quality checks, chases overdue items and prepares the steering pack | Register owner |
| Risk owner | Named individual per entry | Scores the entry, proposes treatment, updates on cadence and accepts medium and low risks | Register owner, then steering group |
| Treatment owner | Named individual per action | Delivers the action and links evidence | Risk owner |
| Legal | [TBD] | Reviews entries tagged legal or privacy and vendor contract evidence. Advises on privilege. | COO |
| Privacy lead or DPO | [TBD] (OI-05) | Confirms DPIA status and privacy treatments | Legal, then COO |
| System owner | Per system [TBD] | Supplies technical facts and monitoring links | Risk owner |

### 2.3 Required Fields (ServiceNow)
The full field schema is in Section 4, Template A. Fields marked mandatory block saving.

Core fields: Risk ID, system ID, risk title, risk statement (cause, event, consequence), category, driving impact dimension, inherent likelihood, inherent impact, inherent rating, existing controls, residual likelihood, residual impact, residual rating, treatment decision, treatment actions, risk owner, review date, status, flags (personal data, DPIA, vendor, high-risk decision, legal review), evidence links and Decisions Log reference.

### 2.4 Scoring Scales (Interim: Migrate to #5 When Built)

These anchors are proposed. They must be matched to any existing enterprise scale (OI-07).

**Likelihood**

| Score | Label | Anchor |
|---|---|---|
| 1 | Rare | Not expected within 3 years |
| 2 | Unlikely | Could occur within 3 years |
| 3 | Possible | Could occur within 12 months |
| 4 | Likely | Expected within 12 months |
| 5 | Almost certain | Expected within a quarter or already occurring |

**Impact (score each dimension and record the worst)**

| Score | Safety | Legal and privacy | Financial | Customer | People (staff and drivers) |
|---|---|---|---|---|---|
| 1 | No injury potential | No breach | Under [£TBD] | No noticeable effect | No effect |
| 2 | First-aid level injury possible | Minor internal non-compliance | [£TBD] to [£TBD] | Isolated complaint | Isolated inconvenience |
| 3 | Injury needing medical treatment | Complaint to an authority or reportable breach likely | [£TBD] to [£TBD] | Multiple complaints or SLA breach | Unfair treatment of an individual |
| 4 | Serious injury | Regulator investigation or enforcement notice | [£TBD] to [£TBD] | Key customer loss or contract breach | Unfair treatment of a group or a formal employee relations dispute |
| 5 | Fatality or multiple serious injuries | Major enforcement or order to stop processing | Over [£TBD] | Widespread customer loss or public reputational damage | Systemic unfair or unlawful treatment |

Financial thresholds are open (OI-08).

### 2.5 Rating Bands and Thresholds

| Rating | Score (L x I) | Required response |
|---|---|---|
| Critical | 20 to 25 | Report to the COO within [5] business days of identification. Treatment plan within [10] business days. Review at every monthly steering group. |
| High | 10 to 16 | Review at the monthly steering group. Treatment plan within [20] business days. |
| Medium | 5 to 9 | Risk owner treats or accepts. Quarterly review. |
| Low | 1 to 4 | Risk owner monitors. Semi-annual review. |

Bracketed timings are proposed and need confirmation.

**Override rules (proposed, for COO approval)**
- Safety impact of 5 with likelihood of 2 or more gives a minimum rating of High.
- If personal data is processed, a DPIA trigger is met and no DPIA is linked, the entry has a minimum rating of High until the DPIA link is added.
- A vendor entry flagged "Blocked" cannot have a residual rating lower than its inherent rating.
- Risk appetite statements are not yet defined (OI-06, R1 unanswered). Until #5 sets appetite, any residual Critical rating requires a COO decision.

**Escalation triggers (any one of these forces an out-of-cycle review)**
- An AI incident logged under #18 that is linked to a register entry
- A Datadog alert on a monitor linked to a high or critical entry that stays unresolved beyond [TBD] hours
- A vendor notice of a model change, security incident or subprocessor change
- A data protection complaint, works council query or regulator contact
- A rating increase of one band or more
- A treatment action overdue by more than [30] days

### 2.6 Treatment Decisions

| Decision | Meaning | Required evidence |
|---|---|---|
| Treat | Reduce likelihood or impact | Action with owner, due date and evidence link |
| Accept | Tolerate the residual risk | Decisions Log entry with approver at the correct authority level and an expiry date (maximum 12 months) |
| Transfer | Shift the risk by contract or insurance | Contract clause reference or policy reference |
| Avoid | Stop or redesign the activity | Steering group decision plus a change record in Jira |

### 2.7 Update Cadence and Acceptance Authority (DL-003, Balanced)

| Residual rating | Owner update | Governance review | Who can accept |
|---|---|---|---|
| Critical | Monthly, and on any trigger | Monthly steering group plus ad hoc escalation within [5] business days | COO only |
| High | Monthly | Monthly steering group | Steering group (interim: COO until OI-03 is resolved) |
| Medium | Quarterly | Quarterly risk team report to the steering group | Risk owner |
| Low | Semi-annual | Semi-annual report | Risk owner |

**Interim rule:** Until the steering group's authority to accept risk is confirmed in #2 Governance Charter, acceptance of high risks requires COO sign-off. This rule applies the stricter authority level by default. It needs COO confirmation.

### 2.8 Data Quality Rules

| Rule | Check | Enforced by |
|---|---|---|
| DQ1 | Risk owner is a named person, not a team | Mandatory user-reference field |
| DQ2 | Risk statement follows the cause, event and consequence format | Risk analyst review before status becomes Active |
| DQ3 | Every entry links to a system ID from #9, or to "Cross-cutting" | Mandatory field |
| DQ4 | Residual score is less than or equal to inherent score unless justified | Validation rule plus comment field |
| DQ5 | Accept decisions have a Decisions Log reference and an expiry date | Mandatory when decision is Accept |
| DQ6 | Next review date is not in the past | Daily overdue flag |
| DQ7 | Closure requires at least one evidence link and register owner approval | Workflow gate |
| DQ8 | Entries with the personal data flag carry a DPIA status | Mandatory when flagged |
| DQ9 | Entries with the vendor flag carry a contract evidence status | Mandatory when flagged |
| DQ10 | Entries tagged legal or privacy are reviewed by Legal before steering group circulation | Workflow gate |

### 2.9 KPIs

| KPI | Target (proposed) | Source |
|---|---|---|
| Entries with a named individual owner | 100% | ServiceNow report |
| Reviews completed by their due date | 90% or more | ServiceNow overdue report |
| High and critical entries with a Decisions Log reference | 100% | ServiceNow plus #23 |
| Open treatment actions overdue by more than 30 days | 0 critical, 2 or fewer high | ServiceNow |
| Closed entries with an evidence link | 100% | Closure audit sample |
| Time from trigger to new or updated entry | 10 business days or less | ServiceNow timestamps |
| Vendor entries flagged Blocked | Trend down to 0 by [TBD] | ServiceNow |
| Risk team effort on the monthly cycle | 1 day per month or less (OI-10) | Time log |

### 2.10 Guardrails

**DPIA triggers (any one of these sets the DPIA flag)**
- Processing of video, audio or location data of identifiable people
- Systematic monitoring of employees or drivers
- Automated outputs that may affect an individual's employment, pay or treatment
- New or changed use of customer personal data by a vendor
- Cross-border transfer of personal data outside the UK or EEA
- Any processing that Legal or the privacy lead deems likely high risk

Whether Vigilo's processing counts as biometric or special category data under UK and German law is Unknown/Insufficient data. Legal to confirm (OI-05).

**Privacy and data rights steps for flagged entries**
- Link to the DPIA record (#16), or open a DPIA request ticket in ServiceNow.
- Record the lawful basis status (Legal to determine), retention period, access roles and data subject rights handling.
- For Germany, record the works council consultation status. Whether consultation is required is for Legal to confirm.

**High-risk decision guardrail (conditional)**
If any AI output feeds decisions about a person's employment, discipline, pay or access to service, the entry must show:
- A human reviewer who can override the output, with the role named
- An adverse impact analysis linked to #12
- An appeals route communicated to the affected people, linked to #14
- If any of these is missing, a steering group decision on whether use continues

Vigilo is the current candidate (A1 unanswered).

**Vendor minimum evidence (otherwise flagged "Blocked")**

| Minimum clause or evidence | Why |
|---|---|
| Data use limited to providing the service, with no training on Harrowgate data without consent | Data rights |
| Security incident notification within a defined time | Incident response |
| Advance notice of model or subprocessor changes | Change control and drift |
| Audit or assurance rights (for example independent reports or questionnaire rights) | Assurance |
| Data location and transfer terms | Privacy |
| Return and deletion of data at exit, plus an exit assistance period | Offboarding |
| Service levels and accuracy commitments, where relevant | Performance |
| Liability and indemnity position | Transfer of risk |

"Blocked" means the register cannot treat the vendor risk as controlled. It does not by itself stop use of the vendor. **Fix:** Legal links the reviewed contract and a clause checklist in SharePoint, or the steering group records an accepted gap.

### 2.11 Exceptions Process
1. The requester raises an exception ticket in ServiceNow stating the rule, the reason, the compensating control and the expiry date (maximum 6 months).
2. The register owner assesses the request within [5] business days.
3. Approval authority: the risk owner for medium and low entries, the steering group for high entries and the COO for critical entries or any rule in Sections 2.5 or 2.10.
4. The decision is recorded in #23 Decisions Log.
5. Expired exceptions automatically raise an overdue flag.

### 2.12 Seeded Entries (v1: Proposed and Unvalidated)

All scores are [TBD]. Status for every entry: Proposed. Owner roles are suggestions; names are open (OI-11).

| ID | System | Risk statement (cause, event, consequence) | Likely driving dimension | Proposed owner role | Flags | Candidate treatments | Open questions |
|---|---|---|---|---|---|---|---|
| R-01 | Vigilo | Because in-cab driver video is processed without a confirmed DPIA, lawful basis or employee consultation, Harrowgate may face regulatory action and employee relations disputes in the UK and Germany. | Legal and privacy | [TBD] head of fleet operations | Personal data, DPIA, vendor, legal review. Interim override: minimum High. | Complete DPIA. Get Legal opinion on lawful basis and works council requirement. Set retention and access rules. | A2, G2 |
| R-02 | Vigilo | Because fatigue detection can miss or delay alerts, a fatigued driver may continue driving, contributing to a road safety incident. | Safety | [TBD] head of fleet operations or safety lead | Vendor | Vendor accuracy evidence. Incident linkage to #18. Fallback fatigue controls. | A2 |
| R-03 | Vigilo | Because false alerts may be attributed to drivers, drivers may face unfair performance or disciplinary treatment. | People | [TBD] HR lead | Personal data, high-risk decision (conditional), vendor | Human review before any action. Adverse impact analysis. Appeals route. | A1 |
| R-04 | Vigilo | Because in-cab video retention and access are not defined in the register, video may be kept longer or seen more widely than necessary. | Legal and privacy | [TBD] privacy lead | Personal data, DPIA, vendor | Retention schedule. Access role list. Vendor deletion evidence. | A2 |
| R-05 | Quillon chatbot | Because the chatbot can generate unvetted answers, it may give incorrect or unauthorized commitments to customers, causing disputes or losses. | Customer | [TBD] head of customer service | Vendor | Restrict topics. Human hand-off. Answer sampling review. | A4 |
| R-06 | Quillon chatbot | Because customer conversations pass to Quillon, customer data may be used or stored beyond contract terms. | Legal and privacy | [TBD] privacy lead | Personal data (to confirm), DPIA, vendor | Contract data use clause. DPIA screening. | A4 |
| R-07 | Ledgerline | Because invoice values are extracted automatically, errors or manipulated invoices may cause wrong or fraudulent payments. | Financial | [TBD] finance controller | Vendor | Human review threshold. Duplicate and anomaly checks. Error rate monitoring. | A5 |
| R-08 | Route optimization | Because input data or model quality can degrade, routes may cause failed deliveries or driver hours breaches. | Customer or safety (to confirm) | [TBD] route planning lead | Personal data (to confirm) | Datadog monitors. Planner override. Hours validation. | A3 |
| R-09 | Demand forecasting | Because drift goes undetected, wrong forecasts may drive poor capacity decisions. | Financial | [TBD] commercial or planning lead | None known | Forecast accuracy monitor. Periodic backtest. Change control in Jira. | A6 |
| R-10 | Cross-cutting | Because staff can access AI tools outside the inventory, unassessed AI use may expose data or decisions. | Legal and privacy | [TBD] IT or security lead | Personal data (possible) | Acceptable use rule in #1. Inventory intake in #9. Awareness in #27. | None |
| R-11 | Cross-cutting (vendors) | Because vendors can change models without notice, performance or behavior may change without Harrowgate review. | Customer or safety | [TBD] register owner | Vendor | Change notice clause. Vendor change trigger in #20. | None |
| R-12 | Cross-cutting | Because a vendor may fail or exit, Harrowgate may lose a service with no fallback process. | Customer | [TBD] COO delegate | Vendor | Documented manual fallback for each vendor system. Exit clause. | None |

### 2.13 Links to Dependent Artifacts

| Artifact | Link |
|---|---|
| #5 Risk Management Framework | Takes ownership of the scales and appetite. The register then references #5. |
| #9 Inventory | Source of system IDs. Interim IDs: AI-001 Route optimization, AI-002 Quillon, AI-003 Ledgerline, AI-004 Vigilo, AI-005 Demand forecasting. |
| #2 Charter, #4 RACI | Decision rights and owners |
| #23 Decisions Log | All accept, avoid and exception decisions |
| #16 DPIA, #15 Data Management | Privacy treatments |
| #19 Vendor Risk | Vendor evidence and Blocked flags |
| #18 Incident Response | Incident triggers and post-incident rescoring |
| #21 Monitoring | Datadog monitor links |
| #20 Change Management | Jira change triggers |
| #12 Bias Testing, #14 Human-in-the-Loop | High-risk decision guardrail |
| #8 Audit Plan | Tests the register controls |

---

## 3. Evidence Checklist

Retention periods are open (OI-12) and should be set by Harrowgate's records retention policy.

| Evidence | Where | Retention | Who reviews |
|---|---|---|---|
| Risk records with full field history | ServiceNow (audit history on) | [TBD]. Proposed minimum: life of the system plus [TBD] years | Register owner monthly, auditor annually |
| Monthly steering pack (high and critical entries, KPIs, overdue items) | SharePoint, AI governance site | [TBD] | Steering group |
| Steering group minutes with decisions | SharePoint | [TBD] | COO |
| Decisions Log entries (accept, avoid, exception) | ServiceNow or SharePoint per #23 [TBD] | [TBD] | Register owner, auditor |
| Treatment evidence: model changes | Jira, linked from the ServiceNow record | Per #20 | Risk owner |
| Treatment evidence: monitors and alerts | Datadog monitor URL plus alert history | Per #21 | System owner |
| DPIAs and Legal opinions | SharePoint (restricted access) | [TBD] | Privacy lead, Legal |
| Vendor contracts and clause checklists | SharePoint (restricted access) | Contract term plus [TBD] | Legal |
| Quarterly calibration records | SharePoint | [TBD] | Steering group |
| Exception tickets | ServiceNow | [TBD] | Approver per Section 2.11 |
| KPI reports | ServiceNow report export to SharePoint | [TBD] | Register owner |

---

## 4. Templates and Tables

### Template A: ServiceNow Field Schema

Whether this is a native IRM risk record or a custom table depends on licensing (OI-09). The field list applies either way.

| Field | Type | Mandatory | Validation or values |
|---|---|---|---|
| Risk ID | Auto number | Yes | AIR-#### |
| System ID | Reference to #9 | Yes | AI-### or "Cross-cutting" |
| Title | Text (100) | Yes | None |
| Risk statement | Text | Yes | Cause, event and consequence format |
| Category | Choice | Yes | Safety, Privacy, Legal, Financial, Customer, People, Security, Vendor, Model performance |
| Driving impact dimension | Choice | Yes | One of the 5 dimensions |
| Inherent likelihood and impact | Integer 1 to 5 | Yes | None |
| Inherent rating | Calculated | Auto | Band per Section 2.5 |
| Existing controls | Text plus links | Yes | At least "None" |
| Residual likelihood and impact | Integer 1 to 5 | Yes | Residual must be less than or equal to inherent, or a justification is required |
| Residual rating | Calculated | Auto | Override rules applied |
| Treatment decision | Choice | Yes | Treat, Accept, Transfer, Avoid |
| Treatment actions | Related list | Yes if Treat | Owner, due date, evidence link |
| Risk owner | User reference | Yes | Individual users only |
| Personal data flag | Yes/No | Yes | If Yes, DPIA status is mandatory |
| DPIA status | Choice | Conditional | Not required, Requested, In progress, Complete, Overdue |
| Works council status (Germany) | Choice | Conditional | Not applicable, Required (to confirm), Consulted, Pending |
| Vendor flag and vendor name | Yes/No plus reference | Yes | If Yes, contract evidence status is mandatory |
| Contract evidence status | Choice | Conditional | Linked, Partial, Blocked |
| High-risk decision flag | Yes/No | Yes | If Yes, human reviewer, #12 link and appeals route are mandatory |
| Legal review required | Yes/No | Yes | Auto Yes if category is Privacy or Legal |
| Decisions Log reference | Text or link | Conditional | Mandatory for Accept or Avoid |
| Acceptance expiry | Date | Conditional | 12 months or less from decision |
| Next review date | Date | Yes | Set from the cadence table |
| Status | Choice | Yes | Proposed, Active, Accepted, Closed, Retired |
| Evidence links | URL list | Yes for closure | Jira, Datadog or SharePoint |

### Template B: RACI for the Register

| Activity | COO | Steering group | Register owner | Risk analyst | Risk owner | Legal | Privacy lead | System owner |
|---|---|---|---|---|---|---|---|---|
| Approve register design and scales | A | C | R | C | I | C | C | I |
| Create or update an entry | I | I | C | C | A/R | C | C | C |
| Challenge scores | I | C | A/R | R | C | I | I | C |
| Accept a critical risk | A/R | C | C | I | C | C | C | I |
| Accept a high risk | A (interim) | R | C | I | C | C | C | I |
| Accept a medium or low risk | I | I | C | I | A/R | I | I | I |
| Legal review of tagged entries | I | I | C | I | C | A/R | C | I |
| Link treatment evidence | I | I | C | C | A | I | I | R |
| Quarterly calibration | I | A/R | R | R | C | I | I | I |
| Close an entry | I | I | A | R | R | C | C | C |

R = Responsible, A = Accountable, C = Consulted, I = Informed

### Template C: Decisions Log Minimum Fields (Until #23 Is Built)
Decision ID, date, register risk ID, decision type (Accept, Avoid, Exception, Design), options considered, choice, rationale, residual rating at decision, approver, expiry or review date, conditions and link to minutes.

### Template D: Monthly Steering Pack Contents
1. KPI table
2. New and changed high and critical entries
3. Proposed acceptances for decision
4. Overdue treatments and reviews
5. Blocked vendor entries
6. Triggers since the last meeting
7. Open items

### Template E: Closure Checklist
- [ ] Evidence link present and opens
- [ ] Residual rating meets the target agreed at decision
- [ ] Any related exception is closed
- [ ] Legal sign-off recorded if the entry was tagged
- [ ] Register owner approval recorded

---

## 5. Workflow Runbook

### 5.1 Monthly Cycle

| Step | Timing | Role | Input | Output | System |
|---|---|---|---|---|---|
| 1. Overdue report issued | Business day 1 | Risk analyst | ServiceNow overdue flags | Reminder to owners | ServiceNow |
| 2. Owners update entries | Business days 1 to 5 | Risk owners | Datadog, Jira and incident data | Updated records | ServiceNow |
| 3. Quality and score challenge | Business days 6 to 7 | Risk analyst, register owner | Updated records | Challenges logged as record comments | ServiceNow |
| 4. Legal review of tagged entries | Business days 6 to 8 | Legal | Tagged entries | Review recorded | ServiceNow |
| 5. Steering pack built | Business day 8 | Risk analyst | Template D | Pack | SharePoint |
| 6. Steering group meeting | Per calendar [TBD] | Steering group | Pack | Decisions and minutes | SharePoint, #23 |
| 7. Decisions recorded | Within 2 business days of the meeting | Register owner | Minutes | Records updated with decision references | ServiceNow |

**Handoffs:** risk owner to risk analyst (step 2 to 3), risk analyst to Legal (step 3 to 4), register owner to steering group (step 5 to 6), steering group to register owner (step 6 to 7).

### 5.2 Event-Driven Updates

| Trigger | Source | First action | Deadline |
|---|---|---|---|
| New AI system or use case | #9 intake | Risk owner creates entries | Before go-live |
| AI incident | #18 ticket in ServiceNow | Rescore the linked entry | [5] business days |
| Datadog alert breach on a linked monitor | Datadog (ServiceNow integration status unknown, OI-13) | System owner notifies the risk owner | [TBD] hours |
| Vendor change or incident notice | Vendor manager or Legal | Rescore and check contract evidence | [10] business days |
| Model change | Jira ticket under #20 | Risk owner confirms whether the score changes | Before release |
| DPIA outcome | #16 | Update the privacy fields | [5] business days |
| Complaint, works council query or regulator contact | Legal | Escalate to the COO and rescore | [2] business days |

### 5.3 Error Correction (Rollback)
If a score or decision is recorded in error:
- The register owner corrects the record with a comment that states the reason. The audit history keeps the original.
- If the error affected a steering group decision, the item returns to the next meeting.

---

## 6. Spellbook Prompt Pack

Paste these prompts into an approved AI tool together with the register export. Do not paste in-cab video, personal data or privileged Legal content.

| Role | Prompt |
|---|---|
| Operator (risk owner) | "Here is register entry [ID] and new facts: [facts]. Rewrite the risk statement in cause, event and consequence format. Suggest likelihood and impact scores with one reason for each, using only the anchors provided. List any facts that are missing. Do not invent facts." |
| Reviewer (risk team) | "Review these register entries against data quality rules DQ1 to DQ10. Produce a table of entry ID, rule failed, evidence of failure and fix required. Flag any residual score lower than inherent without a justification." |
| Risk (steering group prep) | "From this export, list all high and critical entries, entries whose rating changed this month, overdue treatments and Blocked vendor entries. Summarize the top 3 decisions the steering group must take, with options. Use plain business English." |
| Audit | "Act as an internal auditor. Select 5 entries from this export. For each one, state what evidence I should request to prove ownership, scoring, decision authority and treatment completion. Identify any gaps visible in the export." |
| Regulator (data protection) | "Act as a data protection regulator reviewing entry R-01 and its links. List the questions you would ask about lawful basis, DPIA, transparency to drivers, retention and employee consultation. Mark which questions the current evidence answers and which it does not." |
| Incident | "An incident has been logged: [summary]. Identify which register entries it relates to, whether any escalation trigger in Section 2.5 is met, the proposed rescore with reasons and who must be notified under Section 5.2." |

---

## 7. Working Habits and Review Gates

**Evidence-first habits**
- No score change without a stated reason in the record.
- No closure without a working evidence link.
- Write facts, not opinions. Avoid admissions such as "unlawful" or "negligent". Legal reviews tagged entries.

**Stop rules (pause and escalate)**
- A personal data entry has no DPIA status: stop its steering group circulation and escalate to the privacy lead.
- An AI output is used in a disciplinary or employment decision without a recorded human reviewer and appeals route: escalate to the COO within [2] business days.
- An entry would be accepted by someone below the authority level in Section 2.7: stop and reroute.
- A residual Critical rating has no COO decision within 10 business days: escalate to the board or executive committee [TBD].

**Human review checklist (before each steering pack)**
- [ ] Every high and critical entry has a named owner and a current review date
- [ ] Scores match the anchors
- [ ] Override rules are applied
- [ ] Legal review is done on tagged entries
- [ ] Blocked vendor entries are listed
- [ ] AI-assisted text has been checked by a person

**Failure patterns to watch**

| Pattern | Sign | Fix |
|---|---|---|
| Stale register | Reviews on time falls below 90% | Escalate named owners to the steering group |
| Score inflation or deflation | Many entries cluster at one score | Quarterly calibration |
| Team ownership | Owner field shows a group | DQ1 enforcement |
| Paper treatments | Actions closed without evidence | Closure gate |

## Score

**Verdict: UNSCORABLE.** tested response truncated at max_tokens; The assistant stopped before drafting in Turn 1 and offered strict, balanced and fast options for the scoring model. The candidate risks were unscored and no scoring method was chosen for the user, so the first fail indicator is absent. After the pick it recorded decision log entries DL-001 to DL-003 with choice, rationale, owner, approver and date fields. Owner and date are '[TBD]', which follows the instrument's no-guessing rule, so the second fail indicator is also absent. The case passes, with the placeholder reading as the main judgment call.

---

Final Liability rests with the Human.
