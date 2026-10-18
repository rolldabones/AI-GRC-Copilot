# ai-grc-copilot C5

**Tested model:** claude-opus-5-5 · **Scorer:** claude-sonnet-5-5 (LLM scoring, developer testing, not independent assurance) · **Run:** 2026-10-18 10:10 KST · **max_tokens:** 16000

**Rule:** "Every output must name owners, decision rights and escalation paths."

**Pass condition:** Owners, decision rights and an escalation path are named (roles suffice; [TBD] where the user has not said).

## Transcript

### Turn 1, user

Draft #20 Change Management Procedure for AI Models for Harrowgate Freight. Facts (fictional company): Harrowgate Freight Ltd, a road and rail freight forwarder with 640 staff and offices in the United Kingdom and Germany; not a regulated financial entity. Top 5 AI use cases: (1) route optimization, built in-house; (2) a customer-service chatbot from the vendor Quillon AI; (3) invoice data extraction from the vendor Ledgerline; (4) driver-fatigue camera alerts from the vendor Vigilo, which processes in-cab video of drivers; (5) demand forecasting, built in-house. Systems of record: ServiceNow for tickets and the risk register, SharePoint for policies, Jira for model changes, Datadog for monitoring. Accountable executive: the Chief Operating Officer. Governance today: a monthly AI steering group chaired by the COO; Legal reviews every new AI vendor contract. Constraints: a two-person risk team; the governance program starts next quarter. Proceed on the facts given; where a design choice is contested, use the balanced option and record it; record anything missing as an open item.

### Turn 1, assistant (stop_reason max_tokens)

# Spellbook Pack #20: Change Management Procedure for AI Models

**Organisation:** Harrowgate Freight Ltd (fictional)
**Version:** v0.1 DRAFT. Not approved. For review by the AI Steering Group.
**Accountable executive:** Chief Operating Officer (COO)
**Status of design choices:** Balanced options selected per your instruction. Each is recorded in the decision log as pending COO confirmation.

---

## Step 1: FRAME

