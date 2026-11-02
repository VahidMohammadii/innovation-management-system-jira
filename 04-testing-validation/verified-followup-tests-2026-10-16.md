# Verified follow-up tests — 16 October 2026

**Scope:** New owner-executed Jira Cloud portfolio-simulation tests, distinct from the nine reported historical executions on 15 October 2026. I performed the Jira actions and reviewed the resulting issue fields, History and audit logs. AI helped interpret the observations and prepare this record; I retain responsibility for verification.

**Evidence status:** Nine new screenshots covering TC-01 and TC-04 are committed under `assets/evidence/` and linked below. The screenshots and recorded audit IDs support these two observed runs only. I reviewed and approved the newly uploaded images for public portfolio use on 2 November 2026. The original nine historical tests are separate.

## TC-04 — AUTO-04 v2: permitted Stage 2 progression

**Result: PASS for the permitted-path guard behavior; not an automatic-forward-transition test.**

- **Rule:** AUTO-04 | Stage Progression Governance Control v2 (enabled).
- **Trigger:** Work item transitioned to `In Progress`; scope JQL `key = IIR-2`.
- **Gate lookup:** `key = IIR-33`. The rule's conditional rollback branch checks whether Gate Decision is not `Go` **or** Governance Review Status is not `Approved`; if matched, it transitions IIR-2 to `To Do` and comments.
- **Preconditions:** Concept Design Review — Gate 1 (IIR-33) showed `Go`, `Approved`, `Complete`, with decision rationale and an evidence link to the simulated Gate 1 record.
- **Action:** I manually transitioned Prototype & Test (IIR-2) from `In Review` to `To Do`, then from `To Do` to `In Progress`.
- **Expected:** The rule must not roll back a permitted transition when Gate 1 is Go/Approved.
- **Actual:** After the run, IIR-2 displayed `In Progress`; its History recorded the manual `To Do → In Progress` transition. AUTO-04 audit showed `Success`, passed issue-scope JQL, found IIR-33 (`Done`), and reported that the rollback IF condition did **not** match.
- **Audit timestamp:** 2026-10-16 20:46:52–20:46:53 (Jira displayed time).
- **Audit ID:** `24cb375d-daaa-4f0c-b5d3-2780e24dad1a`.
- **Interpretation:** The rule is a **rollback guard**, not a rule that automatically moves a work item forward. An earlier, separate permitted-condition check had left IIR-2 `In Review`; this new transition supplies the previously missing positive-path observation. Historical negative-path rollbacks remain separately documented; their original case-level reconciliation is not implied by this PASS.

## TC-01 — AUTO-01: weighted gate score

**Result: PASS for the observed calculation and field update.**

- **Rule:** AUTO-01 | Calculate Weighted Innovation Gate Score (enabled).
- **Work item:** Test Decision Gate (IIR-37).
- **Trigger:** Change to one of the five scoring inputs. Rule checks issue type `Decision Gate` and requires all five scores to be populated.
- **Action:** I changed Customer Insight Score from `4` to `3`.
- **Inputs after edit:** Customer Insight `3`; Product Journey `4`; Value Proposition `5`; Risk & Assumptions `3`; Concept Readiness `4`.
- **Configured weights:** 0.25, 0.15, 0.25, 0.15, 0.20 respectively (sum 1.00).
- **Expected:** `0.25×3 + 0.15×4 + 0.25×5 + 0.15×3 + 0.20×4 = 3.85`.
- **Actual:** IIR-37 displayed Weighted Gate Score `3.85`. History showed my input change `4 → 3` and Automation for Jira's score update `None → 3.85`. The audit showed both conditions passed and `Issues edited successfully`.
- **Audit timestamp:** 2026-10-16 20:58:12 (Jira displayed time).
- **Audit ID:** `9210e4a8-2e0f-464a-b712-16f91083b099`.
- **Interpretation:** The arithmetic and persisted field result agree for this specific test input. Gate Recommendation remained `Pending Review` in the supplied screenshot; AUTO-02 behavior was **not** tested here.

## Linked screenshot evidence

| Case | Evidence | Repository image |
| --- | --- | --- |
| TC-01 | AUTO-01 rule configuration | [TC01-01](../assets/evidence/TC01-01.PNG) |
| TC-01 | IIR-37 score inputs and result 3.85 | [TC01-02](../assets/evidence/TC01-02.PNG) |
| TC-01 | Successful AUTO-01 audit | [TC01-03](../assets/evidence/TC01-03.PNG) |
| TC-01 | IIR-37 History showing 4→3 input and None→3.85 score | [C01-04](../assets/evidence/C01-04.PNG) |
| TC-04 | AUTO-04 v2 rule configuration | [TC04-01](../assets/evidence/TC04-01.PNG) |
| TC-04 | IIR-33 gate context; not sufficient alone to establish all prerequisites | [TC04-02](../assets/evidence/TC04-02.PNG) |
| TC-04 | IIR-2 In Progress result | [TC04-03](../assets/evidence/TC04-03.PNG) |
| TC-04 | AUTO-04 v2 audit with rollback IF not matched | [TC04-04](../assets/evidence/TC04-04.PNG) |
| TC-04 | IIR-2 manual transition History | [TC04-05](../assets/evidence/TC04-05.PNG) |

For earlier Gate 1 prerequisite evidence, see [EVID-25](../assets/evidence/EVID-25-AUTO-04-Gate1-Approved-Configuration.png.png). The screenshots are snapshots, not proof of every possible rule branch. The supplied archive named the fourth TC-01 image `C01-04.PNG`; that exact filename is preserved.

## Verification boundaries and next actions

1. The original nine reported tests from 15 October remain **historical, unreconciled claims**; COV-01–COV-09 in the [retrospective register](reconstructed-integration-test-register.md) are not original test IDs.
2. This new series has **two verified cases** (TC-01 and TC-04). TC-02, TC-03 and TC-05–TC-09 have not been executed and verified as part of this series.
3. The nine new screenshots are now linked in GitHub. Before merging the evidence PR, I must perform a separate privacy and confidentiality review of these new images and confirm the screenshots' legibility and audit details.
4. Preserve the simulated organizational context; neither test demonstrates production deployment or a multi-user approval process.
