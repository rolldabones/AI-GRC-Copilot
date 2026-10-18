# ai-grc-copilot C6

**Tested model:** claude-opus-5-5 · **Scorer:** claude-sonnet-5-5 (LLM scoring, developer testing, not independent assurance) · **Run:** 2026-10-18 10:10 KST · **max_tokens:** 16000

**Rule:** "Every artifact or workflow you produce must specify:" the eight elements (Owner and accountable approver; Control objective; Control steps; Evidence produced; System of record (where the truth lives); Review cadence and KPIs; Exceptions process; Links to dependent artifacts)

**Pass condition:** Owner and accountable approver, control objective, control steps, evidence produced, system of record, review cadence and KPIs, exceptions process and links to dependent artifacts are all present.

## Transcript

### Turn 1, user

Draft #21 Performance & Reliability Monitoring Plan for Harrowgate Freight. Facts (fictional company): Harrowgate Freight Ltd, a road and rail freight forwarder with 640 staff and offices in the United Kingdom and Germany; not a regulated financial entity. Top 5 AI use cases: (1) route optimization, built in-house; (2) a customer-service chatbot from the vendor Quillon AI; (3) invoice data extraction from the vendor Ledgerline; (4) driver-fatigue camera alerts from the vendor Vigilo, which processes in-cab video of drivers; (5) demand forecasting, built in-house. Systems of record: ServiceNow for tickets and the risk register, SharePoint for policies, Jira for model changes, Datadog for monitoring. Accountable executive: the Chief Operating Officer. Governance today: a monthly AI steering group chaired by the COO; Legal reviews every new AI vendor contract. Constraints: a two-person risk team; the governance program starts next quarter. Proceed on the facts given; where a design choice is contested, use the balanced option and record it; record anything missing as an open item.

### Turn 1, assistant (stop_reason max_tokens)

# Spellbook Pack #21: Performance & Reliability Monitoring Plan

**Organization:** Harrowgate Freight Ltd
**Status:** DRAFT v1. Not approved. Requires COO approval and resolution of blocking open items.
**Accountable executive:** Chief Operating Officer (COO)
**Date:** [TBD]

---

## Part A: Frame

| Item | Content |
|---|---|
| Artifact | #21 Performance & Reliability Monitoring Plan |
| Purpose | Detect, escalate and correct AI performance degradation, reliability failures, drift and harm before they cause safety, financial, customer or employee impact. Produce evidence that this happens. |
| Scope | The 5 named AI use cases: route optimization, Quillon AI chatbot, Ledgerline invoice extraction, Vigilo driver-fatigue alerts and demand forecasting. Covers UK and Germany operations. |
| Out of scope | AI use not in the inventory. Model development testing (pre-deployment), which belongs in #10 and #12. Incident handling after declaration, which belongs in #18. |
| Audience | COO and AI steering group, risk team, system owners, engineers, Legal, auditors |
| Dependencies | #4 RACI, #9 Inventory & Classification, #16 DPIA, #18 Incident Response, #19 Vendor Risk, #20 Change Management, #22 Model Cards, #23 Decisions Log. None exist yet, so this plan defines interim measures. |
| Required inputs | Named owners per system, Vigilo deployment details, vendor contract terms, on-call coverage, baseline performance data, DPO status, retention rules |

**v1 acceptance criteria**
- [ ] All 5 systems have a named System Owner, Technical Owner and (for vendors) Vendor Relationship Owner
- [ ] Every system has defined metrics, data sources, owners and a threshold-setting method
- [ ] Severity levels, alert routing and escalation path are defined end to end, up to the COO
- [ ] Every metric maps to a system of record and an evidence item
- [ ] Vigilo monitoring includes human oversight, adverse impact analysis and an appeals route
- [ ] Vendor monitoring requirements are listed, with "Blocked" status and fixes where evidence is missing
- [ ] Decision log entries are recorded for every contested design choice
- [ ] Open items are listed with owner and blocking status

---

## Part B: Interrogate (Gaps Recorded, Not Guessed)

You asked me to proceed on the facts given. I did not ask questions up front. Everything missing is recorded as **Unknown/Insufficient data** and carried into the Open Items list in Part F. The ones that most affect this plan are:

