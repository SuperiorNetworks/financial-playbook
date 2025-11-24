# AI-Powered Strategy Builder Wizard Specification

## 1. Overview

The **AI-Powered Strategy Builder Wizard** is a new feature designed to dramatically simplify the onboarding and playbook creation process. Instead of relying solely on manual data entry or live API integrations, users can upload their existing financial documents (such as bank statements or financial statements). An AI model will then analyze these documents to automatically extract data, identify financial patterns, generate initial graphs, and recommend tailored playbook strategies.

This feature acts as an intelligent onboarding assistant, doing the heavy lifting of data aggregation and initial analysis, which allows the user to move directly to the strategic "what-if" planning stage.

---

## 2. User Journey & Wireframes

The wizard will guide the user through a simple, three-step process: Upload, Analyze, and Recommend.

### Step 1: Document Upload

The user is prompted to upload their financial documents. The interface will accept multiple files and common formats (PDF, PNG, JPG).

**Wireframe: Document Upload Screen**

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  STRATEGY BUILDER WIZARD                                                │
│                                                                         │
│  Step 1: Upload Your Financial Documents                                │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │                                                            │        │
│  │  Drag & Drop Files Here                                    │        │
│  │  or                                                        │        │
│  │  [ Browse Files ]                                          │        │
│  │                                                            │        │
│  │  Supported formats: PDF, PNG, JPG                          │        │
│  │  Recommended: Last 3-6 months of bank/financial statements.│        │
│  │                                                            │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  Uploaded Files:                                                       │
│  - Jan_2025_Statement.pdf  [Remove]                                │
│  - Feb_2025_Statement.pdf  [Remove]                                │
│  - Mar_2025_Statement.pdf  [Remove]                                │
│                                                                         │
│  [Cancel]                                    [Analyze Documents →]    │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### Step 2: AI Analysis & Data Verification

Once the documents are uploaded, the AI model processes them. The user sees a progress screen. After analysis, the user is presented with a summary of the extracted data for verification. This is a crucial step to ensure accuracy.

**Wireframe: AI Analysis & Verification Screen**

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  STRATEGY BUILDER WIZARD                                                │
│                                                                         │
│  Step 2: Verify Extracted Data                                          │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │  AI Analysis Complete! Please review the extracted summary.   │        │
│  │                                                            │        │
│  │  Time Period Analyzed: Jan 1, 2025 - Mar 31, 2025          │        │
│  │                                                            │        │
│  │  Average Monthly Income:    $8,200  [View Details]         │        │
│  │  Average Monthly Expenses:  $7,500  [View Details]         │        │
│  │  Net Cash Flow:             +$700/mo [View Details]         │        │
│  │                                                            │        │
│  │  Identified Recurring Bills:                                │        │
│  │  - Rent: $2,500/mo                                          │        │
│  │  - Insurance: $450/mo                                       │        │
│  │  - Software: $300/mo                                        │        │
│  │  [+ Add/Edit Recurring Bill]                                │        │
│  │                                                            │        │
│  │  Is this summary correct?                                   │        │
│  │                                                            │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  [← Re-upload]                         [Confirm & Get Recommendations →]│
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### Step 3: Recommendations & Playbook Creation

After the user confirms the data, the AI generates insights and recommends 1-3 potential playbook strategies. Each recommendation comes with a brief explanation and a starting cash flow graph.

**Wireframe: Recommendations Screen**

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  STRATEGY BUILDER WIZARD                                                │
│                                                                         │
│  Step 3: Choose Your Starting Strategy                                  │
│  Based on our analysis, here are a few recommended strategies:          │
│                                                                         │
│  ┌──────────────────────────┐ ┌──────────────────────────┐             │
│  │  RECOMMENDATION 1        │ │  RECOMMENDATION 2        │             │
│  │  **Cash Flow Optimization**│ │  **Debt Reduction Focus**  │             │
│  │                          │ │                          │             │
│  │  Your cash flow is       │ │  Your credit card debt   │             │
│  │  positive but could be   │ │  is impacting your       │             │
│  │  improved. This strategy │ │  growth. This strategy   │             │
│  │  focuses on accelerating │ │  prioritizes paying down │             │
│  │  AR and reducing         │ │  high-interest debt.     │             │
│  │  discretionary spending. │ │                          │             │
│  │                          │ │                          │             │
│  │  [Preview Graph]         │ │  [Preview Graph]         │             │
│  │  [Select This Strategy]  │ │  [Select This Strategy]  │             │
│  └──────────────────────────┘ └──────────────────────────┘             │
│                                                                         │
│  [Skip and Create a Blank Playbook]                                     │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

Once a strategy is selected, the user is taken directly to the **Scenario Editor** (Wireframe 5), with all the extracted data, recurring bills, and the initial cash flow graph pre-populated. The user can then fine-tune the playbook.

---

## 3. Technical Implementation

The AI engine for this wizard involves a multi-step pipeline:

1.  **Document Ingestion & OCR:**
    *   Uploaded files (PDF, PNG, JPG) are processed.
    *   **Optical Character Recognition (OCR)** is used to extract raw text from the documents. For PDF files, text extraction is direct where possible.

2.  **AI-Powered Data Structuring:**
    *   The raw text is fed into a **Large Language Model (LLM)** with a specific prompt.
    *   The prompt instructs the model to act as a financial analyst and extract key information into a structured JSON format. This includes:
        *   Transactions (date, description, amount, credit/debit)
        *   Recurring income and expenses (e.g., payroll, rent, utilities)
        *   Account balances (starting and ending)
        *   Statement periods

3.  **Analysis & Assumption Generation:**
    *   The structured JSON data is then processed by a backend service.
    *   This service calculates key metrics: average monthly income, expenses, burn rate, etc.
    *   It identifies patterns, such as bills that appear consistently across multiple statements.
    *   It generates a list of **assumptions** (e.g., "Assumed rent of $2,500/month based on consistent payments").

4.  **Recommendation Engine:**
    *   The key metrics and identified patterns are fed into another LLM prompt or a rules-based engine.
    *   This engine is designed to recognize common financial situations and suggest appropriate strategies. For example:
        *   If `(total_debt / total_assets) > 0.5`, recommend a **Debt Reduction** strategy.
        *   If `(monthly_income - monthly_expenses)` is highly variable, recommend a **Cash Buffer** strategy.
        *   If `AR_days_outstanding > 45`, recommend an **AR Acceleration** strategy.

5.  **Graph & Playbook Generation:**
    *   Based on the selected strategy, a starting playbook is generated.
    *   The extracted transaction data is used to create an initial cash flow projection graph.
    *   All this data is pre-populated into the Scenario Editor for the user to begin their detailed planning.

---

## 4. Benefits of this Feature

*   **Reduces Friction:** Massively lowers the barrier to entry for new users.
*   **Saves Time:** Automates hours of manual data entry.
*   **Provides Instant Value:** Users get actionable insights and a working playbook within minutes of signing up.
*   **Improves Data Accuracy:** Reduces the chance of human error during manual data input.
*   **Creates a "Wow" Factor:** Demonstrates the power of the application's AI capabilities from the very first interaction.

This Strategy Builder Wizard will be a key differentiator, making the Financial Playbook application not just a tool for planning, but an intelligent partner in financial strategy creation.
