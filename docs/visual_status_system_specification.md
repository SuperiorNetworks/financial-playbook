# Visual Status System Specification

## Overview

The Financial Playbook application uses a comprehensive **Traffic Light Visual Status System** to provide instant, at-a-glance feedback on the synchronization state and health of financial data between QuickBooks Online and the user's playbook scenarios.

This visual language is consistent throughout the entire application and provides contextual explanations for every status indicator.

---

## Core Design Principles

1. **Universal Application:** Status indicators appear consistently across all pages (Dashboard, Accounts, Scenarios, Reports, Calendar)
2. **Instant Recognition:** Color-coded visual cues provide immediate understanding without reading text
3. **Contextual Depth:** Every status indicator includes an info icon (ℹ️) that reveals detailed explanations
4. **Actionable Intelligence:** Status messages explain not just what is wrong, but what action to take
5. **Real-Time Updates:** Status indicators refresh automatically when data syncs occur

---

## Status Color System

### 🟢 GREEN - In Sync / Healthy

**Visual Treatment:**
- Subtle green halo/background glow around the element
- Green checkmark icon (✓) or green dot indicator
- Optional: Green border (1-2px solid)

**Meaning:**
- QuickBooks data and Playbook expectations are perfectly aligned
- All expected transactions have been found in QuickBooks
- No variances detected
- System is operating normally

**Example Scenarios:**
- A bill in the playbook matches exactly with a bill in QuickBooks (amount, date, vendor)
- An expected income transaction appears in QuickBooks within the expected timeframe
- Account balance in QuickBooks matches playbook projection within tolerance

**More Info Text Examples:**
> ✓ **In Sync** - This bill ($1,683.88 to Connectwise) matches the QuickBooks record exactly. Last verified: 5 minutes ago.

> ✓ **Healthy** - Your Chase account balance ($39,255.53) is tracking as expected. No issues detected.

---

### 🟡 YELLOW - Warning / Attention Needed

**Visual Treatment:**
- Yellow/amber halo/background glow around the element
- Yellow warning triangle icon (⚠️) or yellow dot indicator
- Optional: Yellow border (1-2px solid)

**Meaning:**
- Minor variance detected that requires attention
- Synchronization issue or delay
- Duplicate records found
- Price variance exceeds threshold but is not critical

**Example Scenarios:**
- A bill amount in QuickBooks differs from the playbook expectation by more than the threshold (default 3%)
- Synchronization with QuickBooks has not occurred in over 24 hours
- A duplicate transaction is detected in QuickBooks
- An expected payment date has shifted by a few days

**More Info Text Examples:**
> ⚠️ **Price Variance Detected** - Expected: $1,683.88 | QuickBooks: $1,700.00 | Variance: +$16.12 (0.96%). This exceeds your 3% threshold. Click "View in QuickBooks" to verify.

> ⚠️ **Sync Delayed** - Last sync was 26 hours ago. Click "Sync Now" to refresh data from QuickBooks.

> ⚠️ **Duplicate Found** - Two transactions for "IRS Payment - $600.00" found on 12/01/2025. Review in QuickBooks to resolve.

---

### 🔴 RED - Critical / Action Required

**Visual Treatment:**
- Red halo/background glow around the element (more prominent than yellow/green)
- Red alert icon (🚨) or red dot indicator
- Optional: Red border (2px solid) with subtle pulsing animation for urgent items

**Meaning:**
- Critical issue requiring immediate action
- Expected activity is missing from QuickBooks with deadline approaching
- Expected payment not found in register within critical window
- Overdraft risk or account balance critical threshold breached

**Example Scenarios:**
- A planned bill payment is 5 days away but no corresponding bill exists in QuickBooks
- An expected payment should have cleared 3 days ago but is not in the QuickBooks register
- Account balance is projected to go negative within 7 days
- A delegated task is overdue by more than the configured threshold (default 3 days)

