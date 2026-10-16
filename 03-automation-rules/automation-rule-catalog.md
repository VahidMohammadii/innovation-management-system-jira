# Jira Automation Rule Catalog — Innovation Implementation Roadmap

**Status:** Owner-authored portfolio documentation; configuration reconciliation pending  
**Environment:** Simulated Jira Cloud innovation governance workflow

I configured and tested eight controls. This catalog describes their intended functions and my observed tests; it is not a Jira configuration export.

| Rule | Control | Observed scope |
| --- | --- | --- |
| AUTO-01 | Weighted Gate Score | Score calculation tested on test decision gate (IIR-37) |
| AUTO-02 | Gate Recommendation | Go / No-Go / Revise candidate logic; I corrected a stale recommendation using an unconditional ELSE fallback |
| AUTO-03 | Governance Review Control | Governance scenarios exercised; current precise conditions require reinspection |
| AUTO-04 v2 | Stage 2 progression | Uses Stage 2 Prototype & Test (IIR-2) and Gate 1 Concept Design Review — Gate 1 (IIR-33); older version disabled in observed setup |
| AUTO-05 | Stage 3 progression | Checks Gate 2 decision and governance approval |
| AUTO-06 | Stage 4 progression | Checks Gate 3 decision and governance approval |
| AUTO-07 | Evidence Completeness | Returns incomplete approvals to Returned for Revision; duplicate-comment prevention tested |
| AUTO-08 | Missing Gate Score | Resets recommendation to Pending Review when score is empty |

## AUTO-04 v2 follow-up

I tested blocked scenarios A/B and a permitted scenario C. The positive test initially failed when AUTO-07 reset Concept Design Review — Gate 1 (IIR-33)'s governance approval due to incomplete evidence. I completed the simulated Gate 1 evidence record, set the required fields and retested. The AUTO-04 v2 blocking condition did not match and I confirmed Prototype & Test (IIR-2) remained **In Review** after refresh, rather than asserting it was In Progress.

Evidence: [AUTO-04 v2 audit history](../assets/evidence/EVID-24-AUTO-04-v2-Audit-History.png), [Gate 1 configuration](../assets/evidence/EVID-25-AUTO-04-Gate1-Approved-Configuration.png.png), [Test C condition](../assets/evidence/EVID-26-AUTO-04-Test-C-Condition-Not-Matched.png.png).

## Verification standard and limitations

I distinguish automation audit execution from a successful business-rule outcome, inspect the resulting Jira issue fields and History as well as audit logs, and recorded nine passing integration tests; the AUTO-04 v2 follow-up is separate. Individual case-to-screenshot reconciliation and reinspection of exact enabled rule configurations remain outstanding.

I used AI for rule-design options, troubleshooting, edge-case analysis and documentation and configured the rules, executed tests, inspected evidence and made the final decisions. This is a portfolio simulation, not a production deployment.
