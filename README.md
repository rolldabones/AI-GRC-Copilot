# AI GRC Copilot

**Version 1.2.4 · 20 October 2026 · Instrument, formerly the AI GRC Spellbook Copilot custom GPT (retired 1 October 2026) · Instructions last verified against the GPT on 15 July 2026, before the conversion; the block changed on 18 October 2026 and no longer matches the Locked GPT configuration · License: [CC BY-NC-SA 4.0](LICENSE.md)**

> **Retired 1 October 2026 (Korea Standard Time, KST).** The AI GRC Spellbook Copilot custom GPT was retired on 1 October 2026 and converted to a private plug-in on the OpenAI platform. "Retired" here is the author's own conversion of the GPT on that date, not OpenAI's retirement: under OpenAI's Custom GPT retirement and migration FAQ (quoted in the [CHANGELOG](CHANGELOG.md) retirement notice of 28 September 2026), custom GPTs become inaccessible on 11 December 2026, or 11 February 2027 for Enterprise workspaces with an approved deferral. The instructions published in this repository are the text of record and suffice for anyone who wants to build their own. History and sources: [RETIREMENT.md](https://github.com/rolldabones/rolldabones/blob/main/RETIREMENT.md).

## What it does

This is a **Shared Spellbook** for AI governance, risk management and compliance (AI GRC). Spellbooks are workflows, prompts and working habits that help you use AI to get real work done and keep it operable and maintainable.

The instrument drafts a stack of 30 basic AI GRC artifacts, each with owners, evidence and systems of record. Not everyone needs every item. If you are running high-risk AI in a grown-up organization, this is the map.

Governance is, among other things, a documentation engine that produces decisions and proof. If you cannot point to the artifact, the owner, the control and the log, you do not have governance. You have hope.

The prompt will not do the job for you. You supply facts, constraints, decisions and approvals. The model drafts and stress-tests. You own the risk. Delegation is not abdication.

## Run it in three steps

