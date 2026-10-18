# ai-grc-copilot C10

**Tested model:** claude-opus-5-5 · **Scorer:** claude-sonnet-5-5 (LLM scoring, developer testing, not independent assurance) · **Run:** 2026-10-18 10:13 KST · **max_tokens:** 16000

**Rule:** "Drafting requirements by type"

**Pass condition:** Each draft carries every element listed for its type. Register: required fields, owners, update cadence, scoring scales, thresholds, data quality rules. Policy: objective, scope, definitions, roles, requirements, exceptions, enforcement, evidence, review cadence. SOP: triggers, steps, roles, inputs, outputs, records, handoffs, exceptions, rollback.

## Transcript

### Turn 1, user

For Harrowgate Freight, draft three artifacts: #9 AI System Inventory & Classification Register, #1 AI Policy and #10 AI Lifecycle Management SOPs (one SOP, for deploying a new model version). Facts (fictional company): Harrowgate Freight Ltd, a road and rail freight forwarder with 640 staff and offices in the United Kingdom and Germany; not a regulated financial entity. Top 5 AI use cases: (1) route optimization, built in-house; (2) a customer-service chatbot from the vendor Quillon AI; (3) invoice data extraction from the vendor Ledgerline; (4) driver-fatigue camera alerts from the vendor Vigilo, which processes in-cab video of drivers; (5) demand forecasting, built in-house. Systems of record: ServiceNow for tickets and the risk register, SharePoint for policies, Jira for model changes, Datadog for monitoring. Accountable executive: the Chief Operating Officer. Governance today: a monthly AI steering group chaired by the COO; Legal reviews every new AI vendor contract. Constraints: a two-person risk team; the governance program starts next quarter. Proceed on the facts given; where a design choice is contested, use the balanced option and record it; record anything missing as an open item.

### Turn 1, assistant (stop_reason max_tokens)

# Harrowgate Freight Ltd: AI GRC Spellbook, Batch 1

**Status:** v1 DRAFT. Not approved. For review by the AI Steering Group. Sign-off and risk ownership sit with Harrowgate.
**Artifacts in this batch:** #9 AI System Inventory & Classification Register, #1 AI Policy, #10 AI Lifecycle Management SOPs (SOP-10.1: Deploy a New Model Version)
**Build order:** #9 first, then #1, then #10. The Policy and SOP both depend on the risk tiers defined in the Register.

---

## Part 0: Engagement Frame

### 0.1 Facts received

| Item | Fact |
|---|---|
| Company | Harrowgate Freight Ltd, road and rail freight forwarder |
| Size | 640 staff |
| Geographies | United Kingdom and Germany |
| Regulated status | Not a regulated financial entity |
| Accountable executive | Chief Operating Officer (COO) |
| Governance today | Monthly AI Steering Group chaired by the COO. Legal reviews every new AI vendor contract. |
| Systems of record | ServiceNow (tickets and risk register), SharePoint (policies), Jira (model changes), Datadog (monitoring) |
| Constraints | Two-person risk team. Governance program starts next quarter. |

### 0.2 Use cases received

| ID | Use case | Build or buy | Known data | Known affected groups |
|---|---|---|---|---|
| AI-001 | Route optimization | In-house | Unknown/Insufficient data | Drivers, customers (indirect) |
| AI-002 | Customer-service chatbot | Vendor: Quillon AI | Unknown/Insufficient data | Customers |
| AI-003 | Invoice data extraction | Vendor: Ledgerline | Unknown/Insufficient data | Suppliers, Finance staff |
| AI-004 | Driver-fatigue camera alerts | Vendor: Vigilo | In-cab video of drivers | Drivers |
| AI-005 | Demand forecasting | In-house | Unknown/Insufficient data | Internal planning |

### 0.3 v1 acceptance criteria (whole batch)

- All 5 known AI systems have a register entry with a provisional tier and named owner role.
- Every requirement in the Policy and SOP is testable and names its evidence and system of record.
- Every contested design choice has a decision log entry.
- Every missing fact is a numbered open item with an owner role.
- The design can be run by a two-person risk team.

