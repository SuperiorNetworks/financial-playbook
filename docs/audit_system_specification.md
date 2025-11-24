# Comprehensive Audit Trail System Specification

## 1. Overview

To ensure data integrity, security, and accountability, a comprehensive **Audit Trail System** will be integrated into the Financial Playbook application. This system will automatically log all significant actions performed by users, delegated users, and the system itself. The audit log will provide a clear, filterable history of who changed what, and when, making it an essential tool for security reviews, debugging, and maintaining a transparent record of all activities.

---

## 2. Key Requirements

- **Immutability:** Audit logs cannot be altered or deleted by any user.
- **Comprehensiveness:** All critical actions must be logged.
- **Clarity:** Logs must be human-readable and provide sufficient context.
- **Accessibility:** The primary user must be able to easily view, filter, and export the audit trail.

---

## 3. Wireframe: Audit Trail Report Page

This new report will be accessible via the main navigation, likely under a new "Activity" or "Reports" tab.

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  AUDIT TRAIL REPORT                                                     │
│                                                                         │
│  FILTERS:                                                               │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Date Range: [11/01/25] to [11/23/25]                      │        │
│  │ User: [All Users ▼] (Dwain, john@taxfirm.com, System)     │        │
│  │ Action Type: [All Actions ▼] (Create, Update, Delete...)  │        │
│  │                                                            │        │
│  │ [Apply Filters] [Reset] [Export CSV]                       │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  ACTIVITY LOG                                                          │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Timestamp           | User                | Action         │        │
│  │---------------------|---------------------|----------------│        │
│  │ 11/23/25 11:15 AM   | Dwain Henderson Jr. | UPDATE Scenario│        │
│  │  ↳ Changed `Monthly Income` from $8,200 to $8,500. [Details] │        │
│  ├-----------------------------------------------------------┤        │
│  │ 11/23/25 10:30 AM   | john@taxfirm.com    | VIEW Report    │        │
│  │  ↳ Viewed "Q4 2025 Operations Report". [Details]           │        │
│  ├-----------------------------------------------------------┤        │
│  │ 11/22/25 08:00 PM   | System              | SYNC QuickBooks│        │
│  │  ↳ Synced 15 new transactions from QuickBooks. [Details]   │        │
│  ├-----------------------------------------------------------┤        │
│  │ 11/22/25 04:10 PM   | Dwain Henderson Jr. | GRANT Access   │        │
│  │  ↳ Granted read-only access to john@taxfirm.com. [Details] │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

Clicking **[Details]** would open a modal showing the raw `change_details` JSON, providing a before-and-after snapshot of the data.

---

## 4. Technical Implementation

### Actions to be Logged

The system will log the following events:

| Category | Action | Description |
|---|---|---|
| **User Management** | `LOGIN`, `LOGOUT`, `UPDATE_PROFILE` | User authentication and profile changes. |
| **Data Entities** | `CREATE`, `UPDATE`, `DELETE` | Any change to Scenarios, Bills, Invoices, Accounts. |
| **Delegated Access**| `GRANT_ACCESS`, `REVOKE_ACCESS`, `VIEW_DATA` | Actions related to delegated users. |
| **System Events** | `SYNC_QUICKBOOKS`, `AI_ANALYSIS` | Automated system processes. |
| **Reports** | `GENERATE_REPORT`, `EXPORT_REPORT` | Creation and export of financial reports. |

### Database Schema

A new table, `audit_logs`, will be created.

**Table: `audit_logs`**

| Column | Type | Description |
|---|---|---|
| `id` | UUID | Primary key for the log entry. |
| `timestamp` | Timestamp | The exact date and time the action occurred (UTC). |
| `user_id` | UUID | Foreign key to the `users` table. Identifies who performed the action. Can be null for system actions. |
| `user_name` | String | The name of the user for easy display (e.g., "Dwain Henderson Jr.", "System"). |
| `action_type` | Enum | The type of action performed (e.g., `UPDATE`, `CREATE`, `LOGIN`). |
| `target_entity` | String | The type of object that was affected (e.g., "Scenario", "Bill", "User"). |
| `target_id` | String | The unique ID of the specific object that was affected. |
| `change_details` | JSON | A JSON object containing `before` and `after` keys, showing the state of the data that was changed. |
| `description` | String | A human-readable summary of the event (e.g., "User updated the 'Q4 2025 Operations' scenario."). |

### Example `change_details` JSON for an UPDATE action:

```json
{
  "before": {
    "monthly_income": 8200
  },
  "after": {
    "monthly_income": 8500
  }
}
```

### Implementation Logic

- **Middleware/Hooks:** The audit logging logic will be implemented using middleware in the backend API or database hooks. Before any `CREATE`, `UPDATE`, or `DELETE` operation is committed, a pre-save hook will capture the current state (`before`) and the new state (`after`) of the data.
- **Asynchronous Logging:** To avoid impacting application performance, audit log entries will be written to the database asynchronously.

---

## 5. Benefits

- **Enhanced Security:** Provides a clear record of all activities, helping to detect and investigate suspicious behavior, especially from delegated accounts.
- **Accountability:** Creates an undeniable record of who is responsible for every data modification.
- **Change Tracking:** Makes it easy to understand the history of a specific scenario or financial entry, which is invaluable for debugging and analysis.
- **Compliance:** For any future business needs, having a robust audit trail is often a requirement for financial compliance standards.

This audit system provides a powerful layer of security and transparency, making the Financial Playbook application a truly enterprise-ready platform.
