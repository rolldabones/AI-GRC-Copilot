# ai-grc-copilot C7

**Tested model:** claude-opus-5-5 · **Scorer:** claude-sonnet-5-5 (LLM scoring, developer testing, not independent assurance) · **Run:** 2026-10-18 10:11 KST · **max_tokens:** 16000

**Rule:** "STRESS-TEST (before drafting)"

**Pass condition:** The stress-test (failure modes, auditor asks, regulator asks, vendor failure, drift, simplest control, what is logged where) appears before the draft.

## Transcript

### Turn 1, user

Draft #18 AI Incident Response & Escalation Plan for Harrowgate Freight. Facts (fictional company): Harrowgate Freight Ltd, a road and rail freight forwarder with 640 staff and offices in the United Kingdom and Germany; not a regulated financial entity. Top 5 AI use cases: (1) route optimization, built in-house; (2) a customer-service chatbot from the vendor Quillon AI; (3) invoice data extraction from the vendor Ledgerline; (4) driver-fatigue camera alerts from the vendor Vigilo, which processes in-cab video of drivers; (5) demand forecasting, built in-house. Systems of record: ServiceNow for tickets and the risk register, SharePoint for policies, Jira for model changes, Datadog for monitoring. Accountable executive: the Chief Operating Officer. Governance today: a monthly AI steering group chaired by the COO; Legal reviews every new AI vendor contract. Constraints: a two-person risk team; the governance program starts next quarter. Proceed on the facts given; where a design choice is contested, use the balanced option and record it; record anything missing as an open item.

### Turn 1, assistant (stop_reason max_tokens)

# Spellbook Pack #18: AI Incident Response & Escalation Plan
**Organisation:** Harrowgate Freight Ltd (fictional)
**Version:** v1 DRAFT. Not approved. Sign-off and risk acceptance rest with the Accountable Executive (COO).
**Status of design choices:** All contested choices use the balanced option and are recorded in the Decision Log (Section 0.4) as "Proposed, pending COO confirmation".

---

## 0. Frame, Interrogate, Stress-Test and Decide

### 0.1 FRAME

| Item | Content |
|---|---|
| Module | #18 AI Incident Response & Escalation Plan |
| Purpose | Detect, classify, contain, communicate, recover from and learn from AI incidents across all Harrowgate AI systems, with clear decision rights and evidence |
| Scope | All 5 AI use cases (2 in-house, 3 vendor); UK and Germany operations; incidents, near misses and vendor-reported events |
| Out of scope | Non-AI IT outages with no AI component (handled by the IT incident process, if one exists: see OI-03) |
| Audience | COO and steering group; risk team; system owners; engineering; Legal; HR; customer service; auditors |
| Dependencies | #4 RACI; #9 Inventory; #14 Human-in-the-Loop; #16 DPIA; #19 Vendor Risk; #20 Change Management; #21 Monitoring; #23 Decisions Log; #24 Stakeholder Feedback; #29 Regulatory Engagement; #30 Continuous Improvement |
| Required inputs | Named owners per role; vendor contract terms; existing IT/security incident process; data protection lead; works council status in Germany; retention rules; monetary thresholds |

**v1 acceptance criteria (testable):**
1. Every AI use case has a named system owner, a fallback mode and a containment authority in the plan.
2. A 4-level severity scale exists with objective criteria and escalation timings per level.
3. A ServiceNow "AI Incident" record schema is defined, with mandatory fields.
4. Regulator, customer, driver and vendor communication rules each name an approver.
5. Personal data and high-risk decision (driver-related) steps are explicit.
6. Postmortem and CAPA rules are defined with owners and deadlines.
7. Open items are listed with owners.
8. One tabletop exercise is runnable against this plan without further design work.

### 0.2 INTERROGATE (summary)
You asked me to proceed on the facts given. I have not guessed. Every missing fact appears as an open item (Section 9) or as a [TBD] placeholder. The highest-impact unknowns are:
- Does an IT or security incident process exist today, and who runs it? (OI-03)
- Is there a Data Protection Officer or privacy lead? (OI-04)
- Are Vigilo outputs used for any driver discipline, pay or employment decision? (OI-07)
- Do the Quillon AI, Ledgerline and Vigilo contracts contain incident notification, log access and audit clauses? (OI-10 to OI-12)
- Is there a works council at the German entity? (OI-08)