### 0.4 Decision log (provisional)

You asked me to use the balanced option for contested choices. These entries record that instruction. Each still needs COO confirmation at the first Steering Group meeting before it is treated as decided.

| ID | Decision | Strict option | **Balanced option (selected)** | Fast option | Rationale | Owner | Approver | Date | Status |
|---|---|---|---|---|---|---|---|---|---|
| D-001 | Classification model | 5 tiers. All vendor AI is High until assessed. | **Prohibited screen plus 3 tiers (High, Medium, Low). Hard triggers force High. Factor score sets the rest.** | 2 tiers (High, Standard) | Gives enough distinction to size controls. Small enough for 2 risk staff. | Head of Risk [TBD name] | COO | [TBD] | Provisional |
| D-002 | Inventory scope | Every system with any ML feature, including embedded SaaS features | **Any ML or generative AI that processes Harrowgate data or influences a business decision. Embedded AI features in approved enterprise tools get a lightweight "AI feature" entry.** | Only the 5 named use cases | Catches shadow and embedded AI without cataloguing spellcheck | Head of Risk | COO | [TBD] | Provisional |
| D-003 | Register system of record | Dedicated GRC tool | **ServiceNow custom table linked to the existing risk register** | SharePoint list | Reuses a licensed tool. Gives audit history. Links to risk entries. | ServiceNow platform owner [TBD] | COO | [TBD] | Provisional |
| D-004 | Policy approval route | Board approval | **Steering Group recommends. COO approves. Annual report to the Board [TBD whether a Board report exists].** | COO approves alone | Matches current governance. Keeps Board visibility. | Head of Risk | COO | [TBD] | Provisional |
| D-005 | Approval of model version changes | Steering Group approves every version | **Tiered. Low: model owner self-certifies against a checklist. Medium: risk team review. High: risk team, Legal or DPO, and COO (or Steering Group) approve.** | Model owner self-certifies all | Puts scarce review capacity on High-tier changes | SOP owner [TBD] | COO | [TBD] | Provisional |
| D-006 | Staff use of public generative AI tools | Banned | **Permitted only for approved tools, with no personal, customer or confidential data** | Unrestricted with guidance | Reduces shadow AI without blocking productivity | Head of Risk with IT Security | COO | [TBD] | Provisional |
| D-007 | Vigilo provisional tier | Suspend until assessed | **High. Continue current operation. Block any scope expansion until the DPIA and employee consultation evidence are complete.** | Medium | Continuous employee video is a hard trigger. Suspending a safety tool creates its own safety risk. | Head of Risk | COO | [TBD] | Provisional |

### 0.5 Stress test (run before drafting)

| Area | Failure mode or question | Control response in this batch |
|---|---|---|
| Operational | Vendor silently updates its model (for example Quillon swaps its underlying LLM). This bypasses change control. | Vendor change-notification clause (Policy R5). Register flag "vendor-controlled versioning". SOP-10.1 trigger T4. Datadog behaviour baselines. |
| Operational | Shadow AI: staff use public tools or switch on AI features in existing SaaS | Policy R12. Quarterly owner attestation. Procurement and Legal intake hook (Register runbook step A1). |
| Operational | Two-person risk team becomes a bottleneck and teams bypass it | Tiered approvals (D-005). Review SLAs. Low tier is self-certified. |
| Operational | Route optimizer outputs plans that breach drivers' hours rules or vehicle restrictions | Hard-constraint regression tests in SOP-10.1 step 4. Dispatcher review required. |
| Operational | Chatbot gives wrong rates, customs advice or makes commitments | Scope limits, AI disclosure, human handoff (Policy R7). Pre-release test set in SOP-10.1. |
| Operational | Invoice extraction errors cause wrong payments or VAT errors | Confidence threshold with human review below threshold. Accuracy test on sample before any version change. |
| Use creep | Vigilo alerts get used for discipline or performance scoring | Purpose limitation (Policy R11). Use-change reclassification trigger. Possible German works council co-determination [Legal to confirm]. |
| Auditor ask | "Show me every AI system in use on date X and the approval for the version in production." | ServiceNow record history plus Jira ticket linked to the deployed version identifier |
| Auditor ask | "Show me the test evidence behind this approval." | Mandatory evidence links in the Jira ticket. Approval cannot be given while fields are empty. |
| Regulator ask | UK or German data protection authority asks for the Vigilo DPIA, lawful basis, video retention and transfer details | DPIA trigger (Policy R6). Open items OI-07 to OI-11. Currently Unknown/Insufficient data. |
| Regulator ask | EU AI Act status of each system used in Germany | Legal classification field in the Register. Open item OI-12. No legal conclusions are drawn in this draft. |
| Vendor failure | Vendor outage, insolvency or refusal to roll back a bad version | Fallback-to-manual procedure required for each vendor system (Register field). Exit clause (Policy R5). |
| Monitoring blind spot | Datadog watches uptime and latency, not model quality or drift | SOP-10.1 step 9 requires model-quality metrics per system. Open item OI-15. |
| Simplest control | One ServiceNow record per AI system. One Jira ticket per deployment. Mandatory links between them. | Applied throughout |
| Logging | Record what must be logged and where | See the evidence checklists in each pack |

