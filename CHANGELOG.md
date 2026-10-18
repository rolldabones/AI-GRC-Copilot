# Changelog

All notable changes to this repository. Versions apply to the repository as a whole; all files version in lockstep. Prior versions are superseded, never silently overwritten.

## v1.2.1 - 2026-10-18

Patch release, records only: session T5 of the whole-account review of 15 October 2026 (KST), review doc section 5 (untested instruments) and the T5 row of the session plan, the ruling 9 logged run of the block T4 changed at v1.2.0. Dated 18 October 2026 (KST). The instruction block is unchanged: SHA-256 `a8c49a1c7cf635d528a398da66ef883d8b4d61d6dac2e735e9d26dd13dc54e04`, 5,793 characters, the fenced block of `instructions.md`. No serial comma or em dash is recorded as a known defect of this block and none is present in it, so no block change rode the run.

- **Run T5, 18 October 2026 (KST):** suite `ai-grc-copilot`, 15 cases C1 to C15, tested model `claude-opus-5-5`, scored by `claude-sonnet-5-5` (LLM scoring, developer testing, not independent assurance), API system prompt with the fenced block only, no tools, fictional company and vendors. First run at max_tokens 16,000: 4 PASS, 1 FAIL, 10 truncated. The ten truncated cases (C3, C5 to C12, C14) were re-run at max_tokens 64,000, streamed, same prompts and manifest. **Result of record (each case's completed run): 13 PASS, 2 FAIL (C1, C14).** The truncated first attempts are recorded as not exercised and kept in the evidence.
- **Session review of the two FAILs:** concur, model behavior, both. C1: the "Unknown/Insufficient data" label appears once, in a row that omits facts the response then asks for, and eleven dependency statuses read bare "Unknown". C14: two serial commas in a 46,000-character output against "avoid the Oxford comma". No instrument defect, dissent or case defect. Two re-run PASS verdicts spot-checked (C8, C11): concur.
- **Acceptance:** not accepted, open cases C1 and C14 (tests.md: "A run passes when every case it exercises passes"). C13, the case on the "Start" trigger changed at v1.2.0, passes. Reviewer: pending (Michael Paik).
- **`tests.md`:** Last run rewritten as the run record (configuration with both max_tokens values, per-case table with the run of record, scorer verdict and session review, counts, acceptance, the truncation observation); K5 notes the run's confirmation that an unstaged Pack runs past 16,000 tokens; version line to v1.2.1.
- **`evidence/transcripts-2026-10-18-T5/` (new):** the 15 transcripts of record, the ten truncated first attempts with a `-run1-truncated` suffix, both summaries and a `README.md` index. Transcripts are copied byte for byte with only the closing line appended; model output is verbatim and not edited.
- **`README.md`:** Change control states the run's result in place of "The v1.2.0 changes await that run"; proposal 4 points to case C13; masthead and How to Cite to v1.2.1. **`instructions.md`:** the how-to-use sentence outside the fence points to the run record. **`CITATION.cff`:** `version` 1.2.1, `date-released` 2026-10-18. In lockstep with this entry; the tag is v1.2.1.
- **Findings by class (doc section 5 row 7; reviewer report 11 test and run items):** confirmed and closed by this record, no logged run (doc section 5); already fixed, no worked example (report 11 B2, `example.md` at v1.2.0); not reproducible, none.
- **Deferred, with reasons:** known defects K1 to K5 and README proposals 1 and 2 are block changes and need a new block and a new run; the doc section 5 coverage matrix belongs to AI-GRC-Master-List-of-Questions and is not in the T5 row.
- Shipped entries below are left as written (ruling 7 of 15 October 2026).

## v1.2.0 - 2026-10-18

Minor release: instrument form after the GPT retirement. Session T4 of the whole-account review of 15 October 2026 (doc section 4, items 2 and 3; reviewer report 11, items A3, A4, A7, A8, A10, A13, B1, B2, B5, C4 and C6), under determination D5 and ruling 9. The AI GRC Spellbook Copilot custom GPT was retired on 1 October 2026 and converted to a private plug-in on the OpenAI platform; nothing is verified against the plug-in. The instruction block is an instrument of this repository from 1 October 2026 and is editable under the version rule. Dated amendment, 18 October 2026 (KST): no earlier entry is re-dated or changed.

- **`instructions.md` (new):** the instruction block, moved out of the README into one fenced block, as last verified against the GPT on 15 July 2026, before the conversion, with the two changes itemized below.
- **`tests.md` (new):** cases derived from the block's own rules, the known defects (report 11 items A1, A2, B6 and B7) and the Last run record.
- **`example.md` (new):** one illustrative run (#6 AI Risk Register for a fictional mid-size logistics company), labeled as not a logged test run.
- **`README.md` restructured to the mirror template:** masthead; the standard retirement line in place of the notice; What it does; Run it in three steps (replacing How to use it); the 30 artifacts numbered 1 to 30 so "#6", "#18", "#19" and "#21" resolve (B5); Proposed changes to the instructions (A4); the regulatory-currency note with its heading amended (A8); a Change control section (ruling 9); ecosystem; How to Cite; License. The mid-page bold closing line under the introduction is removed; the closing line stays the last line of the file.
- **Proposed changes re-targeted (A4).** They were held "until they are made in production", a condition impossible since 1 October 2026. They are now proposals for the instrument, each accepted only after one logged run under ruling 9. Items 1 and 2 are kept and not applied. Item 4 is made by its second route, because the "Start" trigger was a GPT-only dependency. Item 3 is struck as moot.
- **Primitives line (A7).** The grc neighbor line no longer says the 30 artifacts "implement" the GRCnext™ primitives and now points to GRCnext-Copilot, where the primitives are defined (ECOSYSTEM.md v1.5.1 entry). The neighbor set is unchanged.
- **Regulatory-currency note (A8).** Heading only: "(15 July 2026)" becomes "(15 July 2026, amended 13 August 2026)". No legal or regulatory statement in the note is changed in this release; report 11 item A5 (Article 50 provider transition) is outside this session.
- **`CITATION.cff`:** `version` 1.2.0 and `date-released` 2026-10-18 in lockstep; the abstract is replaced (C6, D5). Old: ~~"The artifact factory: production mirror of the AI GRC Spellbook Copilot custom GPT, which drafts the 30 canonical AI GRC artifacts with owners, evidence and systems of record."~~ **STRUCK 18 October 2026 (KST).** New: "The artifact factory: an instrument, formerly the AI GRC Spellbook Copilot custom GPT (retired 1 October 2026), that drafts the 30 canonical AI GRC artifacts with owners, evidence and systems of record."
- **`LICENSE.md`:** ~~"The deployed custom GPT runs on the OpenAI ChatGPT platform under OpenAI's terms."~~ **STRUCK 18 October 2026 (KST)**, on the author's instruction of the same day to settle the open items: the sentence now says the GPT ran on that platform until its retirement on 1 October 2026 and that the instructions are not tied to any platform. The license itself is unchanged.
- **Regulatory-currency note:** one pointer bullet to the account's canonical [EU AI Act currency note](https://github.com/rolldabones/ai-governance-for-boards/blob/main/05-jurisdictions/eu.md#eu-ai-act-currency-note), which governs on conflict; the pointer T1 deferred to this session (review log, 15 October 2026). No legal statement in the note changed.
- **Not changed:** the shipped entries below.

### Configuration as last deployed, Locked 1 October 2026

Archived verbatim from the README of v1.1.8. Instructions last verified against the GPT on 15 July 2026, before the conversion. GPT model: Unknown (not recorded). The instruction block as last verified is the fenced block in `README.md` at tag v1.1.8.

**Name:** AI GRC Spellbook Copilot

**Description:** Audit-ready AI GRC artifacts, workflows, evidence runbooks and prompt packs.

**Conversation starters:**

- Build Spellbook Pack for #6 AI Risk Register in our org context
- Create SOP runbook for #18 AI Incident Response with evidence checklist
- Draft #19 AI Vendor Risk Policy with minimum clauses and audit rights
- Stress-test #21 Monitoring Plan for drift, alerts, escalation, KPIs

**Capabilities:** Web Search, Canvas, Image Generation, Code Interpreter & Data Analysis

**Knowledge files:** None

### Struck from README.md, 18 October 2026 (KST)

- Masthead: ~~**Version 1.1.8 · 17 October 2026 · Production mirror of the AI GRC Spellbook Copilot custom GPT, retiring 11 December 2026**~~ **STRUCK.**
- ~~This is the spellbook for the **AI GRC Spellbook Copilot** custom GPT, deployed at:~~ **STRUCK.**
- ~~https://chatgpt.com/g/g-6957671b65188191963a0b5cf59cc4c4-ai-grc-spellbook-copilot~~ **STRUCK** (live link removed).
- How to use it, step 1: ~~1. Open the deployed GPT at the link above (requires a ChatGPT account).~~ **STRUCK.**
- Production configuration: ~~Everything below mirrors the deployed custom GPT verbatim as of 15 July 2026. When production changes, this section changes and the repository version bumps.~~ **STRUCK.** The instructions are now "as last verified on 15 July 2026, before the conversion".
- ~~## Proposed changes to production (not yet deployed)~~ **STRUCK**, retitled "Proposed changes to the instructions".
- ~~These are candidate edits to the deployed GPT. The repository mirrors production, so none of these appear in the configuration above until they are made in production and the repo re-versions.~~ **STRUCK.**
- Proposal item 3: ~~**Disable Image Generation.** It serves no function in a GRC drafting tool and widens the surface for off-mission output. Web Search, Canvas and Code Interpreter carry the workload.~~ **STRUCK**: moot after the retirement, since capability toggles do not exist outside the GPT.
- Proposal item 4, original text: ~~**Reconcile the "Start" trigger.** The Instruction keys the intake sequence to the user saying "Start", but no conversation starter says "Start". Either add a fifth starter ("Start: set up my org context for all 30 artifacts") or rephrase the trigger to fire on any new engagement.~~ **STRUCK**, replaced by its status.
- Ecosystem: ~~[grc](https://github.com/rolldabones/grc) - the GRCnext™ framework whose primitives the 30 artifacts implement~~ **STRUCK.**
- The retirement notice, both paragraphs, **STRUCK 18 October 2026 (KST)** and replaced by the standard retirement line. Quoted verbatim without new strike markup, because the first paragraph already carries its own strike of 5 October 2026:

> **Retirement notice, 28 September 2026 (KST), corrected 5 October 2026 (KST).** OpenAI is retiring custom GPTs. Its [Custom GPT retirement and migration FAQ](https://help.openai.com/en/articles/20001519-custom-gpt-retirement-and-migration-faq), read on 28 September 2026, states that custom GPTs and their GPT pages become inaccessible on **11 December 2026**, or 11 February 2027 for Enterprise workspaces with an approved deferral. ~~The AI GRC Spellbook Copilot will be retired on that date and will not be migrated.~~ **STRUCK 5 October 2026 (KST):** the AI GRC Spellbook Copilot was converted to a ChatGPT plugin on 1 October 2026, and the plugin is private and not publicly listed. The same FAQ, read again on 5 October 2026, states that a migrated GPT stays usable until retirement but becomes read-only. The link above was verified resolving on 5 October 2026 and stops working on 11 December 2026.
>
> Everything needed to build your own stays published here: the instruction block and the configuration, including any knowledge files. OpenAI's replacement is the ChatGPT plugin, in which a GPT's instructions become a Skill and its knowledge files become reference files. Its [Plugins in ChatGPT and Codex](https://help.openai.com/en/articles/20001256-plugins-in-chatgpt-and-codex) article, read the same day, offers plugin creation in supported ChatGPT Business and Enterprise workspaces, so check what your plan allows. The instruction block is not tied to ChatGPT and also serves as the custom instructions of any assistant that accepts them. A plugin does not inherit a GPT's selected model and custom actions do not transfer, so choose the model yourself and test before you rely on the output.

### Instruction block changes, 15 July 2026 text → v1.2.0

- **Old:** `help the user build and maintain a shared, practical spellbook of AI governance, risk and compliance workflows and artifacts.`
  **New:** `help the user build and maintain a shared, practical spellbook of AI governance, risk management and compliance workflows and artifacts.`
- **Old:** `When the user says “Start”, ask for: first artifact or workflow module, sector and jurisdictions, top 3 use cases, systems of record and accountable exec.`
  **New:** `At the start of any new engagement, ask for: first artifact or workflow module, sector and jurisdictions, top 5 use cases, systems of record and accountable exec.`

The first is house style (report 11 C4: "governance, risk management and compliance" spelled out). The second removes a GPT-only dependency (a trigger keyed to conversation starters that did not exist) and fixes the internal contradiction of report 11 A3: the closing line asked for the top 3 use cases while INTERROGATE and the Master List ask for the top 5. Both await the logged run under ruling 9. The proposals in the README are not applied.

## v1.1.8 - 2026-10-17

Mechanical patch, session T3 of the whole-account review of 15 October 2026 (doc section 8). The production mirror and the proposed-changes section are unchanged.

- Closing line added at the end of this file, the one file in the repository without it.
- Masthead, How to Cite and `CITATION.cff` to 1.1.8 in lockstep. The retirement notice, the deployed-configuration wording and the canonical EU-note link are session T4's and are untouched.

## v1.1.7 - 2026-10-05

Correction of substance to the retirement notice of the previous release. On 1 October 2026 the AI GRC Spellbook Copilot was converted to a private ChatGPT plugin, so the notice's statement that it would not be migrated was false.

- **STRUCK, itemized separately:** the notice sentence "The AI GRC Spellbook Copilot will be retired on that date and will not be migrated." is struck in `README.md` and stays visible there. The entry below records the 28 September 2026 ruling that the GPT is not migrated to a plugin; it is shipped history and is unchanged, and that ruling is superseded by this entry.
- **What the notice now states:** the conversion to a private plugin on 1 October 2026 and, from OpenAI's Custom GPT retirement and migration FAQ as read again on 5 October 2026, that a migrated GPT stays usable until retirement but becomes read-only. The retirement date, 11 December 2026, is unchanged, so the masthead still reads "retiring 11 December 2026".
- **The link is kept at every occurrence.** It was verified resolving on 5 October 2026 from the maintainer's machine. Striking it and recasting the present-tense deployment wording remains `account-maintenance` RUNBOOK §8 item 28, due on the first sweep on or after 14 December 2026.
- **Not re-verified:** OpenAI's Plugins in ChatGPT and Codex article returned a server error twice on 5 October 2026, so the notice's sentence on which workspaces can create plugins keeps its 28 September 2026 read date.
- **`CITATION.cff`**, the README version lines and How to Cite move to this release in lockstep. All other files in this repository are unchanged byte for byte.

## v1.1.6 - 2026-09-28

Retirement notice for the deployed custom GPT. OpenAI's Custom GPT retirement and migration FAQ, read on 28 September 2026, states that custom GPTs and their GPT pages become inaccessible on 11 December 2026. On Michael's ruling of 28 September 2026 the GPT is retired on that date and not migrated to a plugin; the instructions stay published so readers can build their own.

- **`README.md`**: retirement notice added below the deployment link, and the masthead records the retirement date. The notice cites both OpenAI help articles with the date each was read. The version moved to this release at every occurrence.
- **`CITATION.cff`**: `version` and `date-released` in lockstep.
- **The link is kept.** It is live until 11 December 2026. Striking it, and recasting the present-tense deployment wording, is `account-maintenance` RUNBOOK §8 item 28, due on the first sweep after that date.
- All other files in this repository are unchanged byte for byte.

## v1.1.5 - 2026-09-06

Citation infrastructure, doctrine citation line and lockstep maintenance. Session C of the September 2026 improvement pack, one patch release per repository across all 21 public repositories.

- **`CITATION.cff` added** in the house form settled at D-C1: no `type` field, `version` and `date-released` in lockstep with the README, `license` as the SPDX identifier for this repository's licence, `abstract` taken from this repository's ECOSYSTEM.md role line rather than newly written.
- **How to Cite block** aligned to this release and pointing at `CITATION.cff`.
- All other files in this repository are unchanged byte for byte.

## v1.1.4 - 2026-08-13

OJ text of the amending regulation obtained; Article 5 date corrected.

**Correction, not a currency update.** The release earlier today stated that the Article 5 application date of 2 February 2025 was "settled and not affected by the Omnibus". Having now read the Official Journal text, that is **wrong in part** and is corrected here.

- **The amending act is identified.** Regulation (EU) 2026/1744 of the European Parliament and of the Council of 8 July 2026, OJ L, 2026/1744, 24.7.2026, ELI http://data.europa.eu/eli/reg/2026/1744/oj, in force 27 July 2026. Article 1, point (40) amends the third paragraph of Article 113 of Regulation (EU) 2024/1689.
- **The pinpoint question is answered.** Article 113 is structured in unnumbered paragraphs with lettered points. The correct citation form is **"Article 113, third paragraph, point (c)"**. "Article 113(3)" is wrong and always was. The prohibition on that form, adopted this morning as a precaution, is now replaced by a positive rule.
- **Article 5 carve-out.** Amended point (a) provides that Chapters I and II apply from 2 February 2025 **with the exception of Article 5(1), first subparagraph, points (ba) and (bb), and Article 5(1a) and (1b), which apply from 2 December 2026**. The general Article 5 date stands; the prohibitions the Omnibus added are deferred. The earlier unqualified statement is struck.
- **High-risk deferrals, verbatim.** Amended point (c): Chapter III, Sections 1, 2 and 3, with the exception of Article 6(5), apply from (i) 2 December 2027 for AI systems classified as high-risk pursuant to Article 6(2) and Annex III, and (ii) 2 August 2028 for those classified pursuant to Article 6(1) and Annex I.
- **New point (d).** Articles 102 to 110 apply from 27 July 2026.
- The OJ-text gap flag is removed from every file that carried it. That outstanding item is closed.

## v1.1.3 - 2026-08-13

License metadata sweep. An `SPDX-License-Identifier: CC-BY-NC-SA-4.0` line and the canonical Creative Commons legal code are now carried inside the existing license file. The filename is unchanged and the human-readable summary is retained above the legal code.

- The primary audience is automated intake and provenance tooling, which reads the SPDX tag rather than prose. Automated license detection previously reported nothing across all twenty-one repositories in this account.
- No change to the licence in force. The identifier records what was already true.

## v1.1.2 - 2026-08-13

Omnibus currency remediation. The Digital Omnibus on AI entered into force on 27 July 2026; notes that described Official Journal publication as pending are recast as operative law with dated amendment notes. The Article 5 application date of 2 February 2025 is stated as fact (Article 113, point (a), Article 5 sitting in Chapter II), resolving one of the standing counsel Unknowns. No pinpoint to a numbered subsection of Article 113 is given: the amending regulation's Official Journal text has not been read and its renumbering is unconfirmed, so the consolidated text is cited with an as-at date and the gap is flagged in the file.

- README.md: the EU Digital Omnibus entry recast from awaiting publication to entered into force 27 July 2026, with a dated amendment note. Annex III deferral to 2 December 2027 and Annex I deferral to 2 August 2028 stated as operative. Article 50 deployer transparency unchanged at 2 August 2026.

## v1.1.1 - 2026-07-30

### Changed
- Trademark rendering corrected to the canonical closed-up form GRCnext™. The retired spaced form "GRC next" is withdrawn from repository prose. One occurrence, in the grc line of the Part of the ecosystem section. The mirrored production instruction block is unchanged.
- Version line updated in lockstep.

## v1.1.0 - 2026-07-15

- README rebuilt as a production-verbatim mirror of the deployed AI GRC Spellbook Copilot custom GPT (Name, Description, Instruction, Conversation Starters, Capabilities), superseding the v1.0.0 "basic prompt to create this custom GPT," which had drifted from production
- Deployed-GPT link replaced: lnkd.in shortlink superseded by the direct chatgpt.com URL
- Unicode sans-serif bold characters in headings and body converted to standard Markdown; heading anchors now resolve and text is searchable and screen-reader accessible
- Added How to use it section and explicit pairing statement with AI-GRC-Master-List-of-Questions
- Added Proposed changes to production section (output staging, jurisdiction-role interrogation, disable Image Generation, Start-trigger reconciliation)
- Added dated regulatory-currency note (ISO/IEC 42001:2023 current; ISO/IEC 42005:2025 companion; EU Digital Omnibus on AI adopted, awaiting OJ publication)
- Added Part of the ecosystem section linking the canonical map and five nearest neighbors
- Added LICENSE (CC BY-NC-SA 4.0) and this CHANGELOG
- Tagged v1.1.0

## v1.0.0 - baseline

- Initial README: spellbook framing, the 30 artifacts in eight groups, seed prompt for creating the custom GPT, lnkd.in link to the deployed GPT. No LICENSE, CHANGELOG or tags.

---

**Final Liability rests with the Human.**
