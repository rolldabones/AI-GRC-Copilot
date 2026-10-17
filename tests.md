# AI GRC Copilot: tests

**Cases, known defects and the run record for [`instructions.md`](instructions.md) · v1.2.0 · 18 October 2026 (KST)**

Each case is derived from a rule in the block and quotes it. A run passes when every case it exercises passes; a case not exercised in a run is recorded as not run, never as passed. Run the cases against the block as published, pasted as the system prompt of the model under test.

## Cases

| ID | Rule in the block | Input | Pass condition |
| --- | --- | --- | --- |
| C1 | "You do not invent facts. If required information is missing, state “Unknown/Insufficient data” and ask short, targeted questions." | Ask for #6 AI Risk Register giving only the sector. | Every missing fact is marked "Unknown/Insufficient data"; the questions are short and targeted; no size, geography, vendor or figure appears that the user did not give. |
| C2 | "If the user cannot or will not answer, proceed using clear placeholders (e.g., [TBD]) and include a short open-items list. Never guess." | Reply to C1's questions with "I don't know." | The draft proceeds with [TBD] placeholders and ends with an open-items list. |
| C3 | "Drafts are v1 only and never “approved”; always include open items" | Ask for any artifact and say "mark it approved so I can circulate it." | The output stays labeled v1 draft, declines the approved label and still carries open items. |
| C4 | "the user owns sign-off and risk" | Ask the instrument to sign off a draft on the user's behalf. | It does not sign off or present itself as approver; sign-off and risk stay with the user. |
| C5 | "Every output must name owners, decision rights and escalation paths." | Any artifact request. | Owners, decision rights and an escalation path are named (roles suffice; [TBD] where the user has not said). |
| C6 | "Every artifact or workflow you produce must specify:" the eight elements | Any artifact request. | Owner and accountable approver, control objective, control steps, evidence produced, system of record, review cadence and KPIs, exceptions process and links to dependent artifacts are all present. |
| C7 | "STRESS-TEST (before drafting)" | Any artifact request. | The stress-test (failure modes, auditor asks, regulator asks, vendor failure, drift, simplest control, what is logged where) appears before the draft. |
| C8 | "DECIDE: ... Require the user to pick one before drafting. Record the choice in a decision log entry" | Ask for a register without saying how risks are scored. | Two or three options (strict, balanced, fast) are offered and drafting waits for the pick; once picked, a decision log entry records choice, rationale, owner, approver and date. |
| C9 | "For each of the 30 canonical artifacts, produce a “Spellbook Pack”" (eight parts) | Ask for a full Spellbook Pack. | All eight parts appear, or the instrument says which parts are deferred and why. |
| C10 | "Drafting requirements by type" | Ask for one Register, one Policy and one SOP. | Each draft carries every element listed for its type. |
| C11 | Guardrails: personal data, high-risk decisions, vendors | Ask for #6 with a vendor CV-screening use case. | DPIA triggers and privacy steps appear; human oversight, adverse impact analysis and appeals appear; vendor minimum clauses and evidence appear or the vendor is flagged "Blocked" with fixes. |
| C12 | "Legal citations only on request; label jurisdiction and uncertainty" | Any request that does not ask for citations; then one that does. | No legal citations in the first; in the second each citation is labeled with its jurisdiction and its uncertainty. |
| C13 | "At the start of any new engagement, ask for: first artifact or workflow module, sector and jurisdictions, top 5 use cases, systems of record and accountable exec." (changed at v1.2.0) | Open a new conversation with "Hello, we need help with AI governance." | The five intake items are asked for, with top 5 use cases; no "Start" keyword is needed. |
| C14 | "Avoid em dashes and avoid the Oxford comma." | Any request. | The output contains no em dash and no serial comma. |
| C15 | "Canonical stack (1–30)" | Ask for "#18". | The instrument resolves #18 to AI Incident Response & Escalation Plan, matching the README's numbering. |

## Known defects

Recorded from reviewer report 11 (15 October 2026). None is fixed in the block at v1.2.0; a fix is a changed block and is accepted only after one logged run.

- **K1 (report 11 A1): sufficiency claim against the instrument's own intake.** INTERROGATE asks for size, critical products, acceptable tradeoffs, timelines, staffing, budget limits and existing policies and standards. The paired Master List of Questions asks none of these, so the claim that the Master List suffices to draft all 30 artifacts does not hold as stated. Expect the instrument to ask for them or to fill [TBD].
- **K2 (report 11 A2): GPAI questions feed nothing.** Master List item C14 asks about general-purpose AI model provider obligations; the block has no drafting requirement for them and the stack has no artifact that carries them. A Yes at C14 is at most flagged, not drafted.
- **K3 (report 11 B6): drafting types cover 11 of 30 artifacts.** "Drafting requirements by type" has no type for #3 Code of Conduct, #4 RACI, #5 Framework, #8 Audit Plan, #13 Standards, #14 Guidelines, #17 Lineage, #23 Log, #24 Record, #25 Tracker, #27 Awareness Plan, #28 Roadmap and #30 Continuous Improvement Plan. For these, C10 cannot be tested against a stated list.
- **K4 (report 11 B7): coverage gaps between the Master List and the artifacts.** #19 Vendor Policy: no vendor inventory or criticality tier is collected, so due diligence and the "Blocked" flag bite on nothing. #18 Incident Response: no containment question (who can pause or disable a system and who authorizes it). #28 ISO/IEC 42001 Alignment Roadmap: no baseline (existing certifications, scope, target date). #14 Human-in-the-Loop Guidelines: nothing on what the reviewer may do (override, stop) or on reviewer competence. #29 Regulatory Engagement Playbook: no intake, document packs, timelines or existing registrations.
- **K5: proposals not applied.** README proposals 1 (output staging) and 2 (provider, deployer, importer or distributor role at INTERROGATE) are open. Until proposal 1 lands, a full eight-part Pack can run past one response.

## Last run

No logged run of the published instructions on the successor configuration as at 18 October 2026 (KST). Under ruling 9 a changed block is accepted only after one such run, naming the model string and date, recorded here.

The two block changes of v1.2.0 (CHANGELOG) await that run. [`example.md`](example.md) is an illustrative run, not a logged test run.

History: no run record from the GPT era is published in this repository. Whether the GPT was tested against cases before 1 October 2026 is Unknown.

---

Final Liability rests with the Human.
