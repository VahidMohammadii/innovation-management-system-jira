# Conceptual Stage-Gate System Flow — Innovation Implementation Roadmap

I designed this **conceptual process map** to show how the simulated innovation management system connects four Jira stages, three decision gates, automated recommendations, evidence requirements, human governance approval and controlled stage progression. The flow represents the intended operating logic and the documented portfolio configuration; it is **not** a full export of live Jira workflows or proof that every possible branch was executed.

## 1. End-to-end innovation roadmap

```mermaid
flowchart TD
    S1["Stage 1<br/>Design Concept<br/>IIR-1"] --> G1["Gate 1<br/>Concept Design Review<br/>IIR-33"]
    G1 --> D1{"Go decision?<br/>Governance approved?<br/>Evidence complete?"}
    D1 -- Yes --> C2["AUTO-04 v2<br/>Stage 2 progression guard"]
    C2 --> S2["Stage 2<br/>Prototype & Test<br/>IIR-2"]
    D1 -- "Revise / pending" --> R1["Hold progression<br/>Complete evidence<br/>and reassess"]
    R1 -. Reassess .-> G1
    D1 -- No-Go --> N1["Do not progress<br/>Record decision<br/>and rationale"]

    S2 --> G2["Gate 2<br/>Prototype Validation Review<br/>IIR-35"]
    G2 --> D2{"Go decision?<br/>Governance approved?"}
    D2 -- Yes --> C3["AUTO-05<br/>Stage 3 progression guard"]
    C3 --> S3["Stage 3<br/>Concept Acceptance<br/>IIR-3"]
    D2 -- "Revise / pending" --> R2["Hold Stage 3<br/>Revise and reassess"]
    R2 -. Reassess .-> G2
    D2 -- No-Go --> N2["Do not progress<br/>Record gate decision"]

    S3 --> G3["Gate 3<br/>Concept Acceptance Review<br/>IIR-36"]
    G3 --> D3{"Go decision?<br/>Governance approved?"}
    D3 -- Yes --> C4["AUTO-06<br/>Stage 4 progression guard"]
    C4 --> S4["Stage 4<br/>Market Launch<br/>IIR-4"]
    D3 -- "Revise / pending" --> R3["Hold Stage 4<br/>Revise and reassess"]
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

**Readability:** I keep diagram-node labels short and place full stage/gate names and Jira identifiers in the traceability table below. The word *guard* means that AUTO-04 v2, AUTO-05 and AUTO-06 check or block transitions; it does not mean that those rules automatically move a stage forward.

**Interpretation:** I use the decision diamonds to summarize governance prerequisites, **not** to claim that each Jira rule has one identical condition expression. In particular, the Gate 1 evidence requirement is documented explicitly; I have not independently re-exported and reconciled the precise enabled condition sets for all other gates. “No-Go” and “Revise” are conceptual decision outcomes, not claims of independently tested Jira transitions for each branch.

## 2. Cross-cutting gate decision and evidence logic

```mermaid
flowchart TD
    INPUT["Evaluation inputs<br/>Customer Insight / Value Proposition<br/>Product Journey / Concept Readiness<br/>Risk & Assumptions"] --> SCORE["AUTO-01<br/>Calculate weighted score"]
    SCORE --> MISSING{"Score<br/>populated?"}
    MISSING -- No --> RESET["AUTO-08<br/>Recommendation:<br/>Pending Review"]
    MISSING -- Yes --> RECOMMEND["AUTO-02<br/>Recommend candidate:<br/>Go / No-Go / Revise"]
    RECOMMEND --> HUMAN["Human governance review<br/>Gate Decision<br/>Review Status"]
    HUMAN --> EVIDENCE{"Evidence Status, Link<br/>and Decision Rationale<br/>complete?"}
    EVIDENCE -- No --> RETURN["AUTO-07<br/>Return incomplete<br/>approval for revision"]
    RETURN -. "Complete evidence" .-> HUMAN
    EVIDENCE -- Yes --> GATE["Approved gate<br/>Eligible for stage<br/>progression check"]
    GATE --> CONTROL["AUTO-04 v2 / AUTO-05 / AUTO-06<br/>Check stage progression"]
    HUMAN -. "AUTO-03: review control" .-> GATE

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
| Stage 1 | Design Concept (IIR-1) | Develop the innovation concept | Concept design work |
| Gate 1 | Concept Design Review — Gate 1 (IIR-33) | Review concept and required evidence before Stage 2 | AUTO-07; AUTO-04 v2 on Stage 2 |
| Stage 2 | Prototype & Test (IIR-2) | Develop and test the concept / MVP | AUTO-04 v2 |
| Gate 2 | Prototype Validation Review — Gate 2 (IIR-35) | Assess prototype validation before Stage 3 | AUTO-05 on Stage 3 |
| Stage 3 | Concept Acceptance (IIR-3) | Evaluate acceptance and readiness | AUTO-05 |
| Gate 3 | Concept Acceptance Review — Gate 3 (IIR-36) | Review readiness before Stage 4 | AUTO-06 on Stage 4 |
| Stage 4 | Market Launch (IIR-4) | Plan and execute launch work in the simulated roadmap | AUTO-06 |

**Supporting work packages recorded in the initial roadmap:** Customer Journey Mapping (IIR-5), Product Journey Mapping (IIR-6), Value Map Development (IIR-7), MVP Development & Validation (IIR-8), Value Proposition Design (IIR-9), Cost-Benefit Analysis (IIR-10), Use Case Development (IIR-11), Industrial Feasibility Assessment (IIR-12), Business Case Development (IIR-13), Market Segmentation (IIR-14), Ecosystem & Unit Cost Analysis (IIR-15), Market Potential & Market Share Assessment (IIR-16), and Target Price Definition (IIR-17). I list these as **documented work packages**, not as verified current stage assignments or completed deliverables. The complete live Jira issue hierarchy has not been reconciled.

## 4. Verification boundary and observed example

In an **earlier 16 October 2026 AUTO-04 v2 permitted-condition check**, Gate 1 (IIR-33) had the required simulated evidence, a **Go** decision and **Approved** governance status. AUTO-04 v2's blocking condition did not match, but Prototype & Test (IIR-2) remained **In Review** after refresh. In a **subsequent, separately audited test (TC-04)**, I manually moved IIR-2 through **To Do → In Progress** and confirmed that the guard did not roll back the permitted transition. This demonstrates a permitted manual transition, **not** automatic progression or full production governance validation. See the [verified follow-up test record](../04-testing-validation/verified-followup-tests-2026-10-16.md).

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