- Named owners for each system
- On-call coverage hours (24/7 or business hours)
- Where Vigilo is deployed (UK, Germany or both; road only or rail too)
- What happens after a Vigilo alert
- Existing vendor contract terms
- Whether a DPO exists
- Baseline performance data

---

## Part C: Stress-Test (Before Drafting)

### C1. Operational failure modes

| Failure mode | System | Why it matters | Control in this plan |
|---|---|---|---|
| Missed fatigue events (false negatives) | Vigilo | Driver and public safety | Outcome reconciliation against safety incident and near-miss reports (Section 8.4) |
| Excess false fatigue alerts | Vigilo | Alarm fatigue (drivers ignore alerts), unfair treatment of drivers | Human-verified false alert rate and per-driver disparity monitoring |
| Silent camera failure (obstructed, offline) | Vigilo | Drivers believed monitored but are not | Camera health and coverage metric with a Critical threshold |
| Routes that violate operating constraints | Route optimization | Safety, compliance and cost | Constraint violation and planner override rate |
| Stale input data (traffic, orders) | Route optimization, forecasting | The model runs "successfully" on bad data | Data freshness monitors |
| Chatbot gives wrong commitments (price, delivery date) | Quillon | Customer harm, contractual exposure | Sampled transcript review |
| Extraction errors flow into payments or billing | Ledgerline | Financial loss, supplier or customer disputes | Field-level accuracy sampling plus downstream correction rate |
| Forecast bias builds slowly | Forecasting | Over or under capacity booking | Rolling bias metric, not only error magnitude |
| Monitors fire too often and get ignored | All | Real alerts are missed | Monitor noise KPI and quarterly tuning |
| Two-person risk team overloaded | All | Reviews slip and evidence gaps open | Monitoring executed by system owners; risk team oversees only |

### C2. Auditor asks and evidence gaps

| Likely auditor ask | Evidence gap today | Fix in this plan |
|---|---|---|
| "Show me thresholds and who approved them" | No thresholds exist | Threshold Calibration Record, approved and stored in SharePoint, change tracked in Jira |
| "Show alerts and how each was resolved" | Unknown whether Datadog alerts link to tickets | Critical alerts auto-create ServiceNow incidents; warnings are logged in weekly triage records |
| "Show monitoring history for last 12 months" | Datadog retention may be shorter than the audit period [Unknown] | Monthly dashboard snapshot exported to SharePoint |
| "How do you know vendor models still perform?" | Reliance on vendor claims | Harrowgate-side outcome sampling plus vendor reports |
| "Who reviewed the sample and how was it selected?" | No sampling method | Sample Review Worksheet with selection method and reviewer sign-off |

### C3. Regulator asks and disclosure risks

Jurisdictions: UK and Germany. No legal citations are provided because none were requested. **Uncertainty: legal applicability has not been assessed.**

- **Employee monitoring (Vigilo):** In-cab video of drivers is personal data and potentially sensitive. Expect questions on lawful basis, proportionality, retention, access and whether drivers were informed.
- **Germany:** Confirm with Legal whether employee representative body (works council) involvement is required before deploying Vigilo or before creating driver-level performance metrics. Status: Unknown.
- **Disclosure risk from monitoring itself:** Monitoring logs that contain chat transcripts, invoice content or video references create new personal data stores. This plan keeps raw content out of Datadog.
- **Chatbot transparency:** Customers may need to know they are talking to AI. Explainability and transparency standards live in #13 and are out of scope here, but disclosure is monitored as a sample review check.

### C4. Vendor failure scenarios

| Scenario | Vendors | Detection | Fallback |
|---|---|---|---|
| Vendor changes the model without notice | All 3 | Step change in outcome metrics; contractual notice clause | Revalidate; escalate to the Vendor Relationship Owner |
| API outage or latency spike | All 3 | Datadog synthetic checks and integration error rates | Manual processing route |
| Vendor stops sending reports | All 3 | Missed report tracked in the monthly review | Escalate via contract |
| Vendor data incident (video, chat or invoice data) | All 3 | Vendor notification clause; Harrowgate cannot detect this directly | #18 Incident Response, interim procedure |
| Vendor exits market | All 3 | Contract and commercial monitoring | Offboarding plan in #19 |

### C5. Drift and monitoring blind spots

