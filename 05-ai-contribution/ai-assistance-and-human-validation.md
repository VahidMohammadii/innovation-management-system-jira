# AI Assistance and Human Validation

**Scope:** Simulated Jira Cloud innovation governance portfolio case study  
**Document date:** 16 October 2026

## How I used AI

I used ChatGPT as a support tool to structure the stage-gate design, consider automation conditions, develop edge-case tests, troubleshoot stale recommendations and unexpected transitions, and draft and review documentation.

## My decisions and execution

I selected the approach, configured Jira work items and automation rules, ran the tests, inspected audit logs and issue History, reviewed field values, and decided which corrections to accept. I am accountable for the accuracy of this portfolio.

## Concrete example

During AUTO-04 v2 testing, I identified an interaction with AUTO-07: incomplete evidence caused the simulated Gate 1 approval to revert. I completed the Concept Design Review — Gate 1 (IIR-33) evidence prerequisites, reran the test and confirmed the blocking condition did not match. Prototype & Test — Stage 2 (IIR-2) remained **In Review** after refresh. See [Gate 1 simulation evidence](../01-system-design/gate-1-concept-review-evidence.md) and the [evidence matrix](../04-testing-validation/evidence-traceability-matrix.md).

I do not present AI suggestions as independent verification or claim a live enterprise deployment, measured business impact or production certification.