**More Info Text Examples:**
> 🚨 **Critical: Missing Bill** - Miamisburg Loan payment of $5,627.01 is scheduled for Feb 15, 2026 (5 days away) but no bill exists in QuickBooks. Add this bill in QuickBooks immediately or adjust your playbook.

> 🚨 **Critical: Payment Missing** - Expected payment from Invoice #1234 ($5,200) was due 3 days ago but has not appeared in your QuickBooks register. Contact customer or verify payment status.

> 🚨 **Critical: Overdraft Risk** - Your Chase account is projected to go negative on Feb 15, 2026 (-$1,182.30). Review the full report for recommended solutions.

---

## Status Indicator Placement

### Dashboard Page
- **Alert Cards:** Each alert has a status color on the left border
- **Quick Stats Cards:** Small status dot in top-right corner
- **Cash Flow Chart:** Color-coded event markers on timeline

### Accounts Management Page
- **QuickBooks Connection Status:** Large status indicator next to "Connected ✓"
- **Individual Account Cards:** Status indicator next to account name
- **Bills List:** Status dot next to each bill
- **Invoices List:** Status dot next to each invoice

### Scenario Planning Page
- **Scenario Cards:** Status indicator in header showing overall scenario health
- **Individual Rules:** Status dot next to each rule in the logic editor

### Playbook Report Page
- **Executive Summary:** Overall playbook status at the top
- **Critical Issues Section:** Each issue has prominent status indicator
- **Account Registers:** Status indicators on individual transactions

### Calendar Page (New)
- **Calendar Events:** Color-coded by status (green/yellow/red background)
- **Event Details:** Status explanation in event tooltip

---

## Info Icon & Tooltip System

### Visual Design
- Small info icon (ℹ️) or circled "i" appears next to every status indicator
- Icon is subtle but clearly clickable/hoverable
- On hover: Show brief tooltip preview
- On click: Open detailed modal/popover with full explanation

### Tooltip Content Structure
```
[Status Icon] [Status Title]
[Brief explanation of the issue]
[Specific details: expected vs. actual values]
[Recommended action]
[Timestamp: "Last checked: X minutes ago"]
```

### Modal Content Structure (for complex issues)
```
[Large Status Icon] [Status Title]

What's Happening:
[Detailed explanation of the status]

Details:
• Expected: [value]
• Actual: [value]
• Variance: [calculation]
• Last Synced: [timestamp]

Recommended Actions:
1. [Action 1]
2. [Action 2]

[View in QuickBooks Button] [Dismiss Button]
```

---

## Status Logic Rules & Thresholds

### GREEN Status Conditions
- QuickBooks transaction matches playbook expectation within tolerance
- Amount variance: ≤ configured threshold (default 3%)
- Date variance: ≤ 2 days
- Last sync: < 24 hours ago
- No duplicates detected

### YELLOW Status Conditions
- Amount variance: > 3% but < 10%
- Date variance: 3-7 days
- Last sync: 24-48 hours ago
- Duplicate transaction detected
- Minor data inconsistency

### RED Status Conditions
- Expected activity within 5 days not found in QuickBooks
- Expected payment within 3 days missing from register
- Amount variance: > 10%
- Last sync: > 48 hours ago
- Overdraft projected within 7 days
- Delegated task overdue by > 3 days

### Configurable Thresholds (in Settings)
Users can adjust these thresholds:
- Price variance tolerance: 1%, 3%, 5%, 10%
- Critical activity warning window: 3, 5, 7 days
- Missing payment alert window: 1, 3, 5 days
- Sync delay warning: 12, 24, 48 hours

---

## Implementation Guidelines

