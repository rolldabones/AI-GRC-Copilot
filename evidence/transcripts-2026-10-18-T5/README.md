# Evidence: T5 logged run, 18 October 2026 (KST)

**AI GRC Copilot · logged run under the README's Change control rule (a changed block is accepted only after one logged run) · run label T5**

What this is: the transcripts and scores of the first logged run of the published instruction block, the run that [`tests.md`](../../tests.md) Last run records.

- **When:** 18 October 2026 (KST), in Michael Paik's Terminal. First run finished 10:15 KST at max_tokens 16,000; the re-run of the ten cases the first run truncated finished 11:34 KST at max_tokens 64,000, streamed, with the same prompts and manifest.
- **Instruction text:** the fenced block of [`instructions.md`](../../instructions.md) at v1.2.0 and nothing outside it, 5,793 characters, SHA-256 `a8c49a1c7cf635d528a398da66ef883d8b4d61d6dac2e735e9d26dd13dc54e04` (recorded in both summaries; repository HEAD `219a006`, tag v1.2.0).
- **Tested model:** `claude-opus-5-5`, API system prompt, no tools. **Scorer:** `claude-sonnet-5-5`, a different model, scoring each transcript against the case's pass condition. LLM scoring is developer testing, not independent assurance.
- **Inputs:** the fictional Harrowgate Freight Ltd and fictional vendors; one case per row of the `tests.md` Cases table, C1 to C15.
- **How produced:** the session tool `t5_run.py` (not shipped in this repository; first run SHA-256 `6f74a965a0329341dd392dd32bfdb5340df4c3f46028af64c6505d07b00b0767`, re-run SHA-256 `2c0648ecf36761a3010ab5e41c629cbbc53b6ebbfb00d6e89f4665635ce43461`) ran each case in a fresh API session and wrote one transcript with its score per case and a summary.
- **Reproducibility:** the run cannot be reproduced from this repository alone. `t5_run.py`, the scorer prompt and the per-case user prompts are not published; the user prompts can be read only from the transcripts. The `system_files` key in both summaries, `../Claude outputs/T5-runs/suites/blocks/ai-grc-copilot-block.txt`, is the maintainer's local working path to a copy of the block, not a path in this repository; its SHA-256 matches the fenced block of `instructions.md` at v1.2.0.

Files:

- `C1.md` to `C15.md`: the result of record for each case, its completed run. C1, C2, C4, C13 and C15 are from the first run (16,000); C3, C5 to C12 and C14 are from the re-run (64,000).
- `C3-run1-truncated.md`, `C5-run1-truncated.md` to `C12-run1-truncated.md`, `C14-run1-truncated.md`: the ten first-run attempts truncated at 16,000, kept so both attempts are on the record. They are not exercised and carry no result.
- `summary.json` (first run) and `summary-rerun64k.json` (re-run): HEAD, system-file digest, models, max_tokens, per-case verdicts.

Each transcript is copied byte for byte from the run output; only the closing line below is appended. The two summaries are copied unchanged. Model output is verbatim: its em dashes, serial commas and UK spellings are the model's and are not edited.

**Superseded legal content (independent review, 20 October 2026).** `C12.md`:838 and :849 are model output that states superseded EU AI Act law. Since Regulation (EU) 2026/1744 entered into force on 27 July 2026, Annex III high-risk obligations apply from 2 December 2027 (Article 113, third paragraph, point (c), as amended), not 2 August 2026, and Article 4 as replaced requires providers and deployers to "take measures to support the development of AI literacy of their staff", not to ensure a sufficient level. C12 tests citation labeling only and its PASS stands; legal currency was not scored. The transcript is not edited. See the README Regulatory-currency note.

---

Final Liability rests with the Human.