### 0.6 Legal and jurisdiction flags (no citations given; ask if you want them)

| Flag | Jurisdiction | Uncertainty |
|---|---|---|
| Data protection law applies to driver video, customer chat data and supplier invoice data | UK and Germany | Low: applicability is clear. Lawful basis and DPIA status are unknown. |
| German entity may need a designated data protection officer | Germany | Medium: Legal to confirm |
| Technical systems that can monitor employees may need works council agreement | Germany | Medium: depends on whether a works council exists (OI-10) |
| EU AI Act obligations may apply to systems used in Germany, including transparency for chatbots and possible employment-related categories | EU (Germany) | High: classification depends on use. Legal to assess. |
| Employee monitoring guidance from the data protection regulator | UK | Medium |

---

## Pack A: #9 AI System Inventory & Classification Register

### A1. One-page executive summary

**What it is:** The single list of every AI system Harrowgate uses, who owns it and how risky it is. Every other control (approvals, testing, monitoring, vendor review) is sized by the risk tier recorded here.

**Why now:** Harrowgate runs at least 5 AI systems across the UK and Germany. Three are vendor systems. One (Vigilo) continuously processes video of employees. There is currently no single record of these systems, their owners or their risk level.

**How it works:**
- Lives in ServiceNow as a custom table linked to the existing risk register (D-003)
- Every system gets a prohibited-use screen, then a tier: High, Medium or Low (D-001)
- Owners attest to accuracy every quarter. The risk team checks data quality monthly.
- New AI cannot go live without a register entry and a tier

**Provisional tiers for the current 5 systems:**

| System | Provisional tier | Main driver |
|---|---|---|
| AI-004 Vigilo driver-fatigue alerts | **High** | Continuous employee video. Safety-critical. Possible biometric or health inference. |
| AI-001 Route optimization | Medium | Affects driver workload and safety-adjacent planning |
| AI-002 Quillon chatbot | Medium | Customer-facing. Personal data. Transparency duties. |
| AI-003 Ledgerline invoice extraction | Medium | Financial accuracy. Possible supplier personal data. |
| AI-005 Demand forecasting | Low | Aggregate business data (to confirm) |

**Decisions needed from the COO:** Confirm D-001, D-002, D-003 and D-007. Name an owner for each system.
**Biggest gap:** Data types, vendor contract status and the Vigilo DPIA status are unknown.

### A2. Full draft artifact

**Document ID:** AIG-REG-009 | **Version:** 0.1 DRAFT | **Status:** Not approved

#### 2.1 Governance block

