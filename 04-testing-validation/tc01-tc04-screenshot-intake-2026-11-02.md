# TC-01 and TC-04 screenshot intake — 2 November 2026

**Status:** All nine screenshot files are committed to the evidence PR branch and exact paths verified. I approved the nine images for public portfolio use on 2 November 2026.

I supplied a RAR archive containing nine PNG screenshots for two previously verified tests, TC-01 and TC-04. AI assisted with file inspection and documentation; I remain responsible for the final evidence selection and privacy review. I uploaded the nine source images to the PR branch; AI assisted with file and link checks.

## Screenshot inventory and committed repository paths

All paths below are committed files in this PR branch. Retain the original filenames during upload to avoid introducing ambiguity. The first file is named `C01-04.PNG` in the supplied archive (without the initial `T`).

| Case | Source filename | Committed path under `assets/evidence/` | Visible content | Review note |
| --- | --- | --- | --- | --- |
| TC-01 | `TC01-01.PNG` | `assets/evidence/TC01-01.PNG` | AUTO-01 field-change trigger, Decision Gate condition, nonempty-score JQL and score-edit action | Configuration overview; formula details may require an additional close-up |
| TC-01 | `TC01-02.PNG` | `assets/evidence/TC01-02.PNG` | IIR-37 five scoring inputs and Weighted Gate Score 3.85 | Outcome screenshot |
| TC-01 | `TC01-03.PNG` | `assets/evidence/TC01-03.PNG` | AUTO-01 successful audit execution and passed checks | Match audit ID to the test register |
| TC-01 | `C01-04.PNG` | `assets/evidence/C01-04.PNG` | IIR-37 History: automation updates Weighted Gate Score to 3.85 after Customer Insight 4→3 | Source filename typo preserved intentionally |
| TC-04 | `TC04-01.PNG` | `assets/evidence/TC04-01.PNG` | AUTO-04 v2 conditional rollback rule | Verify readable rule conditions |
| TC-04 | `TC04-02.PNG` | `assets/evidence/TC04-02.PNG` | IIR-33 Gate 1 work item and scoring / recommendation context | Does **not by itself** prove Go / Approved / Complete; corroborate with prior verified gate screenshot |
| TC-04 | `TC04-03.PNG` | `assets/evidence/TC04-03.PNG` | IIR-2 shown In Progress | Positive-path resulting state |
| TC-04 | `TC04-04.PNG` | `assets/evidence/TC04-04.PNG` | AUTO-04 v2 successful audit, Gate 1 lookup and rollback IF condition not matched | Match audit ID to the test register |
| TC-04 | `TC04-05.PNG` | `assets/evidence/TC04-05.PNG` | IIR-2 History showing manual transition to In Progress | Confirms manual transition, not auto-forward movement |

## Cross-reference to verified runs

- **TC-01 / AUTO-01:** IIR-37; expected and actual weighted score **3.85**; audit ID `9210e4a8-2e0f-464a-b712-16f91083b099`.
- **TC-04 / AUTO-04 v2:** IIR-2 allowed to remain **In Progress** after a manual transition; audit ID `24cb375d-daaa-4f0c-b5d3-2780e24dad1a`.
- See [verified follow-up tests](verified-followup-tests-2026-10-16.md) for the test inputs, expected and actual behavior, and historical distinction.

## Publication acceptance checklist

- [x] Upload the nine PNG files to their exact paths on this PR branch.
- [x] Verify each file exists at its exact GitHub path (visual legibility still requires final owner review).
- [x] Owner confirmed review and public-publication approval for the nine new screenshots on 2 November 2026. This is an owner review, not an independent privacy certification.
- [x] Cross-referenced screenshot roles with the documented audit IDs, issue History and observed outcomes; a Jira Success status alone is not treated as proof of the business outcome.
- [x] Add relative image links to the verified follow-up register and the evidence traceability matrix after upload.
- [x] Update the README's screenshot-pending statement after verifying the nine paths.
- [ ] Owner to review the completed PR diff and explicitly approve merge; publication approval of screenshots is not merge authorization.

**Limitations:** The nine files document two test cases, not nine distinct cases. The historical nine tests remain unreconciled. No previously published screenshot binary was changed; this PR adds nine new screenshot binaries.