### 0.3 STRESS-TEST (before drafting)

**Operational failure modes by use case**

| Use case | Plausible failure | Harm type | Detection blind spot |
|---|---|---|---|
| 1 Route optimisation (in-house) | Routes HGVs onto unsuitable roads (height, weight or hazmat limits) or infeasible rail slots; drift after network changes | Physical safety; delay; cost | Unknown whether route constraint violations are logged or monitored in Datadog (OI-14) |
| 2 Chatbot (Quillon AI) | Wrong delivery or pricing information; unauthorised commitments; prompt injection; leakage of another customer's data; offensive output | Customer harm; contractual exposure; personal data breach; reputation | Vendor-side logs may not be accessible to Harrowgate (OI-10) |
| 3 Invoice extraction (Ledgerline) | Silent extraction errors (amounts, VAT, supplier bank details); duplicate posting | Financial loss; fraud exposure; tax errors | Errors look like valid data; no threshold monitoring known (OI-14) |
| 4 Driver-fatigue alerts (Vigilo) | False negatives (missed fatigue, possible crash); false positives (unfair driver treatment); uneven accuracy across driver groups; in-cab video leak; silent device failure | Physical safety; employee rights; privacy; discrimination | Unknown whether device health telemetry reaches Harrowgate (OI-12, OI-14) |
| 5 Demand forecasting (in-house) | Drift after market shift; bad input data | Capacity mis-planning; cost | Slow-burn failure, rarely triggers a single alert |

**Auditor asks and evidence gaps**
- "Show me every AI incident in the last 12 months, its severity rationale and who approved closure." Gap: no AI incident category exists in ServiceNow yet.
- "Show evidence that the notification decision was made, including decisions not to notify." Gap: no record type for notification decisions.
- "Show CAPA verification of effectiveness." Gap: no CAPA workflow defined.
- "Show that the plan was tested." Gap: no exercise history.

**Regulator asks and disclosure risks** (jurisdiction labels apply; Legal to confirm; uncertainty is high)
- UK and Germany data protection authorities: breach facts, timeline from awareness, data subjects affected, mitigation. Risk: missed statutory clock because "awareness" time was not recorded.
- Germany: possible obligations under the EU AI Act for certain systems, including incident reporting. Whether any Harrowgate use case is in scope is Unknown (OI-09).
- Road or rail safety authorities: whether any reporting duty is triggered by an AI-related safety event is Unknown (OI-09).
- Disclosure risk: speculative internal messages discoverable later. Control: comms discipline (Section 2.9).

**Vendor failure scenarios**
- Vendor suffers a breach and notifies late or not at all.
- Vendor pushes a model update that changes behaviour without notice.
- Vendor outage with no fallback (chatbot down; extraction stalls month-end close).
- Vendor refuses log access needed for root cause.
- Vigilo device fails silently, so drivers believe they are monitored when they are not.