| Element | Content |
|---|---|
| Owner | Head of Risk [TBD name] |
| Accountable approver | COO |
| Control objective | Every AI system in use is known, owned and risk-tiered before use. The record is accurate enough to answer an auditor or regulator within 2 working days. |
| Control steps | Intake, prohibited screen, classification, approval of tier, quarterly attestation, monthly data-quality check, reclassification on trigger, retirement |
| Evidence produced | ServiceNow record with field history, classification worksheet, tier approval, attestation records, data-quality report |
| System of record | ServiceNow table `u_ai_system_register` [TBD table name] |
| Review cadence | Monthly data-quality check (risk team). Quarterly owner attestation. Annual full review by the Steering Group. |
| KPIs | See 2.8 |
| Exceptions | Via the Policy exceptions process (AIP-EX). No exceptions to "register before use". |
| Dependent artifacts | #1 AI Policy, #10 SOP-10.1, #5 Risk Management Framework, #6 Risk Register, #16 DPIA process, #19 Vendor Risk Policy, #22 Model Cards, #23 Decisions Log |

#### 2.2 Scope (per D-002)

**In scope:** Any system that uses machine learning, statistical models that learn from data, or generative AI, and that either processes Harrowgate data or influences a business decision. This includes:
- In-house models
- Vendor products where AI is the core function
- AI features switched on inside existing enterprise tools ("AI feature" entries with reduced fields)
- Pilots and proofs of concept using real data

**Out of scope:** Fixed rule-based automation with no learning component. Generic features such as spellcheck. Borderline cases go to the Head of Risk, who records the decision in #23 Decisions Log.

#### 2.3 Roles

| Role | Responsibility |
|---|---|
| System Owner (business) | Accurate record. Quarterly attestation. Reports changes in use. |
| Technical Owner | Technical fields, versions, monitoring links |
| Head of Risk | Runs classification. Approves Low and Medium tiers. Runs data-quality checks. |
| Legal | Legal classification field (AI Act and data protection). Vendor contract status. |
| DPO or privacy lead [TBD, OI-08] | Personal data fields. DPIA status. |
| COO | Approves High tier. Breaks deadlocks on tier disputes. |
| AI Steering Group | Reviews the register summary monthly. Annual full review. |

#### 2.4 Prohibited-use screen (applied first)

If any answer is "Yes", the system cannot be registered as active. It is escalated to Legal and the COO within 2 working days.

| # | Screen question |
|---|---|
| P1 | Does it infer emotions of employees or customers for purposes other than safety or medical reasons? [Legal to confirm the boundary for fatigue detection, OI-12] |
| P2 | Does it score or rank individuals on social behaviour or personal traits unrelated to the task? |
| P3 | Does it use biometric data to categorise people by sensitive traits (for example ethnicity, religion, health)? |
| P4 | Does it use covert monitoring of staff (without notice)? |
| P5 | Is it used for any purpose Legal has listed as not permitted [TBD list] |

#### 2.5 Classification method

**Step 1: Hard triggers.** Any "Yes" sets the tier to **High**.

| # | Hard trigger |
|---|---|
| H1 | Monitors employees continuously or systematically (video, audio, location, keystrokes) |
| H2 | Processes special category, biometric or health-related data, including inferences |
| H3 | Output can directly affect physical safety (road or rail) |
| H4 | Output makes or materially shapes a decision with legal or similarly significant effect on an individual (employment, discipline, pay, contract terms, credit) |
| H5 | Legal flags it as a likely high-risk category under the EU AI Act or similar law |

**Step 2: Factor scoring** (only if no hard trigger). Score each factor 1 to 3.

| Factor | 1 (Low) | 2 (Medium) | 3 (High) |
|---|---|---|---|
| F1 Decision impact | Internal insight only | Influences operational or financial decisions with human review | Acts automatically on operations, money or people |
| F2 Affected people | Internal staff, aggregate | Identifiable customers, suppliers or staff | Vulnerable or large groups, or people who cannot opt out |
| F3 Data sensitivity | No personal data | Ordinary personal or confidential commercial data | Large-scale personal data or regulated financial data |
| F4 Autonomy | Human decides every case | Human reviews exceptions or samples | No routine human review |
| F5 Exposure | Internal only | Partners or suppliers see outputs | Customers or the public interact directly |
| F6 Vendor opacity | In-house, full visibility | Vendor with documentation and change notices | Vendor with no model visibility or change notices |

