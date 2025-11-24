# Delegated Access Feature Specification

## Overview

The delegated access feature allows the primary user (Dwain) to grant limited, read-only access to specific financial data and reports to external parties, such as a tax professional or accountant. This ensures that sensitive financial information can be shared securely without compromising the user's account security.

---

## Use Case

**Primary User:** Dwain Henderson Jr. (Superior Networks LLC)

**Delegated User:** Tax Professional or Accountant

**Goal:** Allow the tax professional to view financial reports, scenarios, and account summaries without the ability to modify data or settings.

---

## Wireframe: Delegated Access Management (in Settings)

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  USER SETTINGS                                                         │
│                                                                         │
│  DELEGATED ACCESS                                                      │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Grant limited access to external parties (e.g., tax pros) │        │
│  │                                                            │        │
│  │ Active Delegations:                                        │        │
│  │                                                            │        │
│  │ ┌────────────────────────────────────────────────────┐   │        │
│  │ │ Tax Pro: john@taxfirm.com                          │   │        │
│  │ │ Access Level: Read-Only (Reports & Scenarios)      │   │        │
│  │ │ Granted: 11/01/25  |  Expires: 04/30/26           │   │        │
│  │ │ [Revoke Access] [Extend] [Edit Permissions]       │   │        │
│  │ └────────────────────────────────────────────────────┘   │        │
│  │                                                            │        │
│  │ [+ Grant New Delegated Access]                             │        │
│  │                                                            │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Wireframe: Grant New Delegated Access Dialog

```
┌─────────────────────────────────────────────────────────┐
│  Grant Delegated Access                                 │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Delegate Email: [_____________________________]        │
│                                                         │
│  Access Level:                                          │
│    ○ Read-Only (View reports and scenarios)             │
│    ○ Limited Edit (Can add notes, no data changes)      │
│                                                         │
│  Access Scope:                                          │
│    ☑ View all scenarios                                 │
│    ☑ View all reports                                   │
│    ☑ View account summaries (balances only)             │
│    ☐ View detailed transactions                         │
│                                                         │
│  Expiration Date: [MM/DD/YYYY] [_____________]          │
│                                                         │
│  [Cancel]  [Send Invitation]                            │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## Delegated User Experience

When the tax professional receives the invitation email:

1. **Invitation Email:**
   - Subject: "Dwain Henderson Jr. has invited you to view their Financial Playbook"
   - Body: "Click here to accept the invitation and create your delegated access account."

2. **Delegated User Login:**
   - The tax professional creates a separate account (or logs in with Google).
   - Upon login, they see a dashboard that clearly indicates they are viewing Dwain's data.

3. **Delegated Dashboard View:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook                                              │
│                                                                         │
│  Viewing: Dwain Henderson Jr. (Superior Networks LLC)                  │
│  Access Level: Read-Only  |  Expires: 04/30/26                         │
│                                                      [Tax Pro] [Logout] │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  AVAILABLE REPORTS                                                     │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Q4 2025 Operations Report                                  │        │
│  │ Generated: 11/23/25                                        │        │
│  │ [View Report] [Download PDF]                               │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Conservative Growth Scenario                               │        │
│  │ Created: 10/15/25                                          │        │
│  │ [View Scenario]                                            │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  ACCOUNT SUMMARIES                                                     │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐                  │
│  │ Total Balance│ │ Monthly Burn │ │ AR Outstanding│                  │
│  │   $45,230    │ │   -$5,100    │ │    $12,400    │                  │
│  └──────────────┘ └──────────────┘ └──────────────┘                  │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Technical Implementation

### Database Schema

**Table: `delegated_access`**

| Column | Type | Description |
|--------|------|-------------|
| `id` | UUID | Primary key |
| `owner_user_id` | UUID | Foreign key to the user granting access |
| `delegate_email` | String | Email of the delegated user |
| `delegate_user_id` | UUID | Foreign key to the delegated user (null until accepted) |
| `access_level` | Enum | `read_only`, `limited_edit` |
| `access_scope` | JSON | Permissions object (e.g., `{view_scenarios: true, view_reports: true}`) |
| `granted_at` | Timestamp | When access was granted |
| `expires_at` | Timestamp | When access expires |
| `revoked_at` | Timestamp | When access was revoked (null if active) |
| `invitation_token` | String | Unique token for invitation link |
| `accepted_at` | Timestamp | When the invitation was accepted |

---

### Access Control Logic

1. **When a delegated user logs in:**
   - Check the `delegated_access` table for active delegations.
   - If found, display the owner's data with the appropriate restrictions.

2. **Permission Checks:**
   - Before rendering any page, check if the current user is a delegated user.
   - If yes, enforce read-only restrictions (disable edit/delete buttons, prevent API calls for modifications).

3. **Audit Logging:**
   - Log all actions taken by delegated users for security and compliance.

---

### Security Considerations

1. **Expiration:** All delegated access must have an expiration date.
2. **Revocation:** The primary user can revoke access at any time.
3. **Scope Limitation:** Delegated users can only see what the primary user explicitly grants.
4. **No Cascading:** Delegated users cannot grant access to others.
5. **Audit Trail:** All delegated user actions are logged.

---

## User Stories

1. **As a primary user (Dwain), I want to grant my tax professional read-only access to my financial reports so they can prepare my taxes without needing to log into my account.**

2. **As a tax professional, I want to view my client's financial data in a secure, read-only environment so I can provide accurate tax advice without the risk of accidentally modifying their data.**

3. **As a primary user, I want to revoke delegated access at any time so I can control who has visibility into my financial information.**

4. **As a primary user, I want to set an expiration date for delegated access so I don't have to remember to manually revoke it after tax season.**

---

## Future Enhancements

- **Multiple Delegation Levels:** Add more granular permission levels (e.g., "View Only Summaries", "Full Read Access", "Read + Comment").
- **Delegation Notifications:** Notify the primary user when a delegated user logs in or views specific reports.
- **Delegation Activity Log:** Show the primary user a log of what the delegated user has viewed.
- **Delegation Templates:** Create reusable delegation templates for common use cases (e.g., "Tax Professional", "Business Partner").

---

This feature ensures that Dwain can securely share financial information with his tax professional while maintaining full control over his data and account security.