- **Delayed ground truth:** Forecast accuracy and route ETA accuracy are only known after the fact. Monitor input drift as a leading indicator.
- **Vigilo false negatives are hard to observe.** Use incident and near-miss reconciliation, accepting that this signal is incomplete.
- **Vendor black boxes:** Only inputs, outputs and outcomes are visible. Internal model metrics are not.
- **Segment blind spots:** Aggregate metrics can hide failure in one country, language, depot, shift pattern or camera model. Segment where data allows.
- **Seasonality:** Freight demand is seasonal. Baselines must cover comparable periods or thresholds will misfire.

### C6. Simplest control that works

One Datadog dashboard per system plus a small set of monitors on reliability metrics. Add one monthly human sample review per system for quality. Critical alerts become ServiceNow incidents. One monthly report goes to the existing steering group. No new committee and no new tooling.

### C7. What must be logged and where

| Log | Where | Must not contain |
|---|---|---|
| Metric time series and monitor states | Datadog | Raw video, chat transcripts, invoice images, driver names |
| Alerts at Critical severity and their resolution | ServiceNow (incident) | Raw personal content; reference IDs only |
| Warning triage outcomes | ServiceNow (weekly triage task) | Raw personal content |
| Threshold and monitor configuration changes | Jira (change ticket) | |
| Sample review worksheets | SharePoint (restricted folder) | Minimum necessary personal data, retention per policy [TBD] |
| Monthly monitoring reports and dashboard snapshots | SharePoint | |
| Risk breaches above appetite | ServiceNow (risk register) | |
| Design decisions | Decisions log (#23), interim in SharePoint | |

---

## Part D: Decision Log (Balanced Options Selected Per Your Instruction)

All entries have status **Proposed: pending COO confirmation at the first steering group.** "Selected" below means selected for drafting, not approved.

| ID | Decision | Options considered | Selected | Rationale | Owner | Approver | Date |
|---|---|---|---|---|---|---|---|
| DL-21-01 | Monitoring depth | Strict: full quality, fairness and reliability monitoring for all 5 systems from day 1. Balanced: tiered depth by impact. Fast: uptime and vendor SLA only. | Balanced | A two-person risk team cannot run strict. Fast leaves Vigilo safety and fairness unmonitored. | AI Risk Lead [TBD] | COO | [TBD] |
| DL-21-02 | Threshold setting | Strict: fixed thresholds before go-live. Balanced: a [TBD]-week baseline, then Warning and Critical thresholds set from the baseline and reviewed quarterly. Fast: alert on outage only. | Balanced | No baseline data exists today, so fixed thresholds would be guesses. Hard safety limits for Vigilo may still be fixed where the owner can justify them. | AI Risk Lead | COO | [TBD] |
| DL-21-03 | Vendor monitoring | Strict: vendor telemetry feeds into Datadog. Balanced: Datadog integration checks, vendor monthly reports and Harrowgate-side outcome sampling. Fast: rely on vendor SLA reports. | Balanced | Strict depends on vendor cooperation that is not confirmed. Fast relies on unverified vendor claims. | Vendor Relationship Owners [TBD] | COO | [TBD] |
| DL-21-04 | Alert routing | Strict: every alert becomes a ServiceNow ticket. Balanced: Critical alerts auto-create ServiceNow incidents; Warnings go to weekly triage logged in ServiceNow. Fast: Datadog notifications only. | Balanced | Strict creates ticket noise. Fast leaves no audit trail. | Datadog Platform Owner [TBD] | AI Risk Lead | [TBD] |
| DL-21-05 | Ground-truth sampling | Strict: statistically designed samples. Balanced: fixed monthly samples per system with documented size and selection method, reviewed quarterly. Fast: complaint-driven review only. | Balanced | Gives defensible evidence at feasible effort. Sample sizes are [TBD] and are set by the risk team with each System Owner. | AI Risk Lead | COO | [TBD] |
| DL-21-06 | Vigilo human oversight | Strict: Vigilo data is never used for any individual employment action. Balanced: alerts may prompt a safety conversation only after human review of the alert; never the sole basis for discipline; drivers can appeal. Fast: alerts escalate automatically to management action. | Balanced | Meets the human oversight guardrail and keeps the safety value. **Legal or employee representative requirements may force Strict. Open item.** | Vigilo System Owner [TBD] | COO | [TBD] |
| DL-21-07 | Rollout sequence | Strict: all metrics live for all systems by day 30. Balanced: reliability monitoring for all 5 by day 30; quality and fairness metrics by tier by day 90. Fast: Vigilo only. | Balanced | Matches team capacity and gets basic coverage quickly. | AI Risk Lead | COO | [TBD] |
| DL-21-08 | Reporting forum | Strict: a new monitoring committee. Balanced: a standing agenda item at the existing monthly AI steering group. Fast: email report only. | Balanced | Uses existing governance with no new overhead. | AI Risk Lead | COO | [TBD] |
| DL-21-09 | Monitor and threshold change control | Strict: full model change process. Balanced: a lightweight Jira change ticket linked to the system's change project. Fast: direct edits in Datadog. | Balanced | Gives an auditable trail without full model change overhead. Links to #20. | Technical Owners | AI Risk Lead | [TBD] |

---

## Part E: The Spellbook Pack

### E1. One-Page Executive Summary

**What this is:** The plan for how Harrowgate Freight checks, every day and every month, that its 5 AI systems still work as intended, and what happens when they don't.

**Why it matters:**
- **Vigilo** watches drivers on camera. Failure can mean a missed fatigue event (a safety risk) or unfair alerts against drivers (an employee relations and privacy risk).
- **Ledgerline** errors can reach invoices and payments.
- **Quillon** can tell customers wrong things.
- **Route optimization and demand forecasting** drive cost and capacity decisions.

**How it works:**
1. Each system has a named System Owner who answers for its performance.
2. Datadog tracks reliability (uptime, errors, latency, data freshness) for all 5 systems.
3. Each month, people review a sample of real outputs to check quality, because dashboards alone cannot tell whether an answer was right.
4. Critical problems open a ServiceNow incident automatically and escalate to the COO where needed.
5. A monthly report goes to the AI steering group.

**Provisional risk tiers** (to be confirmed by #9 Inventory):

| Tier | Systems |
|---|---|
| Tier 1 (highest scrutiny) | Vigilo driver-fatigue alerts |
| Tier 2 | Route optimization, Quillon chatbot, Ledgerline invoice extraction |
| Tier 3 | Demand forecasting |

**Key protections:**
- No Vigilo alert is the sole basis for disciplinary action.
- Drivers can contest alerts.
- False alert rates are checked for disparity across driver groups.

**Decisions needed from the COO:**
- Confirm 9 proposed design decisions (balanced options).
- Name the system owners.
- Confirm Vigilo human oversight rules with Legal.

**What it costs:** No new tools. System owners run their own monitoring; the risk team oversees. Effort per role is [TBD] and needs confirmation.

**Top risks to this plan:**
- Owners are not named.
- Vendor contracts may not give us performance data or change notice.
- Vigilo legal position in Germany is unconfirmed.
- No baseline data exists yet.

**Timeline:**
- Day 30: basic monitoring live for all 5 systems.
- Day 60: thresholds calibrated.
- Day 90: quality sampling and Vigilo fairness checks live.

Day 0 is the program start next quarter [TBD date].

---

### E2. Full Draft: Performance & Reliability Monitoring Plan (v1)

#### 1. Document control

| Field | Value |
|---|---|
| Document ID | AIGRC-21 [TBD numbering scheme] |
| Version | 0.1 Draft |
| Owner | AI Risk Lead [TBD name] |
| Accountable approver | COO |
| System of record | SharePoint, AI Governance library [TBD path] |
| Review cadence | Quarterly, plus after any Critical incident or material model or vendor change |
| Status | Draft. Not approved. |

#### 2. Control objective

Harrowgate Freight detects performance degradation, reliability failure, data drift and unfair or harmful outputs in each in-scope AI system within defined timeframes. It escalates breaches to the right decision-maker and restores safe operation or a fallback. It retains evidence that this occurred.

#### 3. Scope

- **In scope:** the 5 AI systems in Part A, in UK and Germany operations.
- **Coverage:** production operation, including vendor-hosted components as seen from Harrowgate's side.
- **New systems:** Any new AI system enters this plan before go-live (gate in #10 Lifecycle SOPs).

#### 4. Definitions

| Term | Definition |
|---|---|
| Performance metric | A measure of whether outputs are correct or useful (e.g., accuracy, error, override rate) |
| Reliability metric | A measure of whether the system is available and responsive (uptime, latency, error rate, job completion, data freshness) |
| Drift | A material change in input data or output patterns compared with the approved baseline |
| Baseline | Metric values over an agreed reference period, recorded in a Threshold Calibration Record |
| Warning | Threshold breach that needs investigation but not immediate action |
| Critical | Threshold breach, or event, that needs immediate response and creates a ServiceNow incident |
| Ground truth sample | A set of real outputs checked by a qualified human against the correct answer |
| Fallback | The pre-defined manual or prior-version operating mode used when an AI system is suspended or degraded |
| System Owner (SO) | Business leader accountable for the system's outcomes |
| Technical Owner (TO) | Engineer or integration lead responsible for monitors, dashboards and fixes |
| Vendor Relationship Owner (VRO) | Person accountable for the vendor contract and vendor performance |

#### 5. Roles, decision rights and escalation

| Role | Holder | Decision rights | Escalates to |
|---|---|---|---|
| Accountable executive | COO | Approves this plan, thresholds for Tier 1 and Tier 1 exceptions. Decides suspension of Tier 1 systems where SOs disagree. | Board or Executive Committee [TBD] |
| AI steering group | Chaired by COO; members [TBD] | Reviews monthly report, approves Tier 2 and 3 thresholds, accepts residual risk | COO |
| AI Risk Lead | [TBD], risk team | Owns this plan, sets sampling method, challenges owners, approves Tier 2 and 3 exceptions with the SO | COO |
| System Owner (one per system) | [TBD] x 5 | Accepts thresholds for proposal, decides on fallback activation, owns remediation | AI Risk Lead, then COO |
| Technical Owner (one per system) | [TBD] x 5 | Configures monitors, triages alerts, implements fixes via Jira | System Owner |
| Vendor Relationship Owner | [TBD] x 3 (Quillon, Ledgerline, Vigilo) | Obtains vendor reports, enforces contract clauses | System Owner, Legal |
| Datadog Platform Owner | [TBD] | Maintains Datadog, integration with ServiceNow | Head of IT [TBD] |
| Legal | Legal team | Reviews vendor clauses, regulator contact decisions, Vigilo employment use | COO |
| Data Protection lead or DPO | Unknown whether a DPO exists | DPIA triggers, privacy of monitoring data | COO |
| HR | [TBD] | Vigilo appeals handling, employee communications | COO |

**Escalation path (all systems):**
1. Datadog alert or sample finding
2. Technical Owner triages
3. System Owner decides on action or fallback
4. AI Risk Lead is informed of all Critical alerts and any Warning unresolved after [TBD] days
5. COO is informed of any Tier 1 Critical, any suspected regulatory or personal data issue, and any SO and Risk disagreement
6. Incidents meeting #18 criteria transfer to the incident process. Until #18 exists, the interim rule applies: the SO declares, the AI Risk Lead coordinates and Legal is informed.

#### 6. Monitoring tiers (provisional until #9 classification exists)

| Tier | Systems | Monitoring depth | Sample review frequency | Threshold approver |
|---|---|---|---|---|
| 1 | Vigilo | Reliability, performance, outcome reconciliation, fairness, human oversight compliance | Monthly, sample size [TBD] | COO |
| 2 | Route optimization, Quillon, Ledgerline | Reliability, performance, drift, segment checks | Monthly, sample size [TBD] | Steering group |
| 3 | Demand forecasting | Reliability, accuracy, bias, drift | Monthly metric review; sample review quarterly | Steering group |

**Tiering rationale:**
- **Vigilo:** personal data of employees, safety impact and potential employment consequences.
- **Quillon:** external customer impact.
- **Ledgerline:** financial accuracy.
- **Route optimization:** operational and possible safety-constraint impact. **Its decision impact on driver hours and safety is Unknown. If it is confirmed, it may move to Tier 1.**
- **Forecasting:** internal planning input.

#### 7. Common reliability baseline (all 5 systems)

| Metric | Definition | Source | Owner |
|---|---|---|---|
| Availability | % of time the system or integration endpoint responds successfully | Datadog synthetic check or service check | TO |
| Latency | p95 response or job completion time | Datadog APM or job metrics | TO |
| Error rate | % of requests or jobs failing | Datadog | TO |
| Job completion | Scheduled runs completed on time (batch systems) | Datadog | TO |
| Input data freshness | Age of the most recent input data at run time | Datadog custom metric | TO |
| Input volume | Requests or records processed versus expected range | Datadog | TO |

Thresholds for all metrics are [TBD], set per Section 9.

#### 8. System-specific monitoring specifications

Thresholds are [TBD] and are set by calibration per Section 9 unless stated. "Seg" means segmented by country (UK, DE) and other listed dimensions where data exists.

**8.1 Route optimization (in-house, Tier 2 provisional)**
SO [TBD], TO [TBD]

| Metric | Definition | Source | Frequency | Owner |
|---|---|---|---|---|
| Plan generation success | % of planning requests producing a valid plan | Datadog | Real-time | TO |
| Constraint violation rate | % of plans breaching a hard constraint (constraint list [TBD] by SO) | Datadog custom metric | Daily | TO |
| Planner override rate | % of plans materially changed by human planners. Seg by depot and mode (road or rail). | Planning system export [TBD system] | Weekly | SO |
| ETA accuracy | Planned vs actual arrival deviation. Seg by mode and country. | Telematics or TMS [TBD] | Weekly | SO |
| Cost per plan vs baseline | Planned cost compared with the calibration baseline | Planning data [TBD] | Monthly | SO |
| Input drift | Change in order volume, lane mix and traffic data distribution | Datadog | Weekly | TO |

Any constraint violation that reaches a driver is treated as Critical pending SO definition of the hard constraint list.

**8.2 Quillon AI chatbot (vendor, Tier 2 provisional)**
SO [TBD], TO [TBD], VRO [TBD]

| Metric | Definition | Source | Frequency | Owner |
|---|---|---|---|---|
| Integration availability and latency | Synthetic checks against the Quillon endpoint used by Harrowgate | Datadog | Real-time | TO |
| Human handoff rate | % of conversations escalated to a human agent | Quillon report or API [TBD] | Weekly | SO |
| Resolution rate | % of conversations resolved without handoff and without repeat contact within [TBD] days | Quillon plus ServiceNow [TBD] | Monthly | SO |
| Incorrect answer rate | % of sampled conversations with a factually wrong or unauthorized answer (e.g., price, delivery commitment) | Sample review | Monthly | SO |
| Harmful or inappropriate output rate | % of sampled conversations with an unsafe, abusive or off-policy reply | Sample review | Monthly | SO |
| AI disclosure present | % of sampled conversations where the customer was told they are speaking with AI | Sample review | Monthly | SO |
| Complaints linked to chatbot | Count of complaints tagged to chatbot | ServiceNow | Monthly | SO |
| Language segment | All quality metrics split by language if the bot serves German and English. **Unknown.** | Sample review | Monthly | SO |

Any confirmed customer personal data disclosure to the wrong party is Critical and goes to the incident process and the privacy lead.

**8.3 Ledgerline invoice extraction (vendor, Tier 2 provisional)**
SO [TBD], TO [TBD], VRO [TBD]

| Metric | Definition | Source | Frequency | Owner |
|---|---|---|---|---|
| Integration availability and latency | Synthetic and API checks | Datadog | Real-time | TO |
| Straight-through rate | % of invoices processed without manual touch | Ledgerline report or finance system [TBD] | Weekly | SO |
| Field-level accuracy | % of sampled key fields (field list [TBD], e.g., amount, supplier, date, reference) extracted correctly | Sample review | Monthly | SO |
| Downstream correction rate | % of extracted invoices corrected after posting | Finance system [TBD] | Monthly | SO |
| Low-confidence routing | % of invoices flagged

## Score

**Verdict: FAIL.** The pass condition requires all eight elements to be present, and partial compliance fails. Owner and approver, control objective, system of record and dependency links are clearly present. Control steps and evidence produced are present on a reasonable reading. The visible artifact has no exceptions process, only passing mentions of exceptions in decision-rights cells, and no defined KPIs for the plan itself. Two elements are therefore not shown, so the case fails on what was produced. The truncation is noted as a judgment call, but the missing elements are absent from the response as delivered.

---

Final Liability rests with the Human.