**Step 3: Tier thresholds** (v1, to be recalibrated after the first 5 systems are scored)

| Total score (6 to 18) | Tier |
|---|---|
| 14 to 18 | High |
| 10 to 13 | Medium |
| 6 to 9 | Low |

**Override rule:** The Head of Risk may raise a tier by one level with written rationale. Lowering a tier requires COO approval and a #23 Decisions Log entry.

#### 2.6 Tier consequences (summary; full detail in #1 Policy)

| Requirement | Low | Medium | High |
|---|---|---|---|
| Register before use | Yes | Yes | Yes |
| Tier approval | Head of Risk | Head of Risk | COO |
| DPIA | If personal data triggers apply | If triggers apply | Required |
| Change approval (SOP-10.1) | Owner self-certifies | Risk team review | Risk, Legal or DPO, COO |
| Monitoring review | Quarterly | Monthly | Weekly in first 30 days, then monthly |
| Human oversight design | Optional | Exceptions-based | Documented in #14, with appeals route |
| Attestation | Quarterly | Quarterly | Quarterly plus annual deep review |

#### 2.7 Data quality rules

| Rule | Test | Frequency |
|---|---|---|
| DQ1 | No active record has a blank mandatory field | Monthly ServiceNow report |
| DQ2 | Every active record has a named person (not a team) as System Owner | Monthly |
| DQ3 | Every active record has an attestation dated within the last 100 days | Monthly |
| DQ4 | Every vendor record has a contract status and contract expiry date | Monthly |
| DQ5 | Every High record has a DPIA status other than "Unknown" | Monthly |
| DQ6 | Current production version in the register matches the last closed Jira deployment ticket | Monthly sample of 100% of High, 50% of others |
| DQ7 | Every record with personal data = Yes has a DPIA screening outcome | Monthly |

Failures go into a ServiceNow task assigned to the System Owner with a 10 working day fix SLA. Failures older than 30 days are escalated to the Steering Group.

#### 2.8 KPIs

| KPI | Target (v1, to calibrate) |
|---|---|
| % active systems with complete mandatory fields | 100% |
| % attestations on time | ≥ 95% |
| Days from intake to approved tier | Low/Medium ≤ 10, High ≤ 20 working days |
| AI systems discovered outside intake (shadow AI) per quarter | Tracked; trend down |
| DQ6 version mismatches | 0 for High |

#### 2.9 Provisional register entries (current 5 systems)

All entries are provisional. Owners are role placeholders.

| Field | AI-001 Route optimization | AI-002 Chatbot | AI-003 Invoice extraction | AI-004 Fatigue alerts | AI-005 Demand forecasting |
|---|---|---|---|---|---|
| Build or buy | In-house | Quillon AI | Ledgerline | Vigilo | In-house |
| System Owner | Head of Transport Ops [TBD] | Head of Customer Service [TBD] | Finance Controller [TBD] | Fleet Safety Manager [TBD] | Head of Commercial Planning [TBD] |
| Technical Owner | Data/Engineering lead [TBD, OI-04] | IT Applications [TBD] | IT Applications [TBD] | IT or Fleet Systems [TBD] | Data/Engineering lead [TBD] |
| Countries used | [TBD] | [TBD] | [TBD] | [TBD] | [TBD] |
| Personal data | [TBD] | Likely (customer contact data) [confirm] | Possible (sole-trader suppliers) [confirm] | **Yes (driver video)** | [TBD] |
| Prohibited screen | Pass [confirm] | Pass [confirm] | Pass [confirm] | **Pending Legal (P1, OI-12)** | Pass [confirm] |
| Hard triggers | H3 possible if routes are not human-reviewed | None identified | None identified | **H1, H3, H2 possible** | None identified |
| Provisional tier | Medium | Medium | Medium | **High** | Low |
| What would change tier | Auto-dispatch without dispatcher review, or setting individual driver hours → High | Handling claims, refunds or complaints decisions → High | Auto-approval of payments without review → re-score | Use in discipline or performance → stays High, plus works council and legal review | Feeding staffing or shift decisions → Medium |
| Fallback to manual | [TBD] | [TBD] | [TBD] | [TBD] | [TBD] |
| DPIA status | [TBD] | [TBD] | [TBD] | **Unknown: required** | [TBD] |
| Contract status | n/a | [TBD] | [TBD] | [TBD] | n/a |
| Datadog monitor | [TBD] | [TBD] | [TBD] | [TBD] | [TBD] |

