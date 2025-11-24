# Logic Simulator & Report Generator Specification

## 1. Overview

This document specifies a powerful **Logic Simulator & Report Generator** for the Financial Playbook application. This feature elevates the application from a simple forecasting tool to a strategic business intelligence engine. Users will be able to define a set of conditional rules, run complex simulations, and generate detailed, multi-scenario reports that identify risks and recommend actionable solutions, mirroring the sophisticated analysis shown in the user-provided example.

---

## 2. Core Components

The feature consists of three main components:
1.  **The Logic Editor:** A user-friendly interface for defining the rules and conditions of the simulation.
2.  **The Simulation Engine:** A backend process that runs the simulation based on the defined logic.
3.  **The Report Generator:** A module that takes the simulation results and generates a comprehensive, multi-page report.

---

## 3. Wireframes

### a. The Logic Editor

This new editor will be part of the "Scenario Planning" section. It allows users to build a chain of conditional logic.

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  SCENARIO LOGIC EDITOR: "Q1 2026 Cash Flow Analysis"                    │
│                                                                         │
│  SIMULATION RULES:                                                      │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ IF Chase Balance < $8,000 THEN FLAG "Reserve Risk"         │        │
│  │                                                            │        │
│  │ IF Capital One Balance > $15,000 THEN FLAG "Credit Risk"   │        │
│  │                                                            │        │
│  │ ON Feb 15, 2026:                                           │        │
│  │   PAY Miamisburg Loan (Amount: $5,627.01)                  │        │
│  │                                                            │        │
│  │ EVERY 1st and 15th:                                        │        │
│  │   PAY Owner Draw (Amount: $3,000)                          │        │
│  │                                                            │        │
│  │ [+ Add Rule]                                               │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  [Save Logic]                                 [Run Simulation & Generate Report] │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### b. Report Output

The generated report will be a comprehensive document, similar to the user's example, and will be viewable within the application or exportable as a PDF.

---

## 4. Technical Implementation

### a. The Logic Editor & Rule Set

-   **Rule Definition:** The Logic Editor will allow users to create a list of rules. Each rule will have a **condition** and an **action**.
-   **Data Structure:** The set of rules for a scenario will be stored as a JSON object. For example:

```json
{
  "rules": [
    {
      "condition": {
        "variable": "chase_balance",
        "operator": "<",
        "value": 8000
      },
      "action": {
        "type": "FLAG_RISK",
        "payload": "Reserve Risk"
      }
    },
    {
      "condition": {
        "date": "2026-02-15"
      },
      "action": {
        "type": "PAY_BILL",
        "payload": {
          "name": "Miamisburg Loan",
          "amount": 5627.01
        }
      }
    }
  ]
}
```

### b. The Simulation Engine

1.  **Initialization:** The engine starts with the current financial state (account balances, debts, etc.) as of the simulation start date.
2.  **Time-Stepping:** The simulation proceeds day-by-day through the specified time period (e.g., Nov 2025 – Mar 2026).
3.  **Event Processing:** On each day, the engine processes events in a specific order:
    *   Scheduled income (based on projections).
    *   Scheduled bills and payments.
    *   Actions triggered by the user-defined logic rules.
4.  **State Recording:** The financial state (balances, etc.) is recorded for each day.
5.  **Risk Flagging:** If any rule's condition is met, the corresponding risk is flagged with the date and details.

### c. The Report Generator

1.  **Data Aggregation:** After the simulation is complete, the Report Generator collects all the daily state data and flagged risks.
2.  **Root Cause Analysis (AI-Powered):** The flagged risks are fed into an LLM with a prompt asking it to perform a root cause analysis (e.g., "The overdraft on Feb 15 was caused by the Miamisburg payoff combined with the owner draw.").
3.  **Solution Generation (AI-Powered):** The identified root causes are then fed into another LLM prompt that asks for recommended solutions (e.g., "To avoid this, consider reducing the owner draw, delaying the payoff, or cutting other expenses.").
4.  **Report Assembly:** The generator then assembles the final report, including:
    *   An executive summary.
    *   The running balance tables.
    *   The identified critical issues and the AI-generated analysis.
    *   The AI-generated recommended solutions.
    *   Charts and visualizations created from the daily state data.

---

## 5. Benefits

-   **True Strategic Planning:** Moves beyond simple forecasting to allow for complex, rule-based strategic simulations.
-   **Proactive Risk Identification:** The system can automatically identify future problems based on the user's own business logic.
-   **Automated Intelligence:** The AI-powered analysis and recommendation engine does the heavy lifting of interpreting the simulation results.
-   **Actionable Insights:** The final report is not just a collection of data; it's a detailed, actionable plan for financial management.