### CSS/Tailwind Classes
```css
/* Green Status */
.status-green {
  background: rgba(34, 197, 94, 0.1); /* Subtle green glow */
  border: 1px solid rgb(34, 197, 94);
  box-shadow: 0 0 10px rgba(34, 197, 94, 0.3);
}

/* Yellow Status */
.status-yellow {
  background: rgba(234, 179, 8, 0.1); /* Subtle yellow glow */
  border: 1px solid rgb(234, 179, 8);
  box-shadow: 0 0 10px rgba(234, 179, 8, 0.3);
}

/* Red Status */
.status-red {
  background: rgba(239, 68, 68, 0.1); /* Subtle red glow */
  border: 2px solid rgb(239, 68, 68);
  box-shadow: 0 0 15px rgba(239, 68, 68, 0.4);
  animation: pulse 2s infinite; /* Optional for critical items */
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.7; }
}
```

### React Component Structure
```typescript
interface StatusIndicatorProps {
  status: 'green' | 'yellow' | 'red';
  title: string;
  message: string;
  details?: {
    expected?: string;
    actual?: string;
    variance?: string;
    lastChecked?: Date;
  };
  actions?: Array<{
    label: string;
    onClick: () => void;
  }>;
}

const StatusIndicator: React.FC<StatusIndicatorProps> = ({ ... }) => {
  // Render status dot/halo, info icon, and tooltip/modal
};
```

### Database Schema Addition
```typescript
// Add to existing tables
status: mysqlEnum("status", ["green", "yellow", "red"]).default("green"),
statusMessage: text("status_message"),
statusDetails: json("status_details"), // Store expected, actual, variance
lastStatusCheck: timestamp("last_status_check").defaultNow(),
```

---

## Google Calendar Integration

### Calendar View Page
- New navigation item: "Calendar" [QC: 221]
- Full-month calendar view with color-coded events
- Event colors match status system (green/yellow/red)
- Click event to see full details with status explanation

### Event Types
1. **Bills & Payables** (from QuickBooks + Playbook)
2. **Expected Income** (from Playbook projections)
3. **Delegated Tasks** (if multi-user enabled in future)
4. **Scenario Milestones** (user-defined in playbook)

### Two-Way Sync
- Playbook activities automatically create Google Calendar events
- Changes in Google Calendar can optionally sync back to Playbook
- Status indicators show if Calendar and Playbook are in sync

### Calendar Event Status
- **Green Event:** Activity is confirmed in both Playbook and QuickBooks
- **Yellow Event:** Activity is in Playbook but not yet in QuickBooks (warning window)
- **Red Event:** Activity is critical and missing from QuickBooks

---

## User Experience Flow

### Example: User Sees Yellow Status on Dashboard

1. User logs in and sees Dashboard
2. Alert card shows: "⚠️ Connectwise Bill - Price Variance"
3. Card has yellow halo background
4. User hovers over info icon (ℹ️)
5. Tooltip appears: "Expected: $1,683.88 | Actual: $1,700.00"
6. User clicks info icon
7. Modal opens with full details:
   - What's happening: Price increased by $16.12
   - Variance: 0.96% (exceeds 3% threshold)
   - Recommended action: Review bill in QuickBooks
8. User clicks "View in QuickBooks" button
9. Opens QuickBooks in new tab to verify
10. User returns, clicks "Sync Now" to refresh
11. Status updates to green after sync confirms

---

## Accessibility Considerations

- **Color Blindness:** Do not rely solely on color; always include icon + text
- **Screen Readers:** Proper ARIA labels for all status indicators
- **Keyboard Navigation:** Info icons must be keyboard accessible
- **High Contrast Mode:** Ensure status indicators remain visible

---

## Testing Checklist

- [ ] Green status displays correctly across all pages
- [ ] Yellow status displays correctly across all pages
- [ ] Red status displays correctly across all pages
- [ ] Info icons are visible and clickable on all status indicators
- [ ] Tooltips display on hover
- [ ] Modals open on click with full details
- [ ] Status updates in real-time after sync
- [ ] Thresholds can be configured in Settings
- [ ] Status system works with keyboard navigation
- [ ] Status system works with screen readers
- [ ] Calendar events display with correct status colors
- [ ] Google Calendar sync creates events correctly

---

**Document Version:** 1.0  
**Last Updated:** November 23, 2025  
**Related:** Financial Playbook Complete Documentation v8.0
