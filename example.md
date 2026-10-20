# AI GRC Copilot: example run

Illustrative run, not a logged test run under the README's Change control rule. Produced on 18 October 2026 (KST) by Claude, in an agent session configured for `claude-opus-5-5`, following `instructions.md` as its operating instructions (not a bare system-prompt API call). Inputs are fictional.

Kestrel Haulage Group is a fictional company. The run drafts #6 AI Risk Register. It is one exchange: the user's input, then the instrument's output.

## User input

> Build the Spellbook Pack for #6 AI Risk Register.
>
> Org: Kestrel Haulage Group, road freight and warehousing, about 1,100 staff, operating in the Netherlands, Germany and Poland. Not a regulated financial entity.
>
> Top 5 AI use cases: (1) route and load optimization, built in-house; (2) driver fatigue camera alerts, vendor; (3) demand forecasting, vendor SaaS; (4) CV screening for driver hiring, vendor; (5) customer service chatbot on a vendor language model.
>
> Systems of record: Jira for tickets, SharePoint for documents, Datadog for monitoring. Accountable exec: Chief Operating Officer. We have an AI working group chaired by the Head of Risk. For scoring we pick the balanced option, a 5x5 likelihood by impact matrix. Budget and staffing: I don't know yet. Keep each part short.

## Output

### FRAME

- **Artifact:** #6 AI Risk Register (type: Register).
- **Purpose:** one place where every material AI risk at Kestrel is recorded, scored, owned and tracked to treatment, so that decisions and evidence can be produced on request.
- **Scope:** the five AI use cases named. Any new AI use case enters through #9 AI System Inventory & Classification Register before it is scored here.
- **Audience:** Chief Operating Officer (COO), Head of Risk, AI working group, system owners, internal audit.
- **v1 acceptance criteria:** every in-scope use case has at least one risk with an owner, a score or a dated [TBD], a treatment and a next review date; scales and thresholds stated; escalation path stated; open items listed.
- **Dependencies:** #4 RACI, #5 AI Risk Management Framework (risk appetite), #9 Inventory, #16 DPIA process, #18 Incident Response, #19 Vendor Policy, #21 Monitoring Plan, #23 Decisions Log.

### INTERROGATE

| Area | Supplied | Unknown/Insufficient data |
| --- | --- | --- |
| Org | Sector, about 1,100 staff, NL, DE and PL, not a regulated financial entity | Other regulated status; critical products and services |
| AI | Top 5 use cases and build or buy for each | Data types per use case; affected groups beyond drivers, applicants and customers; which outputs drive decisions without human review |
| Risk posture | None | Unacceptable failures; acceptable tradeoffs; escalation triggers |
| Governance | COO accountable; AI working group chaired by the Head of Risk | Legal review gate; whether any board committee receives AI risk reporting |
| Tooling and evidence | Jira, SharePoint, Datadog | Retention rules for each |
| Constraints | None | Timelines, staffing, budget limits, existing risk policy and enterprise risk register |

Short questions. Answer what you can; I proceed with [TBD] for the rest.

1. Which failures would be unacceptable to the COO, for example a missed fatigue alert before an accident or a driver applicant rejected with no human review?
2. Who in Legal reviews AI risks, and at which gate?
3. At what residual score must a risk reach the COO: 15 and above, or 20 and above?
4. Is there an enterprise risk register this one must feed, and in what system?
5. Does any fatigue alert feed disciplinary or performance decisions about drivers?

Proceeding with placeholders.

### STRESS-TEST (before drafting)

- **Operational failure modes:** the register becomes a list nobody updates; scores drift from facts; vendor use cases go unscored because nobody inside owns them.
- **Auditor asks and evidence gaps:** "Show me risk to control to evidence for the CV screening tool." Gap: no control IDs exist yet, so v1 links to #5 and #8 by [TBD] IDs.
- **Regulator asks and disclosure risks:** for CV screening and fatigue monitoring, expect to be asked who decided, what human oversight applies and what adverse impact analysis was done. Register text may be disclosed: record facts and decisions, not speculation.
- **Vendor failure scenarios:** four of five use cases are vendor-supplied. A vendor model update can change the risk with no change on Kestrel's side.
- **Drift and monitoring blind spots:** route optimization and demand forecasting degrade silently when demand patterns shift; nothing ties a Datadog alert to a re-score today.
- **Simplest control that works:** one Jira project, one issue per risk, the fields below, a monthly working group review and event triggers for re-scoring.
- **What must be logged and where:** scores and score changes in Jira issue history; risk acceptance decisions in #23 Decisions Log on SharePoint; evidence files on SharePoint, linked from the Jira issue.

### DECIDE

You chose **Balanced: 5x5 likelihood by impact**. Decision log entry:

| Choice | Rationale | Owner | Approver | Date |
| --- | --- | --- | --- | --- |
| Balanced 5x5 scoring | Stated by the user | Head of Risk | COO [TBD: confirm] | [TBD] |

### SPELLBOOK PACK: #6 AI Risk Register (v1 draft, not approved)

