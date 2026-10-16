# Conceptual Stage-Gate System Flow — Innovation Implementation Roadmap

I designed this **conceptual process map** to show how the simulated innovation management system connects four Jira stages, three decision gates, automated recommendations, evidence requirements, human governance approval and controlled stage progression. The flow represents the intended operating logic and the documented portfolio configuration; it is **not** a full export of live Jira workflows or proof that every possible branch was executed.

## 1. End-to-end innovation roadmap

```mermaid
flowchart TD
    S1["Stage 1: Design Concept<br/>IIR-1"] --> G1["Gate 1: Concept Design Review<br/>IIR-33"]
    G1 --> D1{"Go + Approved<br/>and required evidence complete?"}
    D1 -- Yes --> C2["AUTO-04 v2: Stage 2 progression control"]
    C2 --> S2["Stage 2: Prototype & Test<br/>IIR-2"]
    D1 -- "No: revise / missing approval" --> R1["Hold or return for revision<br/>Complete evidence and repeat review"]
    R1 -. Reassess .-> G1
    D1 -- "No-Go" --> N1["Do not progress<br/>Record decision and rationale"]

    S2 --> G2["Gate 2: Prototype Validation Review<br/>IIR-35"]
    G2 --> D2{"Go + Approved?"}
    D2 -- Yes --> C3["AUTO-05: Stage 3 progression control"]
    C3 --> S3["Stage 3: Concept Acceptance<br/>IIR-3"]
    D2 -- "Revise / approval missing" --> R2["Hold Stage 3 progression<br/>Revise and reassess"]
    R2 -. Reassess .-> G2
    D2 -- No-Go --> N2["Do not progress<br/>Record gate decision"]

    S3 --> G3["Gate 3: Concept Acceptance Review<br/>IIR-36"]
    G3 --> D3{"Go + Approved?"}
    D3 -- Yes --> C4["AUTO-06: Stage 4 progression control"]
    C4 --> S4["Stage 4: Market Launch<br/>IIR-4"]
    D3 -- "Revise / approval missing" --> R3["Hold Stage 4 progression<br/>Revise and reassess"]
    R3 -. Reassess .-> G3
    D3 -- No-Go --> N3["Do not progress<br/>Record gate decision"]

    classDef stage fill:#E8F0FE,stroke:#3B6EA8,color:#182D49
    classDef gate fill:#FFF1D6,stroke:#B88625,color:#493611
    classDef control fill:#E5F4EC,stroke:#39835B,color:#173D2B
    classDef hold fill:#F9E9E9,stroke:#B75B5B,color:#572828
    class S1,S2,S3,S4 stage
    class G1,G2,G3,D1,D2,D3 gate
    class C2,C3,C4 control
    class R1,R2,R3,N1,N2,N3 hold
```

**Interpretation:** I use the decision diamonds to summarize governance prerequisites, **not** to claim that each Jira rule has one identical condition expression. In particular, the Gate 1 evidence requirement is documented explicitly; I have not independently re-exported and reconciled the precise enabled condition sets for all other gates. “No-Go” and “Revise” are conceptual decision outcomes, not claims of independently tested Jira transitions for each branch.

## 2. Cross-cutting gate decision and evidence logic

```mermaid
flowchart TD
    INPUT["Evaluation inputs<br/>Customer Insight, Value Proposition,<br/>Product Journey, Concept Readiness,<br/>Risk & Assumptions"] --> SCORE["AUTO-01<br/>Calculate Weighted Gate Score"]
    SCORE --> MISSING{"Score populated?"}
    MISSING -- No --> RESET["AUTO-08<br/>Gate Recommendation: Pending Review"]
    MISSING -- Yes --> RECOMMEND["AUTO-02<br/>Recommend Go / No-Go / Revise candidate"]
    RECOMMEND --> HUMAN["Human governance review<br/>Gate Decision and Governance Review Status"]
    HUMAN --> EVIDENCE{"Evidence Status, Evidence Link<br/>and Decision Rationale complete?"}
    EVIDENCE -- No --> RETURN["AUTO-07<br/>Return incomplete approval for revision"]
    RETURN -. Complete evidence .-> HUMAN
    EVIDENCE -- Yes --> GATE["Approved gate decision<br/>eligible for stage progression check"]
    GATE --> CONTROL["AUTO-04 v2 / AUTO-05 / AUTO-06<br/>Evaluate corresponding stage progression"]
    HUMAN -. "AUTO-03: governance review control" .-> GATE

    classDef input fill:#E8F0FE,stroke:#3B6EA8,color:#182D49
    classDef action fill:#E5F4EC,stroke:#39835B,color:#173D2B
    classDef decision fill:#FFF1D6,stroke:#B88625,color:#493611
    classDef exception fill:#F9E9E9,stroke:#B75B5B,color:#572828
    class INPUT input
    class SCORE,RECOMMEND,HUMAN,GATE,CONTROL action
    class MISSING,EVIDENCE decision
    class RESET,RETURN exception
```