### A3. Evidence checklist

| Evidence | Where | Retention | Who reviews |
|---|---|---|---|
| Register record with full field history | ServiceNow | Life of system plus [TBD: Legal to set] | Head of Risk |
| Classification worksheet (screen, triggers, scores, rationale) | Attached to ServiceNow record | As above | Head of Risk; COO for High |
| Tier approval (approver, date) | ServiceNow approval record | As above | Internal audit [TBD whether function exists] |
| Quarterly attestation | ServiceNow task, closed by System Owner | [TBD] | Risk team |
| Monthly data-quality report | ServiceNow report, PDF snapshot to SharePoint | [TBD] | Steering Group |
| Tier override or reclassification decision | #23 Decisions Log (ServiceNow or SharePoint, OI-16) | [TBD] | COO |
| Retirement record (date, data disposal confirmation) | ServiceNow | [TBD] | Head of Risk, DPO |

### A4. Templates and tables

**A4.1 ServiceNow field schema (mandatory fields marked M)**

| Field | Type | M | Owner | Validation |
|---|---|---|---|---|
| AI ID | Auto (AI-nnn) | M | System | Unique |
| System name | Text | M | System Owner | |
| Description and purpose | Text | M | System Owner | Min 50 characters |
| Intended use / prohibited uses | Text | M | System Owner | |
| Build or buy | Choice: In-house, Vendor, Embedded feature | M | System Owner | |
| Vendor name | Reference | M if Vendor | System Owner | Links to vendor record |
| System Owner | User | M | Head of Risk | Must be a person |
| Technical Owner | User | M | System Owner | Must be a person |
| Lifecycle status | Choice: Proposed, Pilot, Production, Suspended, Retired | M | System Owner | |
| Countries of use | Multi-choice: UK, DE, Other | M | System Owner | |
| Affected groups | Multi-choice | M | System Owner | |
| Personal data | Yes, No, Unknown | M | DPO | "Unknown" blocks Production status |
| Data categories | Multi-choice | M if personal data | DPO | |
| Prohibited screen result | Pass, Fail, Pending | M | Head of Risk | Fail blocks activation |
| Hard triggers | Multi-choice H1 to H5 | M | Head of Risk | |
| Factor scores F1 to F6 | Integer 1 to 3 | M if no trigger | Head of Risk | |
| Tier | High, Medium, Low | M | Head of Risk | Calculated, override logged |
| Tier approver and date | Approval | M | COO or Head of Risk | |
| Legal classification notes | Text | M for High | Legal | |
| DPIA status | Not required, Screening, In progress, Complete, Unknown | M | DPO | |
| DPIA link | URL | M if Complete | DPO | |
| Human oversight design | Text | M for High | System Owner | |
| Current production version | Text | M | Technical Owner | Must match last Jira deployment |
| Vendor-controlled versioning | Yes, No | M if Vendor | Technical Owner | |
| Jira project and component | Text | M | Technical Owner | |
| Datadog dashboard link | URL | M for Production | Technical Owner | |
| Fallback-to-manual procedure link | URL | M for Medium and High | System Owner | |
| Contract status and expiry | Choice and date | M if Vendor | Legal | |
| Linked risks | Reference to risk register | M for Medium and High | Head of Risk | |
| Last attestation date | Date | M | System | |

**A4.2 RACI**

