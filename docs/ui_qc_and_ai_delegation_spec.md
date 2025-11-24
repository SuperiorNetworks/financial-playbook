# UI QC Numbering & AI Delegation System Specification

## 1. UI Quality Control (QC) Numbering System

### a. Overview

To streamline communication and facilitate precise UI adjustments, a **Quality Control (QC) Numbering System** will be implemented. Every interactive and informational element on the screen—including buttons, images, sections, and subheadings—will be assigned a unique, non-repeating 3-digit number. These numbers will be displayed in brackets (e.g., `[101]`) during development and can be globally disabled for the final production launch.

### b. Wireframe Example with QC Numbers (Dashboard)

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [101] [LOGO]  [102] Financial Playbook    [103] [Dashboard] [104] [Accounts] [105] [Scenarios] [106] [Reports] │
│                                                      [107] [User: Dwain] [108] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│ [201] DASHBOARD                                                         │
│                                                                         │
│ [202] CRITICAL ALERTS                                                   │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ [203] 🚨 Overdraft Risk on Feb 15, 2026 [View Details] [204] │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│ [205] QUICK STATS                                                       │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐                  │
│  │ [206] Total │ │ [207] Monthly│ │ [208] AR     │                  │
│  │ Balance      │ │ Burn         │ │ Outstanding  │                  │
│  │   $39,255    │ │   -$5,100    │ │    $12,400    │                  │
│  └──────────────┘ └──────────────┘ └──────────────┘                  │
│                                                                         │
│ [209] UPCOMING TRANSACTIONS                                             │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ [210] Dec 1: Owner Draw (-$3,000)                          │        │
│  │ [211] Dec 1: IRS Payment (-$600)                           │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### c. Implementation

-   A global "development mode" flag will be used. When this flag is `true`, the QC numbers will be rendered. When `false`, they will be hidden.
-   The numbering sequence will be maintained across all wireframes and will be continued as new elements are added.

---

## 2. AI Delegation & Advanced Automation

### a. Overview

This system introduces a new layer of intelligence for managing playbook tasks. Each item in a playbook can be categorized as `Manual`, `Automated`, or `Delegated`, each with its own set of rules and notifications.

### b. Wireframe Updates

#### i. Playbook Register with Delegation Status

```
| Date       | Description       | Change      | Balance     | [401] Status     |
|------------|-------------------|-------------|-------------|------------------|
| 12/01/25   | Connectwise Bill  | –$1,683.88  | $17,706.51  | [402] [Automated ▼]|
| 12/15/25   | Family Loan       | –$2,500.00  | $13,746.40  | [403] [Delegated ▼]|
| 01/01/26   | Owner Draw        | –$3,000.00  | $11,827.73  | [404] [Manual ▼]   |
```

#### ii. Automation Settings Modal

(Pops up when a user selects `[Automated] [402]`)

```
┌─────────────────────────────────────────────────────────┐
│ [501] Automation Settings for "Connectwise Bill"        │
├─────────────────────────────────────────────────────────┤
│                                                         │
│ [502] This bill is expected every month.                │
│                                                         │
│ [503] Alert me if the amount changes by more than:      │
│   [504] [ 3% ▼] (Options: 1%, 3%, 5%, 10%)              │
│                                                         │
│ [505] [Cancel]                               [506] [Save Automation] │
└─────────────────────────────────────────────────────────┘
```

#### iii. Delegate Profiles & Permissions (in Settings)

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [601] DELEGATE PROFILES                                                 │
│ ┌───────────────────────────────────────────────────────────┐         │
│ │ [602] Profile Name: [Accountant]                           │         │
│ │                                                            │         │
│ │ [603] Permissions:                                         │         │
│ │   [604] ☑ View QuickBooks Data                             │         │
│ │   [605] ☐ Access Checking Account Details                  │         │
│ │   [606] ☐ Access Credit Card Details                       │         │
│ │   [607] ☑ View All Reports                                 │         │
│ │                                                            │         │
│ │ [608] [Save Profile] [609] [+ Create New Profile]          │         │
│ └───────────────────────────────────────────────────────────┘         │
└─────────────────────────────────────────────────────────────────────────┘
```

#### iv. Notification Settings (in Settings)

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [701] NOTIFICATION SETTINGS                                             │
│ ┌───────────────────────────────────────────────────────────┐         │
│ │ [702] Overdue Task Alerts:                                 │         │
│ │ Send an alert if a delegated or automated task is not      │         │
│ │ detected within [703] [ 3 ▼] days of its expected date.    │         │
│ │                                                            │         │
│ │ [704] [Save Notification Settings]                         │         │
│ └───────────────────────────────────────────────────────────┘         │
└─────────────────────────────────────────────────────────────────────────┘
```

### c. Technical Implementation

-   **Database Schema Updates:**
    -   `playbook_items` table: Add `status` (Enum: `manual`, `automated`, `delegated`), `automation_rules` (JSON), and `delegated_to_user_id` (UUID).
    -   New `delegate_profiles` table: `id`, `name`, `permissions` (JSON).
    -   New `user_delegate_profiles` table to link users to these profiles.
-   **Notification Engine:**
    -   A service will handle sending emails for task delegation and overdue alerts.
    -   When a task is marked `Delegated`, an email will be sent to both the delegator and the delegatee with the task details.
-   **Overdue Task Checker:**
    -   A scheduled background job will run daily.
    -   It will scan for all `Automated` and `Delegated` tasks that are past their expected date by the user-defined threshold (default 3 days).
    -   If an overdue task is found, it will trigger an alert email to both parties.
-   **Permissions Logic:** When a delegated user logs in, the system will check their assigned profile to determine which data and features they can access.
