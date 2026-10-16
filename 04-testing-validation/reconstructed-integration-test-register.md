# Reconstructed Integration Test Register — IIR

**Prepared:** 16 October 2026  
**Status:** Retrospective coverage reconstruction; not an original nine-case execution log

I recorded nine passing integration tests on 15 October 2026, but I no longer have the original individual case worksheet. I reconstruct the known **coverage areas** without inventing original case identifiers, numeric inputs, timestamps or per-case results. COV identifiers below are documentation references, not historical test IDs. I have checked the screenshot contents, but a one-to-one mapping to the nine original executions is not established.

| Coverage reference | Rule | Scenario | Expected behavior (reconstructed) | Documented observation | Candidate evidence | Missing detail |
| --- | --- | --- | --- | --- | --- | --- |
| COV-01 | AUTO-01 | Weighted scoring, test decision gate (IIR-37) | Calculate weighted score | Calculation and audit success recorded | [EVID-02](../assets/evidence/EVID-02_AUTO-01.png) | Weights, inputs, timestamp, original ID |
| COV-02 | AUTO-02 | Go / No-Go / Revise recommendation | Update recommendation from current inputs | Stale recommendation corrected using unconditional ELSE | [EVID-03](../assets/evidence/EVID-03_AUTO-02.png) | Exact inputs and outputs |
| COV-03 | AUTO-03 | Governance review | Enforce configured review | Governance test and successful execution documented | [EVID-21](../assets/evidence/EVID-21_AUTO-03-Successful-Execution.png.png) | Exact conditions and timestamp |
| COV-04 | AUTO-05 | Concept Acceptance — Stage 3 (IIR-3) / Prototype Validation Review — Gate 2 (IIR-35) | Block progression without approval | Stage 3 governance reported passed | [EVID-05](../assets/evidence/EVID-05-AUTO-05.png) | Exact transition and timestamp |
| COV-05 | AUTO-06 | Market Launch — Stage 4 (IIR-4) / Concept Acceptance Review — Gate 3 (IIR-36) | Block progression without approval | Stage 4 governance reported passed | [EVID-22](../assets/evidence/EVID-22-AUTO-06-Stage4-Control-Success.png.PNG) | Exact state and timestamp |
| COV-06 | AUTO-07 | Missing evidence fields | Return approval for revision | Returned for Revision observed | [EVID-10](../assets/evidence/EVID-10-AUTO-07-Test-A.PNG), [EVID-11](../assets/evidence/EVID-11-AUTO-07-Test-B.PNG), [EVID-12](../assets/evidence/EVID-12-AUTO-07-Test-C.PNG) | Which missing field per execution |
| COV-07 | AUTO-07 | Repeated evidence validation | Prevent duplicate comments | Prevention observed | [History](../assets/evidence/EVID-13-gate-decision-history.png) | Exact execution sequence |
| COV-08 | AUTO-08 | Missing score and stale recommendation | Reset to Pending Review | Reset and audit success recorded | [EVID-14](../assets/evidence/EVID-14-AUTO-08-Test-A.PNG), [EVID-15](../assets/evidence/EVID-15-AUTO-08-Test-B.PNG) | Previous value and timestamp |
| COV-09 | AUTO-04 / v2 | Stage 2 gate control | Block unapproved progression | JQL/trigger issues and corrective retesting documented | [EVID-23](../assets/evidence/EVID-23-AUTO-04-v2-JQL-Not-Matched.png) | Not established as one of nine passing cases on 15 October |

**Interpretation:** These are nine retrospective coverage categories, **not proof of nine separate historical passes**. The existing integration report identifies five broader coverage areas, not an original nine-case mapping.

## Separate AUTO-04 v2 follow-up — 16 October 2026

| Scenario | Expected | Observed | Evidence |
| --- | --- | --- | --- |
| A/B: Gate 1 prerequisites absent | Block Stage 2 progression | Blocked scenarios reported | [Audit history](../assets/evidence/EVID-24-AUTO-04-v2-Audit-History.png) |
| C: Concept Design Review — Gate 1 (IIR-33) Go / Approved and complete evidence | Do not roll back permitted transition | Blocking condition not matched; Prototype & Test (IIR-2) remained **In Review** after refresh | [Gate 1 fields](../assets/evidence/EVID-25-AUTO-04-Gate1-Approved-Configuration.png.png), [Test C](../assets/evidence/EVID-26-AUTO-04-Test-C-Condition-Not-Matched.png.png) |

I used AI to help organize this retrospective register. I configured Jira, executed the tests, reviewed the evidence and retain responsibility for the findings. This portfolio simulation does not establish a production deployment or independent audit.

## Subsequent verified cases (separate from historical reconstruction)

On 16 October 2026, I separately verified a new AUTO-04 v2 permitted-path transition (TC-04, IIR-2 remained **In Progress** after a manual transition) and a new AUTO-01 weighted-score calculation (TC-01, expected and observed **3.85** on IIR-37). I recorded audit IDs and conditions in the [new follow-up register](verified-followup-tests-2026-10-16.md). These results **do not replace or validate** the missing original nine-case worksheet. New screenshot files are not yet in this repository.