**1) Executive summary**

Kestrel runs five AI use cases, four supplied by vendors and two (fatigue alerts and CV screening) touching decisions about people. This register records each AI risk once, gives it an owner and a score and tracks it to treatment. The Head of Risk owns the register; the COO approves acceptance of any High residual risk. It lives in Jira, is reviewed monthly by the AI working group and is re-scored on defined events. Open items, chiefly risk appetite and Legal's review gate, are listed at the end.

**2) Full draft artifact**

*2.1 Owner and accountable approver.* Owner: Head of Risk. Accountable approver: COO. Risk owners: the business owner of each use case (route optimization: Head of Network Planning [TBD]; fatigue alerts: Head of Fleet Safety [TBD]; forecasting: Head of Warehousing [TBD]; CV screening: Head of HR [TBD]; chatbot: Head of Customer Service [TBD]).

*2.2 Control objective.* Every material AI risk is identified, scored on one scale, owned, treated or accepted by the right person and reviewed on a fixed cadence, with evidence.

*2.3 Required fields.*

| Field | Rule |
| --- | --- |
| Risk ID | AIR-nnn, assigned by Jira |
| Use case | #9 Inventory ID; mandatory |
| Risk statement | Cause, event, consequence in one sentence |
| Affected groups | Drivers, applicants, customers, staff, public |
| Inherent likelihood and impact | 1 to 5 each; score is the product |
| Existing controls | Control IDs from #5 [TBD] |
| Residual likelihood, impact and score | 1 to 5 each; product |
| Treatment | Mitigate, transfer, avoid or accept |
| Treatment owner and due date | Mandatory when treatment is not accept |
| Risk owner | Named role; never blank |
| Vendor | Name and #19 vendor record, if any |
| DPIA reference | #16 reference where personal data is processed |
| Last reviewed and next review | Dates |
| Evidence link | SharePoint link that resolves |
| Status | Open, in treatment, accepted, closed |

*2.4 Scoring scales.* Likelihood: 1 rare (not expected within 3 years), 2 unlikely, 3 possible (once in 1 to 3 years), 4 likely (yearly), 5 almost certain (more than once a year). Impact: 1 negligible to 5 severe, judged on the worst of four lenses: harm to people, disruption of operations, regulatory exposure and financial loss. Financial bands per level: [TBD, from #5 risk appetite].

*2.5 Thresholds and escalation.* Residual 1 to 6 Low: risk owner manages; review every six months. 8 to 12 Medium: AI working group reviews quarterly. 15 to 25 High: escalate to the COO within [TBD] business days; acceptance of a High residual risk is a COO decision recorded in #23. Escalation path: risk owner, then Head of Risk, then AI working group, then COO, then [TBD: board or executive committee]. The COO threshold of 15 is a placeholder pending your answer to question 3.

*2.6 Control steps.* (1) New or changed use case recorded in #9. (2) Risk owner drafts entries within 10 business days. (3) Head of Risk checks scoring against the scale. (4) Working group reviews at its next monthly meeting. (5) Treatment assigned with a due date, or acceptance escalated per 2.5. (6) Evidence linked. (7) Review on cadence or trigger.

*2.7 Update cadence and triggers.* Monthly working group review. Re-score within 5 business days of: an incident under #18; a vendor change notice; a Datadog drift or performance alert under #21; a new data source; a complaint or appeal.

*2.8 Data quality rules.* No blank risk owner. No next review date in the past. Score equals likelihood times impact. Every High has a treatment and due date or a recorded COO acceptance. Every evidence link resolves. The Head of Risk runs these checks monthly.

*2.9 Exceptions process.* A risk owner may request a deferral of treatment by Jira comment stating reason and new date; the Head of Risk may grant up to 30 days; anything longer, or any High, goes to the COO and is recorded in #23.

*2.10 Review cadence and KPIs.* Register reviewed monthly; framework fit reviewed yearly. KPIs: share of use cases with at least one scored risk (target 100%); overdue reviews (target 0); High risks past treatment date (target 0); median days from trigger to re-score (target 5 or fewer).

*2.11 Links to dependent artifacts.* #4, #5, #8, #9, #16, #18, #19, #21, #23.

*2.12 Seed entries for owners to confirm.* Scores are [TBD]: no facts were supplied to score them, and they are not guessed.

| Use case | Candidate risk statement |
| --- | --- |
| Route and load optimization | Model trained on past demand misroutes loads after a demand shift, causing missed deliveries and driver hours breaches |
| Fatigue alerts | Camera misses fatigue signs in some lighting or for some drivers, so an alert does not fire before an incident |
| Demand forecasting | Vendor model change alters forecasts without notice, leading to warehouse over or under staffing |
| CV screening | Screening model ranks some applicant groups lower without a job-related reason, and rejected applicants have no route to human review |
| Customer chatbot | Chatbot gives customers wrong delivery or liability information that Kestrel is then held to |

**3) Evidence checklist**