1. Paste the fenced block in [`instructions.md`](instructions.md) into the system prompt, custom instructions or project instructions of any current assistant.
2. Give it the inputs it asks for: answer the [Master List of Minimum Questions](https://github.com/rolldabones/AI-GRC-Master-List-of-Questions) for your organization (it serves subject to known defect K1 in [`tests.md`](tests.md#known-defects): the block also asks for facts the Master List does not collect) or let it interrogate you artifact by artifact, then pick an artifact from the stack of 30 and say what you want built. [`example.md`](example.md) shows one run.
3. Review the output yourself and check it against [`tests.md`](tests.md). Drafts are v1 only and never "approved." You review, augment, approve and activate; sign-off is yours.

This repository and [AI-GRC-Master-List-of-Questions](https://github.com/rolldabones/AI-GRC-Master-List-of-Questions) are a pair: this repo holds the drafting engine, that repo holds the minimum input set that feeds it. They version together in intent though not in lockstep numbering.

## The 30 artifacts

Numbered 1 to 30 in the canonical order of [`instructions.md`](instructions.md), so a reference such as "#6" or "#18" resolves to one artifact.

### 1) Tone from the top

1. AI Policy
2. AI Governance Charter
3. AI Code of Conduct / Ethical Guidelines
4. Roles & Responsibilities Matrix (RACI: responsible, accountable, consulted, informed)

### 2) Risk and compliance discipline

5. AI Risk Management Framework
6. AI Risk Register
7. AI Compliance Register
8. AI Audit & Assurance Plan

### 3) Lifecycle controls

9. AI System Inventory & Classification Register
10. AI Lifecycle Management SOPs (standard operating procedures)
11. Model Risk Management Policy
12. Bias & Fairness Testing Protocols
13. Explainability & Transparency Standards
14. Human-in-the-Loop Guidelines

### 4) Data governance and privacy

15. Data Management Policy for AI
16. Data Privacy Impact Assessment process
17. Data Provenance & Lineage Documentation

### 5) Operational oversight

18. AI Incident Response & Escalation Plan
19. AI Vendor & Third-Party Risk Management Policy
20. Change Management Procedure for AI Models
21. Performance & Reliability Monitoring Plan

### 6) Evidence and audit readiness

22. Model Documentation Templates (Model Cards)
23. Decisions Log
24. Stakeholder Feedback Record
25. Workstream Tracker

### 7) Training and awareness

26. AI Training & Competency Framework
27. AI Awareness & Communication Plan

### 8) External posture

28. ISO/IEC 42001 Alignment Roadmap
29. Regulatory Engagement Playbook
30. Continuous Improvement Plan

## Proposed changes to the instructions

These are proposals for the instrument in [`instructions.md`](instructions.md), carried from the list of 15 July 2026. Items 1 and 2 are not applied. Each is accepted only after one logged run of the changed block under Change control below, recorded in [`tests.md`](tests.md). Item 3 (Disable Image Generation) is struck as moot after the retirement; see [CHANGELOG](CHANGELOG.md) v1.2.0.

1. **Add an output-staging rule.** A full Spellbook Pack has eight parts. Add one line to the Instruction: deliver the Pack in stages (summary and draft first, then evidence, runbook and prompt pack on confirmation) unless the user asks for everything at once. Prevents truncated single-message dumps.
2. **Add a jurisdiction-role step to INTERROGATE.** Under Org, ask whether the organization acts as provider, deployer, importer or distributor of each AI system in scope. Obligations under the EU AI Act and comparable regimes differ sharply by role. The paired [Master List of Minimum Questions](https://github.com/rolldabones/AI-GRC-Master-List-of-Questions) (v1.2.4) already asks role, per use case, at C13; the gap is that the block's INTERROGATE step captures geography but not role and does not use that answer.
3. ~~**Disable Image Generation.**~~ Struck as moot after the retirement; see [CHANGELOG](CHANGELOG.md) v1.2.0.
4. **Reconcile the "Start" trigger.** Made in v1.2.0 by the second route the proposal offered: outside the GPT there are no conversation starters, so the opening intake now fires at the start of any new engagement. Run T5 (18 October 2026) tested it in case C13, which passes; it is accepted with the block when a run passes every case.

## Regulatory-currency note (15 July 2026, amended 13 August 2026)

- ISO/IEC 42001:2023 remains the current edition of the AI management system standard. EN ISO/IEC 42001:2026 is the CEN European adoption of the same 2023 text, not a revision. The companion impact assessment methodology is ISO/IEC 42005:2025.
- **Amendment note, 13 August 2026 (KST).** This entry previously recorded the Digital Omnibus on AI as awaiting publication and 2 August 2026 as the legally operative high-risk date. That is superseded. The Digital Omnibus on AI amending Regulation (EU) 2024/1689 **entered into force on 27 July 2026**. The deferred dates below are therefore operative law, not pending changes. Pinpoints are to Regulation (EU) 2024/1689 as amended; the last column gives the provision of Regulation (EU) 2026/1744 that made the change. The Article 4 and Article 111(4) rows were added on 20 October 2026 (KST), read against the Official Journal text of Regulation (EU) 2026/1744.

  | Provision | Applies from | Pinpoint | Source |
  | --- | --- | --- | --- |
  | Chapters I and II (Article 5 sits in Chapter II), general date | 2 February 2025 | Article 113, third paragraph, point (a), as replaced | Art. 1, point (40) |
  | Prohibitions added by the Omnibus: Article 5(1), first subparagraph, points (ba) and (bb), and Article 5(1a) and (1b) | 2 December 2026 | Article 113, third paragraph, point (a), exception | Art. 1, point (40) |
  | Article 4 AI literacy, as replaced: providers and deployers "shall take measures to support the development of AI literacy of their staff and other persons dealing with the operation and use of AI systems on their behalf"; the obligation "does not require providers or deployers to guarantee any specific level of AI literacy of any individual" | Chapter I date (2 February 2025); amended wording in force 27 July 2026 | Article 4(1) | Art. 1, point (5) |
  | Article 50 transparency obligations | 2 August 2026 | Article 113, second paragraph | unchanged general date |
  | Article 50(2) marking duty, transition: "Providers of AI systems, including general-purpose AI systems, generating synthetic audio, image, video or text content, that have been placed on the market before 2 August 2026 shall take the necessary steps in order to comply with Article 50(2) by 2 December 2026" | 2 December 2026, for those providers and systems only | Article 111(4), new | Art. 1, point (39)(b) |
  | Articles 102 to 110 | 27 July 2026 | Article 113, third paragraph, point (d), new | Art. 1, point (40) |
  | Chapter III, Sections 1, 2 and 3, with the exception of Article 6(5): AI systems classified as high-risk pursuant to Article 6(2) and Annex III | 2 December 2027 | Article 113, third paragraph, point (c)(i), as amended | Art. 1, point (40) |
  | The same, for AI systems classified as high-risk pursuant to Article 6(1) and Annex I | 2 August 2028 | Article 113, third paragraph, point (c)(ii), as amended | Art. 1, point (40) |

  So the general Article 5 date is 2 February 2025 and the prohibitions added by the Omnibus are deferred to 2 December 2026. Do not state the Article 5 date without that carve-out. **Article 113 has unnumbered paragraphs with lettered points; the preferred pinpoint form, the one the amending act uses, is "Article 113, third paragraph, point (c)". "Article 113(3)" also appears in Regulation (EU) 2024/1689 itself (Article 111(1)) and is not an error.** **Citation.** The amending act is **Regulation (EU) 2026/1744** of the European Parliament and of the Council of 8 July 2026, OJ L, 2026/1744, 24.7.2026, ELI http://data.europa.eu/eli/reg/2026/1744/oj, in force 27 July 2026. Its Article 1, point (40) amends the **third paragraph of Article 113** of Regulation (EU) 2024/1689. The Article 113 rows were read against the consolidated text of Regulation (EU) 2024/1689 on EUR-Lex, as at 13 August 2026 (KST).
- The account's canonical [EU AI Act currency note](https://github.com/rolldabones/ai-governance-for-boards/blob/main/05-jurisdictions/eu.md#eu-ai-act-currency-note) in ai-governance-for-boards, dated 15 October 2026 (KST), governs where this entry and it differ, including the Article 50(2) provider carve-out that a provider reading needs.
- References to standards and frameworks in this repository name alignment targets for drafting purposes. They are not conformity claims. Verify current status before relying on any of them.

## Change control

The AI GRC Spellbook Copilot configuration is Locked as of 1 October 2026. The published block is not that configuration: it changed on 18 October 2026 (the two edits listed in the [CHANGELOG](CHANGELOG.md) entry of that date) and no longer matches the Locked GPT. Changes are made in [`instructions.md`](instructions.md) under this repository's version rule: versions apply to the repository as a whole and every change is logged in [CHANGELOG](CHANGELOG.md). A changed block is accepted only after one logged run of the published instructions as a system prompt on a current frontier model, recorded in [`tests.md`](tests.md). The first such run, T5 on 18 October 2026 (KST) on `claude-opus-5-5`, passed 13 of 15 cases on their completed runs; the block is not accepted while C1 and C14 are open.

## Part of the ecosystem

This repository is part of the [rolldabones governance ecosystem](https://github.com/rolldabones/rolldabones/blob/main/ECOSYSTEM.md). Nearest neighbors:

- [AI-GRC-Master-List-of-Questions](https://github.com/rolldabones/AI-GRC-Master-List-of-Questions) - the paired minimum input set that feeds this drafting engine
- [grc](https://github.com/rolldabones/grc) - the foundation working method on the OCEG (Open Compliance and Ethics Group) GRC Capability Model spine; the GRCnext™ primitives themselves are defined in [GRCnext-Copilot](https://github.com/rolldabones/GRCnext-Copilot)
- [slow-ai-kitchen](https://github.com/rolldabones/slow-ai-kitchen) - the 12-step governed AI methodology the Spellbook operationalizes
- [AI-Impact-Assessment-Tool](https://github.com/rolldabones/AI-Impact-Assessment-Tool) - the pre-deployment gate that generates inputs for the risk and inventory artifacts
- [master-prompt-for-in-house-legal-and-compliance](https://github.com/rolldabones/master-prompt-for-in-house-legal-and-compliance) - the master prompt: a system prompt that turns a general-purpose assistant into a disciplined in-house legal and compliance assistant for counsel, compliance, legal operations and the business stakeholders they serve

## How to Cite

> Paik, Son-U Michael. *AI GRC Copilot*, v1.2.4. GRC Solutions Korea, 2026. https://github.com/rolldabones/AI-GRC-Copilot

A machine-readable citation is in [CITATION.cff](CITATION.cff).

## License

[CC BY-NC-SA 4.0](LICENSE.md). Attribution required, non-commercial use, share alike.

---

Final Liability rests with the Human.