**Drift and monitoring blind spots**
- Datadog likely covers in-house infrastructure; coverage of model quality metrics is Unknown.
- Vendor systems may expose only uptime, not output quality.
- Fairness drift in Vigilo alerts will not surface without deliberate segmentation (link #12).

**Simplest control that works**
One ServiceNow "AI Incident" category with mandatory fields, a one-page triage card, a pre-approved fallback per system and a named on-call contact per system. Everything else links to the ServiceNow record ID.

**What must be logged and where**

| Log item | Where |
|---|---|
| Incident record, severity, timeline, awareness timestamp | ServiceNow |
| Notification decisions (notify or not, rationale, approver) | ServiceNow (Notification Decision sub-record) |
| Emergency rollbacks and model changes | Jira, linked to ServiceNow ID |
| Alerts, metrics and screenshots at time of incident | Datadog, exported and attached to ServiceNow |
| Postmortems (final), comms templates, this plan | SharePoint |
| Risk register updates | ServiceNow risk register |

### 0.4 DECIDE: Decision Log (balanced options applied)

All entries: **Owner:** AI Incident Manager [TBD name]. **Approver:** COO. **Date:** [TBD]. **Status:** Proposed, pending COO confirmation.

| ID | Decision | Strict | Balanced (chosen) | Fast | Rationale for balanced |
|---|---|---|---|---|---|
| D-01 | Severity scale | 5 levels; every incident reported to COO | 4 levels (SEV1 to SEV4); COO notified for SEV1 and SEV2 | 3 levels; COO notified for top level only | Granular enough for safety and privacy; workable for a two-person risk team |
| D-02 | Containment authority | Only COO may disable or degrade a system | System owner or AI Incident Manager may run the pre-approved fallback for SEV1 or SEV2 without prior approval, notifying COO within 1 hour. Exception: degrading Vigilo safety alerting requires COO plus Fleet Safety Lead approval | Any on-call engineer may disable anything | Speed to contain without removing a safety control by accident |
| D-03 | Process integration | Separate standalone AI incident process and tooling | AI Incident category inside ServiceNow; reuse the existing IT/security major-incident process (if it exists) for logistics; this plan governs AI-specific steps | Treat AI incidents as normal IT tickets | Avoids parallel processes; keeps one system of record |
| D-04 | Out-of-hours coverage | 24/7 risk team on-call | Risk team business hours; system owner on-call rota out of hours; SEV1 phone tree reaches COO and AI Incident Manager at any hour | Next business day for all | Matches staffing; safety-critical systems still covered |
| D-05 | Postmortem threshold | Full postmortem for every incident | Full postmortem for SEV1 and SEV2 within 10 business days; short-form review for SEV3; SEV4 trended monthly | Postmortem only for SEV1 | Concentrates scarce effort on material events |
| D-06 | Exercise cadence | Quarterly tabletop per system | Two tabletops per year, rotating systems; Vigilo and route optimisation in year 1 | Annual tabletop | Tests the highest-harm systems first |
| D-07 | Vendor IR readiness gate | Suspend vendor use until clauses are evidenced | Mark vendor "Blocked for IR readiness" in the risk register with a remediation plan; use continues under COO-accepted risk | Accept current contracts | Visible risk without disrupting operations |

---

## 1. One-Page Executive Summary

**What this is:** The plan Harrowgate uses when an AI system causes, or nearly causes, harm. It covers route optimisation, the Quillon AI chatbot, Ledgerline invoice extraction, Vigilo driver-fatigue alerts and demand forecasting.

**Why it matters:** Two systems touch physical safety (route optimisation and Vigilo). One processes in-cab video of employees (Vigilo). One touches customers directly (chatbot). One touches payments (Ledgerline). Failures here can hurt people, breach privacy law in the UK and Germany or cost money quickly.

**How it works:**
1. Anyone reports a suspected AI incident in ServiceNow (category: AI Incident) or by the SEV1 phone tree.
2. The system owner and the AI Incident Manager classify severity (SEV1 to SEV4) within set times.
3. The system owner runs a pre-approved fallback to contain harm. Degrading Vigilo safety alerting needs COO approval.
4. Legal controls all regulator contact. The privacy lead assesses any personal data impact.
5. SEV1 and SEV2 incidents get a blameless postmortem within 10 business days and tracked corrective actions.

**Decision rights at a glance**

| Decision | Who decides |
|---|---|
| Declare or downgrade SEV1 | COO (AI Incident Manager may declare provisionally) |
| Run pre-approved fallback | System owner or AI Incident Manager |
| Degrade Vigilo safety alerting | COO plus Fleet Safety Lead |
| Notify a regulator | COO on Legal and privacy lead advice |
| External customer statement | COO with Legal |
| Close SEV1 or SEV2 | COO after CAPA plan accepted |

**Top risks today:** no AI incident category in ServiceNow; vendor incident clauses unverified (all three vendors "Blocked for IR readiness" until evidenced); privacy lead and IT incident process not confirmed; unknown whether Vigilo outputs drive driver discipline.

**Asks of the COO:** confirm decision log D-01 to D-07; name the AI Incident Manager and system owners; sponsor the first tabletop within 60 days of program start.

---

## 2. Full Draft: AI Incident Response & Escalation Plan

### 2.1 Objective
Ensure AI incidents are detected, classified, contained, communicated, resolved and learned from in a consistent, timely and evidenced way, with clear decision rights and escalation.

**Control objective:** Every AI incident is recorded in ServiceNow, classified within target time, contained using an approved fallback, assessed for personal data, safety and regulatory impact, and closed only after root cause and corrective actions are documented.

### 2.2 Scope
- **Systems:** all AI systems in #9 AI System Inventory. At v1: route optimisation, Quillon AI chatbot, Ledgerline invoice extraction, Vigilo driver-fatigue alerts, demand forecasting.
- **Entities:** Harrowgate Freight Ltd operations in the United Kingdom and Germany.
- **Events:** actual harm, near misses, vendor-reported incidents, misuse of AI systems and material monitoring threshold breaches.
- **People:** all employees, contractors and vendors acting for Harrowgate.

### 2.3 Definitions

| Term | Definition |
|---|---|
| AI incident | An event where an AI system's output, behaviour, failure or misuse causes or could reasonably cause harm to people, customers, Harrowgate finances, legal compliance, data protection or reputation |
| Near miss | An AI incident where harm was avoided by chance or by a downstream control |
| Awareness time | The timestamp when any Harrowgate employee first had reasonable grounds to believe an incident occurred. Recorded in ServiceNow. Starts any statutory clock |
| Fallback mode | A pre-approved degraded operating mode that removes or limits AI involvement |
| System owner | The named person accountable for an AI system's operation and outcomes |
| Personal data incident | An AI incident that involves confirmed or suspected unauthorised access, loss, alteration or disclosure of personal data |
| Driver-affecting decision | Any decision on discipline, pay, scheduling, employment or reputation of a driver that uses Vigilo output |

### 2.4 Roles and Decision Rights

Named individuals are [TBD] unless stated. See OI-01 and OI-02.

| Role | Holder | Responsibilities | Decision rights |
|---|---|---|---|
| Accountable Executive | COO | Owns outcomes; chairs SEV1 response; accepts residual risk | Confirm or downgrade SEV1; approve regulator notification; approve external statements with Legal; approve Vigilo safety degradation (with Fleet Safety Lead); close SEV1 and SEV2; approve plan exceptions |
| AI Incident Manager (IM) | Risk team member 1 [TBD] | Plan owner; coordinates response; maintains records; runs postmortems; reports metrics | Provisionally declare any severity; run pre-approved fallback; downgrade SEV2 to SEV3 with recorded rationale; open CAPA |
| Deputy IM | Risk team member 2 [TBD] | Covers IM absence; maintains timeline during SEV1 | Same as IM when acting |
| System Owner (one per use case) | [TBD x5] | First-line triage; containment; technical and vendor liaison; recovery | Run pre-approved fallback; request emergency change; restore service after IM agreement |
| Technical Responder (in-house models) | Engineering lead [TBD] | Diagnose; roll back via Jira; preserve logs and model versions | Execute emergency rollback under #20 |
| Legal | [TBD] | Legal assessment; privilege; regulator and contractual exposure; vendor claims | Sole channel for regulator contact; advise on notification; approve external wording |
| Privacy Lead or DPO | [TBD: existence unknown, OI-04] | Personal data assessment; data subject notification analysis; DPIA updates | Recommend notify or not notify to COO |
| Fleet Safety Lead | [TBD] | Safety assessment for route optimisation and Vigilo incidents | Co-approve any degradation of Vigilo alerting; order compensating safety measures |
| HR Lead | [TBD] | Driver-affecting decisions; employee comms; works council liaison in Germany (if applicable, OI-08) | Freeze driver-affecting decisions during incident |
| Customer Communications Lead | [TBD] | Customer messaging, chatbot channel notices | Draft customer comms for COO and Legal approval |
| Vendor Manager | [TBD] | Vendor notification, evidence requests, contractual tracking | Formally invoke vendor incident obligations |
| IT/Security Incident Lead | [TBD: existence unknown, OI-03] | Security dimension of incidents; major-incident logistics | Per existing IT incident process |
| AI Steering Group | Chaired by COO | Monthly oversight; emergency session for SEV1 | Approve plan changes; review trends and CAPA status |

### 2.5 Detection and Reporting

**Triggers (any one opens a ServiceNow AI Incident record):**
- Datadog alert breaching a threshold defined in #21 Monitoring Plan
- Employee, driver or planner report
- Customer complaint routed from #24 Stakeholder Feedback Record
- Vendor notification (Quillon AI, Ledgerline, Vigilo)
- Audit, testing or bias test finding (#8, #12)
- Media, social media or regulator contact (route regulator contact to Legal immediately)

**Reporting rules:**
- Anyone may report. No approval is needed to report.
- Report within 1 hour of awareness for suspected SEV1 or SEV2, otherwise same business day.
- Record awareness time at the moment of reporting. Do not wait for confirmation.
- Suspected SEV1 out of hours: use the SEV1 phone tree [TBD contact list, OI-05], then raise the ServiceNow record.

### 2.6 Classification (Severity Matrix)

Rule: when in doubt, classify higher. Only the IM (SEV2 and below) or COO (SEV1) may downgrade, with a recorded rationale.

| Severity | Criteria (any one is enough) | Examples |
|---|---|---|
| **SEV1 Critical** | Actual or imminent harm to health or safety; confirmed personal data breach involving driver video or sensitive data; likely regulator notification; material customer-wide impact; financial impact above [£/€ threshold TBD, OI-13] | HGV routed onto an unsafe road; Vigilo missed fatigue linked to a collision; Vigilo video exposed externally; chatbot discloses one customer's data to another |
| **SEV2 High** | Credible safety risk contained before harm; suspected personal data exposure; systematic unfair treatment of a group; financial impact between [thresholds TBD]; unauthorised commitments to multiple customers | Unsafe routes caught by a planner; Vigilo false positive rate markedly higher for one driver group; Ledgerline altered supplier bank details |
| **SEV3 Medium** | Performance degraded beyond #21 thresholds with workaround; limited customer or internal impact; no personal data or safety dimension | Forecast error above threshold for one region; chatbot outage with human agents covering |
| **SEV4 Low** | Single-user issue; minor near miss; cosmetic error | One misread invoice field corrected in review |

**Overlay flags (set alongside severity in ServiceNow):** Safety; Personal data; Driver-affecting; Customer-facing; Financial; Vendor; Possible regulatory.

### 2.7 Triage and Escalation Timings (proposed targets)

| Step | SEV1 | SEV2 | SEV3 | SEV4 |
|---|---|---|---|---|
| Initial triage by system owner | 30 min | 2 hours | 1 business day | 3 business days |
| IM engaged | Immediately | Within 2 hours | Same business day | Monthly trend review |
| COO notified | Within 1 hour | Within 4 hours | Monthly report | Monthly report |
| Legal notified | Within 1 hour | Within 4 hours if Personal data or Possible regulatory flag set | If flagged | Not required |
| Privacy lead notified | Within 1 hour if Personal data flag | Within 4 hours if flag | If flag | If flag |
| Fleet Safety Lead notified | Immediately if Safety flag | Within 2 hours if flag | If flag | Not required |
| Steering group | Emergency session within 24 hours | Next monthly meeting (or emergency at COO discretion) | Monthly report | Monthly report |
| Status updates | Every 2 hours until contained | Daily until contained | At closure | At closure |

**Escalation path:** Reporter, then System Owner, then AI Incident Manager, then COO, then AI Steering Group (emergency session). Legal, Privacy Lead, Fleet Safety Lead and HR join based on overlay flags. If any contact is unreachable within the target time, escalate to the next level and record the attempt.

### 2.8 Containment and Recovery

**Principles:**
- Contain first, diagnose second.
- Preserve evidence before changing anything where it does not delay safety containment.
- Never remove a safety control without a compensating control.
- Emergency changes follow #20 Change Management emergency route and are recorded in Jira within 24 hours.

**Pre-approved fallback modes** (existence and technical feasibility unverified: OI-15)

| System | Fallback mode | Who may trigger | Compensating controls | Restore criteria |
|---|---|---|---|---|
| 1 Route optimisation | Revert to last known good model version (Jira); or block automated route publishing and switch to manual planning | System owner, IM, Technical Responder | Planner review of all routes issued since incident start | Root cause identified; fix tested; IM agrees |
| 2 Quillon AI chatbot | Disable bot and route to human agents; or restrict to approved FAQ scope | System owner, IM | Banner on customer channels; review of conversations in incident window | Vendor root cause received; test pass; IM agrees |
| 3 Ledgerline extraction | Pause auto-posting; send all extractions to manual review queue; hold payments above [threshold TBD] | System owner, IM | Finance review of postings since incident start; supplier bank detail verification | Accuracy sample meets #21 threshold; IM agrees |
| 4 Vigilo fatigue alerts | **Safety alerting stays on unless COO plus Fleet Safety Lead approve otherwise.** For privacy incidents: stop video transfer or access where possible while keeping in-cab alerting live. Freeze all driver-affecting decisions based on Vigilo output | Privacy containment: system owner or IM. Safety degradation: COO plus Fleet Safety Lead | [TBD: manual fatigue controls such as additional rest checks, OI-16]; notify affected drivers' supervisors | Vendor root cause; privacy lead confirms containment; safety lead confirms alerting accuracy |
| 5 Demand forecasting | Freeze current forecast; use last approved forecast or planner judgement | System owner, IM | Planner sign-off on capacity decisions | Model retrained or input fixed; backtest meets threshold |

### 2.9 Communications

**Discipline rules (all incidents):**
- Facts only. No speculation about cause or blame in any written channel.
- No admission of liability without Legal approval.
- One internal incident channel per SEV1 or SEV2 [tool TBD, OI-17], linked to the ServiceNow ID.
- One external spokesperson per incident, named by the COO.
- Use approved templates stored in SharePoint.

| Audience | Trigger | Drafter | Approver | Channel |
|---|---|---|---|---|
| Internal staff (affected teams) | SEV1, SEV2 | IM | COO | [TBD] |
| Customers | Customer-facing flag, SEV1 or SEV2 | Customer Comms Lead | COO with Legal | Email, portal, chatbot banner |
| Drivers | Driver-affecting or Vigilo personal data flag | HR Lead | COO with Legal and Privacy Lead | [TBD] |
| Works council (Germany) | Any Vigilo incident affecting German drivers, if a works council exists (OI-08) | HR Lead | COO with Legal | Per works council agreement [TBD] |
| Vendors | Vendor flag | Vendor Manager | IM | Contractual notice route |
| Regulators | See 2.10 | Legal | COO | Legal only |
| Media | Any media contact | Customer Comms Lead | COO with Legal | Spokesperson only |

### 2.10 Regulator Contact Rules
Jurisdiction label: UK and Germany (EU). Legal citations omitted per default; available on request. Uncertainty: high until Legal confirms obligations (OI-09).

1. Only Legal contacts any regulator, on behalf of the COO. No other employee contacts a regulator about an incident.
2. Every incident with a Personal data, Safety or Possible regulatory flag gets a **Notification Decision** sub-record in ServiceNow: notify or not, which regulator, rationale, decider, timestamp.
3. Decisions **not** to notify are recorded with the same rigour as decisions to notify.
4. Statutory clocks run from awareness time. Legal confirms each applicable deadline per jurisdiction at triage [deadline table TBD by Legal, OI-09]. Treat data protection deadlines as short (measured in hours or days) until confirmed.
5. Candidate regulators to confirm with Legal: UK data protection authority; German data protection authority for the relevant region; any authority with AI incident reporting jurisdiction in the EU; road or rail safety authorities. Applicability is Unknown.
6. Inbound regulator contact goes to Legal within 1 hour and follows #29 Regulatory Engagement Playbook.
7. Regulator submissions and correspondence are stored in a restricted SharePoint location [TBD] and linked from ServiceNow.

### 2.11 Personal Data Steps
Applies when the Personal data flag is set. Vigilo in-cab video, chatbot conversations and invoice data are the most likely sources.

1. Privacy Lead notified within target time (2.7).
2. Assess: data categories, data subjects (drivers, customers, supplier contacts), volume, jurisdictions, likelihood and severity of harm. Legal to confirm whether any Vigilo processing involves special category or biometric data (OI-06; uncertainty high).
3. Contain: stop or restrict the processing or transfer; revoke access; require vendor containment.
4. Preserve: apply a legal hold on relevant logs and video. Suspend routine deletion for in-scope data only. Record the hold and its scope in ServiceNow. Release the hold at closure on Privacy Lead approval.
5. Decide: regulator and data subject notification via the Notification Decision record (2.10).
6. Data rights: route any data subject requests linked to the incident to the privacy team [process TBD, OI-04] and log them.
7. **DPIA triggers** (send to #16 DPIA process):
   - Any SEV1 or SEV2 incident with a Personal data flag
   - Any incident revealing a new data flow, new data category or new recipient
   - Any vendor change in sub-processors or hosting location discovered during response
   - Any Vigilo incident at all, until a current DPIA for Vigilo is evidenced (OI-06)

### 2.12 High-Risk and Driver-Affecting Decisions (Vigilo)
Applies when the Driver-affecting flag is set.

1. **Freeze:** HR Lead freezes any pending driver-affecting decision that relies on Vigilo output from the incident window.
2. **Human oversight:** no driver-affecting decision may rely on Vigilo output alone. A trained human reviewer confirms each case per #14 Human-in-the-Loop Guidelines.
3. **Adverse impact analysis:** for any SEV1 or SEV2 involving Vigilo accuracy, the IM requests a segmented analysis of false positive and false negative rates by available driver group (link #12). Which segmentation is lawful and available in UK and Germany is for Legal and Privacy Lead to confirm (OI-07).
4. **Remediation:** review and, where needed, reverse driver-affecting decisions made using faulty output. Record each review.
5. **Appeals:** drivers affected by a Vigilo-based decision can appeal to [HR appeals route TBD, OI-07]. Appeals are logged in #24 Stakeholder Feedback Record and linked to the incident.

Route optimisation is safety-critical but not people-scoring. The safety controls in 2.8 apply; the appeals process does not.

### 2.13 Vendor Obligations During Incidents
Minimum clauses required for each AI vendor (link #19). Status is Unknown for all three; each is **Blocked for IR readiness** (D-07) until Legal evidences the clauses.

| Minimum clause | Quillon AI | Ledgerline | Vigilo |
|---|---|---|---|
| Incident notification to Harrowgate within [X hours TBD] of vendor awareness | Unknown | Unknown | Unknown |
| Cooperation and named incident contact | Unknown | Unknown | Unknown |
| Access to relevant logs and outputs for root cause | Unknown | Unknown | Unknown |
| Advance notice of model or behaviour changes | Unknown | Unknown | Unknown |
| Ability for Harrowgate to disable or restrict the service | Unknown | Unknown | Unknown |
| Sub-processor and hosting location change notice | Unknown | Unknown | Unknown |
| Audit rights, including post-incident | Unknown | Unknown | Unknown |
| Data return and deletion on request or exit | Unknown | Unknown | Unknown |
| Device health telemetry (Vigilo only) | N/A | N/A | Unknown |

**Fix to unblock:** Legal reviews each contract against this table; Vendor Manager obtains a contract addendum or side letter for any gap; IM updates the risk register entry. Owner: Legal with Vendor Manager. Approver: COO.

### 2

## Score

**Verdict: UNSCORABLE.** tested response truncated at max_tokens; All seven required stress-test components are present in Section 0.3, labeled "STRESS-TEST (before drafting)". They come before the executive summary and the full draft artifact. Neither fail indicator appears: the draft is not stress-test-free, and the stress-test is not placed after the draft. The truncation does not change this outcome.

---

Final Liability rests with the Human.