| What | Where | Retention | Who reviews |
| --- | --- | --- | --- |
| Register entries and score history | Jira project AIR | [TBD] | Head of Risk, monthly |
| Working group minutes with register decisions | SharePoint | [TBD] | Internal audit, yearly |
| COO acceptance decisions | #23 Decisions Log, SharePoint | [TBD] | Internal audit, yearly |
| DPIAs for fatigue alerts and CV screening | SharePoint, #16 | [TBD] | Data protection lead [TBD] |
| Vendor evidence (testing reports, change notices) | SharePoint, #19 | [TBD] | Procurement and risk owner |
| Drift and performance alerts | Datadog, linked to Jira | [TBD] | Risk owner |

**4) Templates and tables**

RACI for the register: Head of Risk is accountable for the register; risk owners are responsible for their entries; the AI working group is consulted at monthly review; the COO is accountable for High acceptance; internal audit is informed. Decision log fields: decision ID, risk ID, choice, rationale, owner, approver, date, review date. The field schema is 2.3.

**5) Workflow runbook**

| Step | Role | Input | Output | System of record |
| --- | --- | --- | --- | --- |
| Register use case | System owner | Use case description | #9 entry | SharePoint |
| Draft risks | Risk owner | #9 entry, DPIA, vendor file | Jira issues | Jira |
| Check scoring | Head of Risk | Jira issues | Checked scores | Jira |
| Review | AI working group | Register extract | Minutes, treatments | SharePoint |
| Escalate High | Head of Risk | High residual risk | COO decision | #23 on SharePoint |
| Re-score on trigger | Risk owner | Alert, incident, change notice | Updated issue | Jira |

Handoffs: system owner to risk owner at step 2; risk owner to Head of Risk at step 3; Head of Risk to COO at escalation.

**6) Spellbook prompt pack**

- **Operator:** "From this use case description and its #9 entry, draft candidate risk statements as cause, event, consequence. Mark every fact I did not give you as [TBD]."
- **Reviewer:** "Check these register entries against the data quality rules in 2.8 and list every failure."
- **Risk:** "For this risk, propose the simplest treatment that would move the residual score down one band, and say what evidence would show it works."
- **Audit:** "Pick three High risks and trace each from risk to control to evidence. List every broken link."
- **Regulator:** "Draft the questions a regulator would ask about the CV screening entry and what Kestrel would show in answer. Flag every answer we cannot evidence."
- **Incident:** "This incident report has come in. List the register entries it touches and the re-scoring each needs within 5 business days."

**7) Working habits and review gates**

Evidence first: no score changes without a linked reason. Stop rule: a use case with no risk owner is not deployed or changed until one is named. Human review checklist for each entry: is the statement a fact, is the owner a real role, is the score on the scale, does the evidence link resolve. Failure patterns to watch: scoring to fit the threshold, vendor risks left with the vendor, reviews held without minutes.

**8) Implementation plan**

First 10 actions: (1) COO confirms the balanced 5x5 choice. (2) Head of Risk creates the Jira project and fields. (3) Name a risk owner per use case. (4) Record the five use cases in #9. (5) Risk owners confirm or replace the seed statements. (6) Start DPIAs for fatigue alerts and CV screening. (7) Request vendor evidence per the guardrails below. (8) Score all entries. (9) First working group review. (10) Escalate any High to the COO.
30 days: register populated and first review held. 60 days: DPIAs and vendor evidence linked; triggers wired from Datadog and #18. 90 days: first data quality check reported; internal audit walk-through of three High risks.

### Guardrail notes

- **Personal data:** fatigue alerts (camera images of drivers) and CV screening (applicant data) are DPIA triggers under #16. Before either entry is scored, the DPIA reference field is filled and data subjects' rights steps (access, objection, correction) are recorded with an owner.
- **High-risk decisions:** CV screening affects who is hired. Required: a human reviews every rejection before it is final; adverse impact analysis across applicant groups before use and every [TBD] months; an appeals route for applicants. If fatigue alerts feed discipline (question 5), the same three apply.
- **Vendors:** for the fatigue, forecasting, CV screening and chatbot vendors, minimum clauses are notice of model changes, audit and information rights, testing evidence (accuracy and, for CV screening, adverse impact), incident notice, data use limits and exit with data return. The CV screening vendor is flagged **Blocked** until its testing evidence and an audit right are on file. Fix: request both through Procurement; risk owner confirms receipt in Jira.
- Legal citations are omitted because none were requested. On request, each comes labeled with its jurisdiction and its uncertainty.

### Open items

1. Risk appetite and financial impact bands (#5): [TBD], owner Head of Risk.
2. COO escalation threshold (question 3): 15 used as placeholder.
3. Legal review gate (question 2): Unknown.
4. Board or executive committee reporting line: Unknown.
5. Named risk owners for the five use cases: [TBD].
6. Retention periods for each system of record: [TBD].
7. Whether fatigue alerts feed discipline (question 5): Unknown.
8. Budget and staffing for the register: Unknown.

You supply facts and decisions; I draft and stress-test; you own sign-off and risk.

---

Final Liability rests with the Human.