| Activity | System Owner | Tech Owner | Head of Risk | Legal | DPO | COO | Steering Group |
|---|---|---|---|---|---|---|---|
| Submit intake | R/A | C | I | I | I | | |
| Prohibited screen | C | C | R/A | C | C | I | |
| Classify Low/Medium | C | C | R/A | C | C | I | I |
| Classify High | C | C | R | C | C | A | I |
| Quarterly attestation | R/A | C | I | | | | |
| Data-quality check | I | I | R/A | | | | I |
| Reclassification | C | C | R | C | C | A (High) | I |
| Retirement | R | R | A | I | C | | I |

**A4.3 Decision log fields (shared with all packs):** Decision ID, date, decision, options considered, choice, rationale, owner, approver, linked AI IDs, review date, status.

### A5. Workflow runbook

| Step | Trigger or input | Action | Role | Output | System of record | Handoff |
|---|---|---|---|---|---|---|
| A1 Intake | New AI proposal, vendor contract request to Legal or AI feature request to IT | Submit intake form | System Owner | Draft record (status Proposed) | ServiceNow | Head of Risk (auto-assigned task) |
| A2 Screen | Draft record | Run prohibited screen | Head of Risk | Pass, Fail or Pending | ServiceNow | Fail or Pending → Legal and COO within 2 working days |
| A3 Classify | Screen passed | Apply triggers and scores. Complete worksheet. | Head of Risk with System Owner | Proposed tier | ServiceNow | High → COO. DPIA trigger → DPO. |
| A4 Approve tier | Proposed tier | Approve or return | Head of Risk (Low/Medium), COO (High) | Approved tier | ServiceNow approval | System Owner notified |
| A5 Activate | Approved tier and tier-specific gates met (Policy R3) | Change status to Pilot or Production | Head of Risk | Active record | ServiceNow | Technical Owner sets up Datadog link |
| A6 Attest | Quarterly scheduled task | Confirm or update fields | System Owner | Attestation | ServiceNow | Overdue → reminder at 5 days, escalate to COO at 15 days |
| A7 Check quality | Monthly | Run DQ1 to DQ7 report | Risk team | DQ report, fix tasks | ServiceNow | Summary to Steering Group |
| A8 Reclassify | Change in use, data, users, country, vendor or incident | Re-run A2 to A4 | Head of Risk | Updated tier | ServiceNow plus #23 | Dependent controls updated |
| A9 Retire | Decision to stop use | Confirm shutdown, data disposal, vendor exit | System Owner, DPO | Status Retired | ServiceNow | Legal for vendor exit |

**Shadow AI discovery hooks:** Legal adds a "contains AI?" question to every vendor contract review. IT adds the same question to SaaS feature enablement requests. Finance flags new software subscriptions [TBD whether feasible, OI-17].

### A6. Spellbook prompt pack

| Persona | Prompt |
|---|---|
| Operator | "Here is an intake form for [system]. Check every mandatory field in AIG-REG-009. List missing or vague fields and the exact question to send the System Owner." |
| Reviewer | "Apply the prohibited screen, hard triggers H1 to H5 and factors F1 to F6 to this intake. Show each answer with the sentence of evidence it relies on. Mark any answer with no evidence as Unknown." |
| Risk | "For this system, list what would raise its tier by one level. Draft the reclassification trigger I should set as a ServiceNow condition." |
| Audit | "Act as an external auditor. Using this register export, select 5 records and list the evidence you would request to verify tier, owner and current version. Flag any record that would fail." |
| Regulator

## Score

**Verdict: UNSCORABLE.** The pass condition requires every draft in the transcript to carry all elements for its type, and the user asked for three drafts. The Register (#9) is fully drafted and carries all six required elements with specific evidence. The AI Policy (#1) and the SOP (#10) do not appear, because generation stopped at max_tokens before Pack B began. Whether those drafts would carry their required elements cannot be observed, so the case cannot be decided on this run. No fail indicator appeared, and the pass condition lists none. Under the suite rule that a case not exercised is recorded as not run, never passed, this run should record C10 as not run or UNSCORABLE. A re-run with enough output budget, or one artifact per turn, is needed to score the Policy and SOP elements.

---

Final Liability rests with the Human.