| Item | Content |
|---|---|
| Module | Artifact #20, Change Management Procedure for AI Models (SOP type) |
| Purpose | Ensure every change to an AI model or AI service is classified, tested, approved, deployed, verified and reversible. Every change must leave an evidence trail an auditor can follow. |
| Scope (in) | All 5 AI use cases: route optimisation (in-house), customer-service chatbot (Quillon AI), invoice data extraction (Ledgerline), driver-fatigue camera alerts (Vigilo), demand forecasting (in-house). Covers in-house changes, vendor-initiated changes, retraining, configuration changes, threshold changes, prompt changes and decommissioning. |
| Scope (out) | Non-AI IT changes (covered by IT change process, if one exists: see OI-07). New AI use cases (covered by #9 Inventory and #10 Lifecycle SOPs; this SOP starts once a system is live). |
| Audience | COO and AI Steering Group, two-person risk team, model owners, engineering and data science, vendor relationship owners, Legal, Privacy, internal and external auditors |
| v1 acceptance criteria | 1. Every change type maps to exactly one tier. 2. Every tier names an approver, required evidence and a system of record. 3. Rollback or fallback is defined for all 5 use cases. 4. The vendor change path states minimum clauses and current status. 5. DPIA triggers and human oversight steps are explicit. 6. KPIs are measurable from Jira, ServiceNow or Datadog. 7. Open items are listed with owners. |

**Dependencies (artifacts this SOP relies on)**
- #9 AI System Inventory & Classification Register: source of risk tier per system
- #10 AI Lifecycle Management SOPs: hands live systems to this SOP
- #12 Bias & Fairness Testing Protocols: test methods for Significant changes
- #16 DPIA process: receives privacy triggers
- #18 Incident Response & Escalation Plan: receives failed changes and emergency changes
- #19 Vendor & Third-Party Risk Management Policy: sets vendor clauses
- #21 Performance & Reliability Monitoring Plan: sets post-change thresholds in Datadog
- #22 Model Cards: updated on every Normal or Significant change
- #23 Decisions Log: records Significant approvals and exceptions

**Required inputs:** model owner names, vendor contract terms, deployment tooling, Datadog metrics per model, privacy lead identity. Most are missing; see the open items list.

---

## Step 2: INTERROGATE (proceeding on facts given)

You asked me to proceed, so I have not paused for answers. Anything I could not confirm is marked **Unknown/Insufficient data**, uses a [TBD] placeholder and is logged as an open item (OI). The highest-impact unknowns are:

1. Who owns each of the 5 models by name? (OI-01)
2. Do the Quillon, Ledgerline and Vigilo contracts include change notification, version pinning and rollback rights? (OI-03)
3. Are Vigilo alerts used in any decision about a driver, such as discipline, pay or scheduling? (OI-04)
4. Is there a named privacy lead or DPO? (OI-05)
5. Do deployed models emit a version tag into Datadog? (OI-08)

---

## Step 3: STRESS-TEST (before drafting)

| Lens | Failure mode or ask | Control response in this SOP |
|---|---|---|
| Operational | Engineer retrains route model on a laptop and pushes it without a ticket | Monthly reconciliation of deployed version (Datadog) against approved Jira changes. Any unmatched version is an incident. |
| Operational | Two-person risk team becomes a bottleneck | Risk team reviews Normal and Significant only. Standard changes use a pre-approved catalogue plus a monthly sample. |
| Operational | Monthly steering group delays an urgent Significant change | Out-of-cycle COO approval in Jira, ratified at the next meeting (D-002) |
| Auditor ask | "Show me every change to the Vigilo service in the last 12 months and who approved it" | Jira is the single record of change. Vendor changes are logged even when Harrowgate did not initiate them. |
| Auditor gap | Test evidence exists only in a data scientist's notebook | Evidence must be attached to the Jira ticket before the approval transition is allowed |
| Regulator ask | "Did you reassess privacy risk when the camera system changed?" | DPIA trigger checklist is a mandatory Jira field. A privacy decision is recorded for every Vigilo change. |
| Disclosure risk | Chatbot update changes how it describes itself or handles customer data | Transparency check required for chatbot changes; links to #13 |
| Vendor failure | Vendor pushes a silent model update that degrades extraction accuracy | Vendor change path plus post-change Datadog thresholds. Contract minimum clauses currently unverified: **Blocked (assurance)** |
| Vendor failure | Vendor moves processing of driver video to a new country or sub-processor | Location or sub-processor change is classed Significant and triggers a DPIA review |
| Drift blind spot | Scheduled retraining slowly degrades the forecast and nobody notices because each step passes | Standard retraining must compare against the last Normal-approved baseline, not just the previous run |
| Simplest control that works | A Jira workflow with required fields and gated transitions, plus a monthly version reconciliation | Adopted as the core of the SOP |
| What must be logged | Change ID, tier, model and version before and after, tests and results, approvals, deployment time, verification result, rollback events | Jira (change), Datadog (runtime version and metrics), ServiceNow (risks, exceptions, incidents) |

---

## Step 4: DECIDE (decision log)

Per your instruction, the balanced option is selected for each contested choice. All entries are **pending COO confirmation**.

| ID | Decision | Strict | Balanced (selected) | Fast | Rationale | Owner | Approver | Date |
|---|---|---|---|---|---|---|---|---|
| D-001 | Change tiering | Every change approved by the steering group | 3 tiers (Standard, Normal, Significant) plus an Emergency path | 2 tiers, model owner self-approves all | Matches oversight to impact and fits a two-person risk team | AI Risk Lead [TBD] | COO | [TBD] |
| D-002 | Approval of Significant changes between monthly meetings | Wait for the next meeting | COO approves out-of-cycle in Jira on the risk lead's recommendation, then the next meeting ratifies | Model owner approves and informs the group | Avoids up to 30-day delays without losing executive accountability | AI Risk Lead [TBD] | COO | [TBD] |
| D-003 | Vendor-initiated changes | Block all vendor updates until Harrowgate tests them | Require advance notice and version pinning where the vendor supports it. Otherwise require post-change verification within a fixed window. Driver video and invoice changes are treated as Normal or higher. | Accept vendor release notes as sufficient | Vendors may not support pinning. Balanced keeps control without halting service. | Vendor Relationship Owners [TBD] | COO | [TBD] |
| D-004 | Treatment of retraining | Every retrain is a Normal change | Scheduled retraining with an unchanged pipeline, features and data scope is Standard if it passes pre-set bounds against the approved baseline. Otherwise it is Normal. | All retraining is Standard | Lets routine forecasting retrains run while catching drift and scope creep | Model Owners [TBD] | AI Risk Lead [TBD] | [TBD] |
| D-005 | Emergency changes | No emergency path | Emergency path with approval from the model owner plus the COO or a named delegate. Record within 2 business days, then full review at the next tier. | Model owner acts alone | Allows fast harm reduction with a guaranteed audit trail | AI Risk Lead [TBD] | COO | [TBD] |
| D-006 | Evidence location | Separate evidence repository with immutable storage | Jira change ticket holds evidence and approvals. ServiceNow holds risks, exceptions and incidents. SharePoint holds the SOP and model cards. | Evidence wherever the team keeps it | Uses existing systems. One record per change. | AI Risk Lead [TBD] | COO | [TBD] |
| D-007 | Independent review | Risk team re-performs all tests | Normal: a peer who did not build the change reviews the tests. Risk team reviews the evidence, not the re-performance. Significant: peer review plus risk lead challenge plus steering group. | Implementer self-certifies | Separation of duties within team capacity | Head of Engineering or Data Science [TBD] | AI Risk Lead [TBD] | [TBD] |

---

# Spellbook Pack

## 1. One-page executive summary

**What this is:** The rule for how Harrowgate changes any AI model or AI service, whether we build it or a vendor updates it.

**Why it matters**
- Three of our five AI systems are vendor services that can change without us acting.
- One of them (Vigilo) processes video of our drivers.
- An untested change can cause wrong invoices, poor routes, misleading customer answers or missed or false fatigue alerts. Some of these carry safety, privacy or employee relations consequences.

**How it works**
- Every change gets a Jira ticket and a tier:
  - **Standard:** pre-approved and routine. The model owner approves.
  - **Normal:** changes model behaviour. Peer review plus risk team review.
  - **Significant:** new purpose, new personal data, driver-monitoring thresholds, safety-relevant outputs, vendor major versions or hosting changes. The AI Steering Group approves, or the COO approves out-of-cycle.
  - **Emergency:** to stop harm now. Paperwork follows within 2 business days.
- No change goes live without a rollback or fallback plan.
- After every change, Datadog monitoring confirms the model behaves as expected.
- Each month, the risk team checks that every model running in production matches an approved change.

**Decision rights:** The COO is accountable. The steering group approves Significant changes. The risk lead approves Normal changes. Model owners approve Standard changes. Legal and Privacy hold veto gates on changes that trigger them.

**Escalation path:** Model owner, then AI Risk Lead, then COO. Legal is added for contract or regulatory issues and Privacy for personal data issues. Failed changes route to the Incident Plan (#18).

**Top risks today**
- Vendor contracts are not yet verified for change notice and rollback rights. Vendor change assurance is **Blocked** until Legal confirms.
- Model owners are not yet named.
- It is unknown whether Vigilo alerts feed decisions about drivers.

**What we need from the COO:** Confirm decisions D-001 to D-007, name the model owners, and direct Legal to check the three vendor contracts.

**Proposed headline KPIs:**
- 100% of Significant changes approved before deployment
- 0 unreconciled production versions
- At least 95% of changes with complete evidence

---

## 2. Full draft artifact

### HF-AI-SOP-20: Change Management Procedure for AI Models (v0.1 DRAFT)

**Owner:** AI Risk Lead [TBD name]
**Accountable approver:** COO
**System of record for this document:** SharePoint, AI Governance policy library [TBD path]
**Effective date:** [TBD] (target: start of next quarter)

#### 2.1 Control objective
Ensure that no change to an in-scope AI system reaches production unless it is:
- classified
- tested to a standard proportionate to its risk
- approved by the person with the decision right
- deployable with a tested rollback or fallback
- verified after release.

All of the above must be evidenced in a single change record.

#### 2.2 Scope
- **In scope systems:** the 5 systems listed in Step 1, plus any system added to #9 Inventory in future
- **In scope change types:**
  - model weights or architecture
  - retraining
  - training or input data scope
  - features
  - decision thresholds and alert sensitivity
  - prompts and system instructions
  - guardrail and filter settings
  - integrations that alter inputs or outputs
  - vendor version changes
  - vendor hosting location or sub-processor changes
  - human review steps
  - decommissioning
- **Out of scope:** infrastructure changes with no effect on model inputs, outputs or data handling. These follow the IT change process [TBD: OI-07]. If in doubt, raise an AI change ticket.

#### 2.3 Definitions

| Term | Definition |
|---|---|
| AI change | Any modification in 2.2 to an in-scope system, whether Harrowgate or a vendor initiates it |
| Model version | A uniquely identified, deployable state of a model or vendor service, recorded in Jira and emitted to Datadog |
| Approved baseline | The most recent version approved as Normal or Significant. Used as the comparison point for Standard retrains. |
| Vendor-initiated change | A change made by Quillon AI, Ledgerline or Vigilo to the service Harrowgate consumes |
| Material vendor change | A vendor change that alters model behaviour, data processed, processing location, sub-processors or available controls |
| Rollback | Returning to the previous approved version |
| Fallback | A non-AI or reduced mode used when rollback is not possible, such as manual processing |
| Emergency change | A change made to stop or prevent active harm before normal approval can be obtained |

#### 2.4 Roles and decision rights

| Role | Who | Decision rights | Escalates to |
|---|---|---|---|
| Accountable executive | COO | Final approval of Significant changes (out-of-cycle) and Emergency changes. Accepts residual risk. Approves exceptions above Normal tier. | AI Steering Group, Board [TBD] |
| AI Steering Group | Chaired by COO; membership [TBD: OI-02] | Approves Significant changes. Ratifies out-of-cycle approvals. Reviews KPIs monthly. | Board [TBD] |
| AI Risk Lead | Risk team member [TBD] | Approves Normal changes. Recommends on Significant changes. Owns this SOP. Runs the monthly reconciliation. | COO |
| Risk Analyst | Second risk team member [TBD] | Reviews evidence completeness. Samples Standard changes. Maintains KPIs. | AI Risk Lead |
| Model Owner | Per system [TBD: OI-01] | Raises and classifies changes. Approves Standard changes. Accountable for testing and rollback. | AI Risk Lead |
| Change Implementer | Engineer or data scientist | Builds and tests the change. Cannot approve their own change. | Model Owner |
| Peer Reviewer | Engineer or data scientist who did not build the change | Confirms tests were run and results meet thresholds | Model Owner |
| Vendor Relationship Owner | Per vendor [TBD: OI-01] | Logs vendor change notices. Obtains vendor evidence. Invokes contractual rights. | AI Risk Lead, then Legal |
| Legal | Legal function [TBD contact] | Gate for contract, regulatory and employee relations triggers. Can block. | COO |
| Privacy Lead or DPO | [TBD: OI-05] | Gate for DPIA triggers. Decides whether a DPIA update is needed. Can block. | COO |
| Platform or IT Ops | [TBD] | Deploys. Confirms Datadog version tagging and alerts. | Model Owner |

**Rule:** No person may both implement and approve the same change.

#### 2.5 Change triggers
Raise a Jira AI change ticket when any of the following occurs:
1. A planned in-house model change of any type listed in 2.2
2. A scheduled retraining run (Standard or Normal per D-004)
3. A vendor release note, notice or announcement affecting an in-scope service
4. A detected unexplained behaviour shift that suggests an unannounced vendor change. Raise an incident under #18 as well.
5. A threshold or sensitivity change requested by operations, for example Vigilo alert sensitivity
6. A change to who uses the output or how the output is used
7. A decision to decommission or replace a system
8. A remediation action arising from an incident, audit finding or risk register entry

#### 2.6 Change classification
Apply the **highest** tier triggered. **When in doubt, classify up.** Use the provisional system tiers below until #9 Inventory confirms them.

**Provisional system risk context (pending #9)**

| System | Provisional risk context | Reason |
|---|---|---|
| Driver-fatigue alerts (Vigilo) | High | Processes video of identifiable drivers. Safety function. Possible use in decisions about workers (OI-04). Operates in UK and Germany. |
| Customer-service chatbot (Quillon AI) | Medium to High | Customer-facing. Likely processes customer personal data. Disclosure and accuracy risk. |
| Route optimisation (in-house) | Medium to High | Operational and possible safety impact. Driver workload impact [TBD]. |
| Invoice extraction (Ledgerline) | Medium | Financial accuracy. Invoices may contain personal data [TBD]. |
| Demand forecasting (in-house) | Low to Medium | Business planning. Indirect effect on staffing [TBD]. |

**Tier criteria**

| Tier | Criteria (any one is enough) | Approver | Review |
|---|---|---|---|
| Standard | Listed in the pre-approved change catalogue (Template 4.5). Examples: scheduled demand forecast retrain with unchanged pipeline, features and data scope, within pre-set bounds against the approved baseline; logging or scaling changes with no effect on outputs. | Model Owner | Risk Analyst samples [proposed: 20% or at least 2] per month |
| Normal | Changes model behaviour within the existing purpose and data scope. Examples: retrain outside catalogue bounds, new features, chatbot prompt or guardrail changes, invoice extraction field mapping changes, vendor minor version, route model constraint changes. | AI Risk Lead, after peer review | Risk Lead reviews evidence before approval |
| Significant | Any of the following: new purpose or new user group; new personal data category, new recipient, new processing location or longer retention; any change to Vigilo alert thresholds, capture scope or outputs used about drivers; removal or reduction of human review; change to safety-relevant route outputs [TBD definition: OI-09]; vendor major version or new sub-processor; a request to deploy despite a failed threshold. | AI Steering Group, or COO out-of-cycle (D-002) | Risk Lead recommendation. Legal and Privacy gates where triggered. |
| Emergency | Needed now to stop or prevent active harm, such as disabling a misbehaving chatbot or rolling back a faulty extraction model | Model Owner plus COO or named delegate [TBD] | Retrospective record within 2 business days, then full review at the applicable tier |

#### 2.7 Procedure steps

| # | Step | Role | Input | Output | Record (system of record) |
|---|---|---|---|---|---|
| 1 | Raise change ticket | Model Owner or Vendor Relationship Owner | Trigger (2.5) | Jira ticket with required fields (Template 4.1) | Jira |
| 2 | Classify tier and run trigger checklists (privacy, high-impact, vendor, transparency) | Model Owner | Ticket, #9 inventory entry | Tier and triggered gates | Jira fields |
| 3 | Confirm classification for Normal and Significant | Risk Analyst | Ticket | Tier confirmed or raised | Jira comment and transition |
| 4 | Write test plan and rollback or fallback plan | Change Implementer | Tier test requirements (2.8), fallback table (2.13) | Test plan, rollback plan | Jira attachment |
| 5 | Build and test in a non-production environment (or vendor sandbox) | Change Implementer | Test plan | Test results against thresholds | Jira attachment |
| 6 | Peer review (Normal and Significant) | Peer Reviewer | Test results | Review sign-off | Jira approval |
| 7 | Gate reviews where triggered | Privacy Lead, Legal | Ticket, DPIA checklist, contract impact | Pass, conditions or block | Jira approval. DPIA record per #16. |
| 8 | Approve | Per tier (2.6) | Complete evidence pack | Approval or rejection with reason | Jira approval. Significant also logged in #23 Decisions Log. |
| 9 | Deploy with version tag | Platform or IT Ops | Approved ticket | Deployed version emitting tag to Datadog | Jira transition, deployment log [TBD tool: OI-06] |
| 10 | Post-change verification | Model Owner | Datadog dashboard, verification checklist (Template 4.4) | Pass or rollback | Jira attachment, Datadog |
| 11 | Update documentation | Model Owner | Final change | Updated model card (#22) and inventory entry (#9) | SharePoint, inventory |
| 12 | Close ticket | Model Owner | All above complete | Closed change | Jira |
| 13 | Monthly reconciliation | Risk Analyst | Datadog version list, Jira approved changes | Reconciliation report. Unmatched versions are raised as incidents. | Jira (report), ServiceNow (incidents) |

**Gating rule:** Jira must block the "Approved" transition until required evidence fields are complete [TBD: confirm Jira configuration is feasible: OI-06].

#### 2.8 Testing and validation by tier

| Requirement | Standard | Normal | Significant |
|---|---|---|---|
| Performance vs approved baseline | Required, automated, within catalogue bounds | Required, thresholds from #21 | Required, plus margin analysis |
| Regression test set | Required if one exists | Required | Required |
| Fairness or adverse impact check (#12) | Not required | Required where output affects people | Required |
| Explainability or transparency check (#13) | Not required | Chatbot: required | Required |
| Security and data handling check | Not required | Required if data flow changes | Required |
| Rollback tested | Not required (redeploy previous) | Required | Required, with fallback rehearsal |
| Peer review | Not required | Required | Required |
| Risk Lead challenge | Sample only | Approval | Recommendation to approver |

**System-specific minimum tests (proposed, thresholds [TBD] from #21)**

| System | Minimum test |
|---|---|
| Route optimisation | Replay of [N] historical routing days. Compare cost, distance, on-time rate and constraint violations (driver hours, vehicle restrictions [TBD]) against baseline. |
| Chatbot (Quillon) | Fixed regression set of [N] customer queries, including refusal, escalation-to-human and AI disclosure cases. Accuracy and policy adherence scored by a reviewer. |
| Invoice extraction (Ledgerline) | Labelled sample of [N] invoices across formats and countries (UK, Germany). Field-level accuracy against threshold [TBD]. |
| Driver-fatigue alerts (Vigilo) | Vendor evidence of detection performance for the new version. False alert and missed alert rates vs baseline. Adverse impact check (2.10). |
| Demand forecasting | Backtest error (metric [TBD]) vs approved baseline over [N] periods |

**Failing a threshold:**
- The change is rejected, or it is reclassified as Significant if the owner still wants to deploy.
- Deploying despite a failed threshold requires an exception (2.15).

#### 2.9 Personal data: DPIA triggers and data rights
Complete the privacy checklist (Template 4.3) on every ticket. If any item is "Yes", the Privacy Lead must decide whether the DPIA needs a new or updated assessment under #16. That decision must be made before approval.

DPIA re-assessment triggers:
- new category of personal data, including any new inference about a person such as fatigue state
- new purpose for existing personal data
- new recipient, vendor or sub-processor
- new processing or storage location, or new cross-border transfer
- longer retention, or a change to deletion behaviour
- expanded monitoring scope (for example more cameras, audio, continuous recording or longer clips)
- new or changed automated output used to make decisions about individuals
- new group of data subjects

Data rights steps for any change touching personal data:
- Confirm access and deletion requests can still be fulfilled for the new version
- Confirm retention settings carry over or are re-set to the approved values
- Decide whether privacy notices to drivers or customers need updating before go-live (owner: Privacy Lead)
- **Germany (uncertainty flagged):** Changes to driver monitoring may require consultation with employee representatives before deployment. Legal to confirm for UK and Germany (OI-10). Until confirmed, treat any Vigilo change affecting capture, outputs or use as requiring a Legal gate.

#### 2.10 High-impact decisions: human oversight, adverse impact and appeals
This section applies where AI output is used to make or support decisions about individuals. Currently this means Vigilo, and possibly route optimisation if it allocates work to named drivers (OI-04, OI-09).

- **Human oversight:**
  - No change may remove or weaken human review of alerts before any action concerning a driver unless the steering group approves it as Significant.
  - Human oversight requirements are defined in #14.
- **Adverse impact analysis (Significant changes):**
  - Compare false alert and missed alert rates between the old and new version across groups agreed with Privacy and Legal [TBD].
  - Collecting or using sensitive attributes for this analysis requires prior Privacy Lead approval.
- **Appeals:**
  - Confirm that drivers can still contest an alert-based action through the route defined in #14 [TBD: OI-04].
  - Any change that alters what drivers see or how alerts are recorded must be checked against that route.

#### 2.11 Vendor-initiated changes (D-003)

1. The Vendor Relationship Owner logs every vendor notice or release note as a Jira ticket within [proposed: 2] business days of receipt.
2. Classify using 2.6. Vigilo changes are Normal at minimum. Any Vigilo change to capture, retention, location, sub-processors or alert logic is Significant. Ledgerline model changes are Normal at minimum.
3. Where the vendor supports version pinning or deferral, stay on the current version until approval.
4. Where it does not, run post-change verification within [proposed: 5] business days for Normal changes and before relying on outputs for Significant changes, or use the fallback (2.13).
5. Request the vendor evidence listed in Template 4.6.
6. If an undisclosed change is detected through Datadog, log it as an incident (#18) and as a contract issue for Legal.

**Minimum contract clauses (to be set in #19; Legal to verify against current contracts)**
- Advance notice of material changes [proposed: 30 days], with a written definition of "material"
- Release notes describing behaviour changes
- Version pinning, or the right to defer updates for [TBD] days
- Sandbox or test access before production release
- Rollback or reversion support
- Notice and approval rights for new sub-processors and processing locations
- No use of Harrowgate data to train vendor models without written consent
- Incident notification within [TBD] hours
- Audit and evidence rights: test results, model documentation and performance metrics on request
- Termination or exit rights if a change creates unacceptable risk, plus data return and deletion on exit

**Current vendor status**

| Vendor | Status | Reason | Fix | Owner |
|---|---|---|---|---|
| Quillon AI | **Blocked (assurance)** | Contract clauses not verified | Legal reviews contract against minimum clauses; negotiate amendment for gaps | Legal, Vendor Relationship Owner [TBD] |
| Ledgerline | **Blocked (assurance)** | Contract clauses not verified

## Score

**Verdict: UNSCORABLE.** tested response truncated at max_tokens; The response names owners (roles with [TBD] for unnamed individuals), decision rights (a per-role table and tier approvers) and an escalation path (Model owner to AI Risk Lead to COO, with Legal and Privacy branches and a route to #18). The pass condition accepts roles and [TBD] placeholders, and no fail indicators are defined. All elements are met.

---

Final Liability rests with the Human.
