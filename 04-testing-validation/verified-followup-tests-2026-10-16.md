# Verified follow-up tests — 16 October 2026

**Scope:** New owner-executed Jira Cloud portfolio-simulation tests, distinct from the nine reported historical executions on 15 October 2026. I performed the Jira actions and reviewed the resulting issue fields, History and audit logs. AI helped interpret the observations and prepare this record; I retain responsibility for verification.

**Evidence status:** I shared screenshots of the runs for review in the project working session. Those **new screenshots have not yet been uploaded to this repository**, so this register provides exact audit IDs and observed values but does not represent a fully self-contained GitHub evidence package. Do not substitute earlier EVID files as proof of these new runs.

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

## Verification boundaries and next actions

1. The original nine reported tests from 15 October remain **historical, unreconciled claims**; COV-01–COV-09 in the [retrospective register](reconstructed-integration-test-register.md) are not original test IDs.
2. This new series has **two verified cases** (TC-01 and TC-04). TC-02, TC-03 and TC-05–TC-09 have not been executed and verified as part of this series.
3. To make the new cases independently reviewable in GitHub, I must select and privacy-review the new screenshots, upload them under `assets/evidence/`, and add exact links for rule configuration, before/after issue fields, History and audit logs. Until then, the working-session screenshots are the evidence source, not repository assets.
4. Preserve the simulated organizational context; neither test demonstrates production deployment or a multi-user approval process.