I treat the second diagram as a **logical overview**, not a universal execution order: triggers and applicability differ by automation rule. AUTO-07's required evidence fields are specifically documented for the Gate 1 test scenario. AUTO-03's exact current conditions still require Jira configuration reinspection. Recommendations from AUTO-02 do not substitute for the human Gate Decision.

## 3. Stage and gate traceability

| Sequence | Jira work item | Conceptual purpose | Governing control |
| --- | --- | --- | --- |
| Stage 1 | Design Concept (IIR-1) — Design Concept | Develop the innovation concept | Concept design work |
| Gate 1 | Concept Design Review — Gate 1 (IIR-33) — Concept Design Review | Review concept and required evidence before Stage 2 | AUTO-07; AUTO-04 v2 on Stage 2 |
| Stage 2 | Prototype & Test (IIR-2) — Prototype & Test | Develop and test the concept / MVP | AUTO-04 v2 |
| Gate 2 | Prototype Validation Review — Gate 2 (IIR-35) — Prototype Validation Review | Assess prototype validation before Stage 3 | AUTO-05 on Stage 3 |
| Stage 3 | Concept Acceptance (IIR-3) — Concept Acceptance | Evaluate acceptance and readiness | AUTO-05 |
| Gate 3 | Concept Acceptance Review — Gate 3 (IIR-36) — Concept Acceptance Review | Review readiness before Stage 4 | AUTO-06 on Stage 4 |
| Stage 4 | Market Launch (IIR-4) — Market Launch | Plan and execute launch work in the simulated roadmap | AUTO-06 |

**Supporting work packages recorded in the initial roadmap:** Customer Journey Mapping (IIR-5), Product Journey Mapping (IIR-6), Value Map Development (IIR-7), MVP Development & Validation (IIR-8), Value Proposition Design (IIR-9), Cost-Benefit Analysis (IIR-10), Use Case Development (IIR-11), Industrial Feasibility Assessment (IIR-12), Business Case Development (IIR-13), Market Segmentation (IIR-14), Ecosystem & Unit Cost Analysis (IIR-15), Market Potential & Market Share Assessment (IIR-16), and Target Price Definition (IIR-17). I list these as **documented work packages**, not as verified current stage assignments or completed deliverables. The complete live Jira issue hierarchy has not been reconciled.

## 4. Verification boundary and observed example

In the **16 October 2026 AUTO-04 v2 follow-up**, I populated the Gate 1 evidence prerequisites on Concept Design Review — Gate 1 (IIR-33), set the simulated decision to **Go** and governance status to **Approved**, and retested the Stage 2 control. I observed that AUTO-04 v2's blocking condition did not match and that **Prototype & Test (IIR-2) remained In Review after refresh**. I do not describe that observed status as In Progress, nor equate an automation audit “Success” with verified end-to-end business progression.

- [Gate 1 concept-review evidence](gate-1-concept-review-evidence.md)
- [Automation rule catalog](../03-automation-rules/automation-rule-catalog.md)
- [Governance and decision traceability](../03-automation-rules/governance-and-traceability.md)
- [Integration test report](../04-testing-validation/integration-test-report.md)
- [Evidence traceability matrix](../04-testing-validation/evidence-traceability-matrix.md)
- [AUTO-04 v2 audit history](../assets/evidence/EVID-24-AUTO-04-v2-Audit-History.png)
- [Gate 1 approved configuration](../assets/evidence/EVID-25-AUTO-04-Gate1-Approved-Configuration.png.png)
- [AUTO-04 test C](../assets/evidence/EVID-26-AUTO-04-Test-C-Condition-Not-Matched.png.png)

## 5. AI assistance and ownership

I used AI to help structure and check this visual documentation against the recorded project artifacts. I designed the simulated system, configured Jira, tested the scenarios, reviewed the evidence and retain responsibility for the accuracy of the portfolio. The diagrams are **conceptual models** of a simulated system, not independent validation of a production deployment.
