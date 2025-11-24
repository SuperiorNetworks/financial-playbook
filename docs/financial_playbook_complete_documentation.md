# Financial Playbook Application: Complete Documentation

This document provides a comprehensive overview of the Financial Playbook application, including wireframes, technical specifications, and integration details.

---

## Wireframes & Component Overview

## Application Overview

**AI-Driven Financial Playbook Website** - A user-authenticated web application that provides comprehensive financial scenario planning, cash flow monitoring, and automated risk analysis with real-time notifications.

---

## Wireframe 1: Login / Authentication Page

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│              FINANCIAL PLAYBOOK SYSTEM                  │
│                                                         │
│         ┌─────────────────────────────────┐            │
│         │                                 │            │
│         │   Email: [________________]     │            │
│         │                                 │            │
│         │   Password: [____________]      │            │
│         │                                 │            │
│         │        [  LOGIN  ]              │            │
│         │                                 │            │
│         │   [ Forgot Password? ]          │            │
│         │   [ Create New Account ]        │            │
│         │                                 │            │
│         │        [ Sign in with Google ]    │            │
│         │                                 │            │
│         └─────────────────────────────────┘            │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

**Components:**
- User authentication form
- Session management
- Password recovery
- New user registration
- Google Authentication (OAuth 2.0)

---

## Wireframe 2: Dashboard / Home Page

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  ⚠️ ACTIVE ALERTS                                                       │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ • Overdraft Risk: Chase Account - Projected 12/15/2025    │        │
│  │ • Large AR Lag: Invoice #1234 - 45 days overdue           │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  CURRENT SCENARIO: "Q4 2025 Operations"                               │
│  ┌─────────────────────────────────────────────────────────┐          │
│  │                                                           │          │
│  │    [Cash Flow Chart - Interactive]                       │          │
│  │    Balance over Time with Event Markers                  │          │
│  │                                                           │          │
│  └─────────────────────────────────────────────────────────┘          │
│                                                                         │
│  QUICK STATS                                                           │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐                  │
│  │ Total Balance│ │ Monthly Burn │ │ AR Outstanding│                  │
│  │   $45,230    │ │   -$5,100    │ │    $12,400    │                  │
│  └──────────────┘ └──────────────┘ └──────────────┘                  │
│                                                                         │
│  [+ New Scenario] [View All Scenarios] [Generate Report]              │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

**Components:**
- Alert notification system (user-specific)
- Active scenario selector
- Interactive cash flow visualization
- Quick stats dashboard
- Navigation menu

---

## Wireframe 3: Accounts Management Page

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  CONNECTED ACCOUNTS                          [+ Add Account] [Sync All]│
│                                                                         │
│  Bank Accounts                                                         │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Chase Business Checking    ****1234   $23,450  [Edit][Sync]│       │
│  │ Capital One Savings        ****5678   $21,780  [Edit][Sync]│       │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  Credit Cards                                                          │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Chase Business Card        ****9012   -$3,200  [Edit][Sync]│       │
│  │ Capital One Card           ****3456   -$1,850  [Edit][Sync]│       │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  INTEGRATIONS                                                          │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ QuickBooks Online: Connected ✓        Last Sync: 2 hrs ago │       │
│  │ [Configure] [Disconnect]                                   │       │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  BILLS & RECURRING EXPENSES                      [+ Add Bill]          │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Rent                $2,500   Monthly   15th   [Edit][Delete]│      │
│  │ Insurance           $450     Monthly   1st    [Edit][Delete]│      │
│  │ Software Licenses   $300     Monthly   10th   [Edit][Delete]│      │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  ACCOUNTS RECEIVABLE                             [+ Add Invoice]       │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Invoice #1234   $5,000   Due: 11/30/25   45 days  [Edit]  │       │
│  │ Invoice #1235   $3,200   Due: 12/15/25   30 days  [Edit]  │       │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

**Components:**
- Bank account connections (API integration)
- Credit card tracking
- QuickBooks Online integration
- Bills and recurring expenses management
- Accounts receivable tracking
- Manual data entry forms
- Data import/upload functionality

---

## Wireframe 4: Scenario Planning Page

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  SCENARIOS                                          [+ Create Scenario] │
│                                                                         │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ ⭐ Q4 2025 Operations (LOCKED)                             │        │
│  │    Created: 11/01/25  |  Monitoring: Active               │        │
│  │    [View] [Edit] [Unlock] [Generate Report]               │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Conservative Growth - What If                              │        │
│  │    Created: 10/15/25  |  Status: Draft                    │        │
│  │    [View] [Edit] [Lock In] [Delete]                       │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Aggressive Expansion - What If                             │        │
│  │    Created: 10/10/25  |  Status: Draft                    │        │
│  │    [View] [Edit] [Lock In] [Delete]                       │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

**Components:**
- Scenario list (user-specific)
- Scenario status (Draft, Locked, Active)
- Scenario creation wizard
- "What-if" modeling engine
- Lock-in functionality for active monitoring

---

## Wireframe 5: Scenario Editor / What-If Modeling

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  SCENARIO: "Q4 2025 Operations"                     [Save] [Preview]   │
│                                                                         │
│  PARAMETERS                                                            │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Time Range: [11/01/25] to [12/31/25]                      │        │
│  │                                                            │        │
│  │ Monthly Income:        $8,500  [_______]                  │        │
│  │ Monthly Expenses:      $13,600 [_______]                  │        │
│  │ Expected AR Collection: $15,000 [_______]                 │        │
│  │ AR Collection Date:    12/15/25 [_______]                 │        │
│  │                                                            │        │
│  │ One-Time Expenses:                                         │        │
│  │   • Equipment Purchase: $5,000 on 11/20/25 [Edit][Remove] │        │
│  │   [+ Add One-Time Expense]                                 │        │
│  │                                                            │        │
│  │ Credit Card Payoff Plan:                                   │        │
│  │   • Chase Card: $500/month starting 11/01/25               │        │
│  │   [Edit Payment Plan]                                      │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  [Run Simulation]                                                      │
│                                                                         │
│  SIMULATION RESULTS                                                    │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │                                                            │        │
│  │    [Interactive Cash Flow Chart]                          │        │
│  │    [Debt Paydown Chart]                                   │        │
│  │                                                            │        │
│  │  ⚠️ RISKS DETECTED:                                        │        │
│  │  • Overdraft risk on 12/05/25 (-$1,200)                   │        │
│  │  • Reserve drops below $5,000 on 11/28/25                 │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  [Lock In This Scenario] [Export Report] [Adjust Parameters]          │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

**Components:**
- Parameter input forms
- Variable adjustment sliders/inputs
- Simulation engine
- Real-time chart updates
- Risk detection and display
- Scenario comparison tools

---
## Wireframe 6: Playbook Report View

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  PLAYBOOK REPORT: "Q4 2025 Operations"                                 │
│  Generated: 11/23/25 10:30 AM                                          │
│                                                                         │
│  [Export PDF] [Export Word] [Export Markdown] [Export CSV] [Email]    │
│                                                                         │
│  ┌─────────────────────────────────────────────────────────┐          │
│  │ EXECUTIVE SUMMARY                                        │          │
│  │                                                          │          │
│  │ Current spending exceeds income by $5,100/month.        │          │
│  │ Critical risks identified:                               │          │
│  │ • Overdraft on 12/05/25                                 │          │
│  │ • Reserve breach on 11/28/25                            │          │
│  │                                                          │          │
│  │ Recommendations:                                         │          │
│  │ 1. Accelerate AR collection                             │          │
│  │ 2. Defer equipment purchase to 12/20/25                │          │
│  │ 3. Reduce discretionary spending by $1,500/month       │          │
│  └─────────────────────────────────────────────────────────┘          │
│                                                                         │
│  ┌─────────────────────────────────────────────────────────┐          │
│  │ REGISTER: CHASE BUSINESS CHECKING                        │          │
│  │                                                          │          │
│  │ Date     | Description        | Change    | Balance     │          │
│  │----------|-------------------|-----------|-------------|          │
│  │ 11/01/25 | Starting Balance  |    $0     | $23,450     │          │
│  │ 11/01/25 | Rent Payment      | -$2,500   | $20,950     │          │
│  │ 11/05/25 | Client Payment    | +$3,200   | $24,150     │          │
│  │ 11/10/25 | Software License  |   -$300   | $23,850     │          │
│  │ ...      | ...               |   ...     | ...         │          │
│  └─────────────────────────────────────────────────────────┘          │
│                                                                         │
│  ┌─────────────────────────────────────────────────────────┐          │
│  │ CHARTS                                                   │          │
│  │                                                          │          │
│  │ [Cash Flow Over Time - with Event Markers]              │          │
│  │ [Debt Paydown Progress]                                 │          │
│  │ [Credit Card Interest Trends]                           │          │
│  └─────────────────────────────────────────────────────────┘          │
│                                                                         │
│  ┌─────────────────────────────────────────────────────────┐          │
│  │ ASSUMPTIONS VS. FACTS                                    │          │
│  │                                                          │          │
│  │ Assumptions (System Generated):                          │          │
│  │ • Monthly income: $8,500 (based on 3-month average)    │          │
│  │ • AR collection date: 12/15/25 (estimated)             │          │
│  │                                                          │          │
│  │ Facts (User Provided/Linked):                           │          │
│  │ • Rent: $2,500 (from QuickBooks)                       │          │
│  │ • Chase balance: $23,450 (live sync)                   │          │
│  └─────────────────────────────────────────────────────────┘          │
│                                                                         │
│  ┌─────────────────────────────────────────────────────────┐          │
│  │ NEXT STEPS                                               │          │
│  │                                                          │          │
│  │ 1. Contact client for Invoice #1234 payment             │          │
│  │ 2. Review and reduce discretionary expenses             │          │
│  │ 3. Monitor cash position daily through 12/05/25        │          │
│  └─────────────────────────────────────────────────────────┘          │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

**Components:**
- Executive summary generator
- Register tables (checkbook style) for each account
- Chart rendering (PNG/SVG export)
- Assumptions vs. Facts section
- Recommendations engine
- Multi-format export (PDF, Word, Markdown, CSV)
- Email delivery system

---

## Wireframe 7: Settings & Notifications

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  USER SETTINGS                                                         │
│                                                                         │
│  PROFILE                                                               │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Name: Dwain Henderson Jr.                                  │        │
│  │ Email: dwain@superiornetworks.com                          │        │
│  │ Company: Superior Networks LLC                             │        │
│  │ Timezone: America/New_York (EST)                           │        │
│  │                                                            │        │
│  │ [Update Profile] [Change Password]                         │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  NOTIFICATION PREFERENCES                                              │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Email Notifications:                                       │        │
│  │   ☑ Critical Risks (Overdraft, Reserve Breach)            │        │
│  │   ☑ Large AR Lag (>30 days)                               │        │
│  │   ☑ Weekly Summary Reports                                │        │
│  │   ☐ Daily Balance Updates                                 │        │
│  │                                                            │        │
│  │ Notification Recipients:                                   │        │
│  │   • dwain@superiornetworks.com (Primary)                  │        │
│  │   • assistant@superiornetworks.com [Remove]               │        │
│  │   [+ Add Recipient]                                        │        │
│  │                                                            │        │
│  │ SMS/Push Notifications (Future Feature - Wishlist)         │        │
│  │   ☐ Enable SMS alerts                                     │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  ALERT THRESHOLDS                                                      │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Overdraft Warning:        $0      [_______]                │        │
│  │ Low Reserve Warning:      $5,000  [_______]                │        │
│  │ AR Aging Alert:           30 days [_______]                │        │
│  │                                                            │        │
│  │ [Save Thresholds]                                          │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
│  QA & REPORT TEMPLATE                                                  │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Current Gold-Standard Template: "Default Playbook v1.0"    │        │
│  │                                                            │        │
│  │ [Upload New Template] [Preview Current Template]           │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

**Components:**
- User profile management
- Email notification settings
- Multi-recipient notification system
- Alert threshold configuration
- Template management for QA enforcement
- Timezone settings

---

## System Architecture Components Summary

### 1. **Authentication & User Management**
- User registration and login
- Session management
- Password recovery
- Multi-user support with data isolation

### 2. **Data Integration Layer**
- Bank account API connections
- QuickBooks Online integration
- Manual data entry forms
- CSV/Excel import functionality
- Data validation and normalization

### 3. **Financial Data Management**
- Account tracking (bank accounts, credit cards)
- Bills and recurring expenses
- Accounts receivable tracking
- Transaction history
- Real-time balance updates

### 4. **Scenario Engine**
- What-if modeling
- Parameter adjustment
- Simulation calculations
- Multi-scenario comparison
- Scenario locking and monitoring

### 5. **Analysis & Risk Detection**
- Automated financial analysis
- Risk identification (overdrafts, reserve breaches, AR lag)
- Trend analysis
- Recommendations engine
- Assumptions vs. Facts tracking

### 6. **Visualization & Reporting**
- Interactive charts (cash flow, debt paydown, interest trends)
- Register tables (checkbook style)
- Event markers on charts
- Multi-format export (PDF, Word, Markdown, CSV)
- Chart export (PNG, SVG)

### 7. **Quality Assurance System**
- Template comparison engine
- Report validation before export
- Preview mode
- Deviation detection and flagging

### 8. **Notification System**
- Real-time risk monitoring
- Email alerts (critical risks)
- Multi-recipient support
- Configurable alert thresholds
- Weekly summary reports

### 9. **Export & Collaboration**
- PDF generation
- Word document export
- Markdown export
- CSV export for tables
- Email delivery
- Future: Audit logs, collaboration features

---

## Data Flow Diagram

```
┌──────────────┐
│   User       │
│   Login      │
└──────┬───────┘
       │
       v
┌──────────────────────────────────────────────────┐
│           User Dashboard                         │
│  (Shows only user's own data)                   │
└──────┬───────────────────────────────────────────┘
       │
       ├─────> Accounts Management
       │         │
       │         ├─> Bank API Integration
       │         ├─> QuickBooks Sync (with real-time webhook updates)
       │         └─> Manual Entry
       │
       ├─────> Scenario Planning
       │         │
       │         ├─> Create/Edit Scenarios
       │         ├─> Run Simulations
       │         └─> Lock In Scenario
       │
       ├─────> Reports Generation
       │         │
       │         ├─> Generate Playbook Report
       │         ├─> QA Validation
       │         └─> Export (PDF/Word/CSV)
       │
       └─────> Settings & Notifications
                 │
                 ├─> Configure Alerts
                 ├─> Set Thresholds
                 └─> Manage Recipients
                 
┌──────────────────────────────────────────────────┐
│   Background Monitoring Service                  │
│   (Runs continuously for locked scenarios)       │
│                                                  │
│   ├─> Receives real-time updates from QuickBooks Webhooks │
│   ├─> Re-runs simulations on data change        │
│   ├─> Checks for new risk conditions            │
│   ├─> Compares against thresholds               │
│   └─> Sends email alerts when triggered         │
└──────────────────────────────────────────────────┘
```

---

## Technology Stack Considerations

### Frontend
- Modern responsive UI framework
- Interactive charting library
- Real-time data updates
- Mobile-responsive design

### Backend
- User authentication and authorization
- RESTful API for data operations
- Background job processing for monitoring
- Database with user data isolation

### Database
- User accounts and profiles
- Financial accounts and transactions
- Scenarios and simulations
- Bills, expenses, and AR data
- Notification logs

### External Integrations
- Bank account APIs (Plaid, Yodlee, or similar)
- QuickBooks Online API
- Email service (SendGrid, AWS SES, or similar)
- Future: SMS gateway for text alerts

### Security
- Encrypted data storage
- Secure API connections
- User data isolation
- Session management
- HTTPS/SSL

---

## Next Steps for Discussion

I've created comprehensive wireframes for your Financial Playbook application. Now I need to ask you some key questions to refine the design before we build:

### Critical Questions:

1. **User Roles & Access:**
   - Will you be the only user initially, or do you plan to have multiple users (clients, team members)?
   - Do you need different permission levels (admin, viewer, editor)?

2. **Bank Integration Priority:**
   - Which bank account integration is most important? (Plaid is common for US banks)
   - Do you already have QuickBooks Online, or is this a future integration?

3. **Data Entry Workflow:**
   - For the initial version, would you prefer to start with manual data entry, or is live bank integration essential from day one?
   - How often do you want to sync data (real-time, daily, manual)?

4. **Notification Details:**
   - What email address(es) should receive critical alerts?
   - What time of day do you prefer to receive weekly summary reports?

5. **Report Customization:**
   - Do you have an existing "gold-standard" playbook template you want to match, or should we create a default template?
   - What specific charts are most important to you? (Cash flow, debt paydown, expense breakdown, etc.)

6. **Deployment Preferences:**
   - Where do you want this hosted? (Your own server, cloud service like AWS/Azure, or a simple hosting platform?)
   - Do you need this accessible from mobile devices?

7. **Timeline & MVP:**
   - What features are absolutely essential for version 1.0?
   - What features can be added later as enhancements?

8. **Business Context:**
   - Is this primarily for Superior Networks LLC's internal use, or do you plan to offer it as a service to clients?
   - What's your typical monthly transaction volume?

Please review the wireframes and let me know your thoughts on these questions so we can tailor the application to your exact needs!
### 7. **Quality Assurance System**
- Template comparison engine
- Report validation before export
- Preview mode
- Deviation detection and flagging

### 8. **Notification System**
- Real-time risk monitoring
- Email alerts (critical risks)
- Multi-recipient support
- Configurable alert thresholds
- Weekly summary reports

### 9. **Export & Collaboration**
- PDF generation
- Word document export
- Markdown export
- CSV export for tables
- Email delivery
- Future: Audit logs, collaboration features

---

## Data Flow Diagram

```
┌──────────────┐
│   User       │
│   Login      │
└──────┬───────┘
       │
       v
┌──────────────────────────────────────────────────┐
│           User Dashboard                         │
│  (Shows only user's own data)                   │
└──────┬───────────────────────────────────────────┘
       │
       ├─────> Accounts Management
       │         │
       │         ├─> Bank API Integration
       │         ├─> QuickBooks Sync (with real-time webhook updates)
       │         └─> Manual Entry
       │
       ├─────> Scenario Planning
       │         │
       │         ├─> Create/Edit Scenarios
       │         ├─> Run Simulations
       │         └─> Lock In Scenario
       │
       ├─────> Reports Generation
       │         │
       │         ├─> Generate Playbook Report
       │         ├─> QA Validation
       │         └─> Export (PDF/Word/CSV)
       │
       └─────> Settings & Notifications
                 │
                 ├─> Configure Alerts
                 ├─> Set Thresholds
                 └─> Manage Recipients
                 
┌──────────────────────────────────────────────────┐
│   Background Monitoring Service                  │
│   (Runs continuously for locked scenarios)       │
│                                                  │
│   ├─> Receives real-time updates from QuickBooks Webhooks │
│   ├─> Re-runs simulations on data change        │
│   ├─> Checks for new risk conditions            │
│   ├─> Compares against thresholds               │
│   └─> Sends email alerts when triggered         │
└──────────────────────────────────────────────────┘
```

---

## Technology Stack Considerations

### Frontend
- Modern responsive UI framework
- Interactive charting library
- Real-time data updates
- Mobile-responsive design

### Backend
- User authentication and authorization
- RESTful API for data operations
- Background job processing for monitoring
- Database with user data isolation

### Database
- User accounts and profiles
- Financial accounts and transactions
- Scenarios and simulations
- Bills, expenses, and AR data
- Notification logs

### External Integrations
- Bank account APIs (Plaid, Yodlee, or similar)
- QuickBooks Online API
- Email service (SendGrid, AWS SES, or similar)
- Future: SMS gateway for text alerts

### Security
- Encrypted data storage
- Secure API connections
- User data isolation
- Session management
- HTTPS/SSL

---

## Next Steps for Discussion

I've created comprehensive wireframes for your Financial Playbook application. Now I need to ask you some key questions to refine the design before we build:

### Critical Questions:

1. **User Roles & Access:**
   - Will you be the only user initially, or do you plan to have multiple users (clients, team members)?
   - Do you need different permission levels (admin, viewer, editor)?

2. **Bank Integration Priority:**
   - Which bank account integration is most important? (Plaid is common for US banks)
   - Do you already have QuickBooks Online, or is this a future integration?

3. **Data Entry Workflow:**
   - For the initial version, would you prefer to start with manual data entry, or is live bank integration essential from day one?
   - How often do you want to sync data (real-time, daily, manual)?

4. **Notification Details:**
   - What email address(es) should receive critical alerts?
   - What time of day do you prefer to receive weekly summary reports?

5. **Report Customization:**
   - Do you have an existing "gold-standard" playbook template you want to match, or should we create a default template?
   - What specific charts are most important to you? (Cash flow, debt paydown, expense breakdown, etc.)

6. **Deployment Preferences:**
   - Where do you want this hosted? (Your own server, cloud service like AWS/Azure, or a simple hosting platform?)
   - Do you need this accessible from mobile devices?

7. **Timeline & MVP:**
   - What features are absolutely essential for version 1.0?
   - What features can be added later as enhancements?

8. **Business Context:**
   - Is this primarily for Superior Networks LLC's internal use, or do you plan to offer it as a service to clients?
   - What's your typical monthly transaction volume?

Please review the wireframes and let me know your thoughts on these questions so we can tailor the application to your exact needs!


---

## Integration Feasibility Report: Google Auth, QuickBooks Online & Real-Time Updates

This document outlines the technical feasibility, approach, and implications of integrating Google Authentication, QuickBooks Online, and real-time data synchronization into the Financial Playbook application.

---

## 1. Google Authentication

**Feasibility:** **High**. Integrating Google Authentication is a standard and well-documented process.

**Approach:**
We will use the **OAuth 2.0** protocol, which is the industry standard for secure delegated access [1]. The process involves:

1.  **Creating a Google API Console Project:** We will set up a new project in the Google API Console to obtain OAuth 2.0 client credentials (a client ID and client secret) for the application.
2.  **Implementing a "Sign in with Google" Button:** A "Sign in with Google" button will be added to the login page. This will redirect users to Google's authentication server.
3.  **Handling the OAuth 2.0 Flow:** After the user grants permission, Google will redirect back to our application with an authorization code. Our backend will exchange this code for an access token and a refresh token.
4.  **User Profile Creation:** We will use the access token to retrieve the user's profile information (name, email, profile picture) from the Google People API. This information will be used to create a new user account in our application's database or link to an existing one.
5.  **Session Management:** Upon successful authentication, a session will be created for the user, granting them access to their personalized dashboard.

**Benefits:**
- **Enhanced Security:** Leverages Google's robust security infrastructure.
- **Improved User Experience:** Simplifies the login process, as users won't need to create and remember a separate password for this application.
- **Faster Registration:** New users can sign up with a single click.

**Wireframe Update:** The login page wireframe will be updated to include a "Sign in with Google" button.

---

## 2. QuickBooks Online Integration

**Feasibility:** **High**. The QuickBooks Online API is well-documented and provides the necessary endpoints to access financial data [2].

**Approach:**
We will use the **QuickBooks Online API** to establish a live connection to your QuickBooks account. This will also use the OAuth 2.0 protocol for authentication.

1.  **Creating an Intuit Developer Account & App:** We will create an Intuit Developer account and register our application to get API keys and credentials.
2.  **Implementing the QuickBooks Connection Flow:** In the "Accounts Management" section of the application, there will be an option to "Connect to QuickBooks." This will initiate an OAuth 2.0 flow similar to Google's, where you will be asked to authorize our application to access your QuickBooks data.
3.  **Data Synchronization:** Once authorized, the application will be able to make API calls to your QuickBooks Online account to fetch data such as:
    -   Chart of Accounts
    -   Bank and Credit Card account balances and transactions
    -   Invoices (Accounts Receivable)
    -   Bills and Expenses (Accounts Payable)
    -   Customers and Vendors
4.  **Data Mapping:** The data retrieved from QuickBooks will be mapped to the corresponding fields in our application's database, ensuring consistency and accuracy.

**Benefits:**
- **Automation:** Eliminates the need for manual data entry, saving time and reducing errors.
- **Real-time Data:** Ensures that the financial playbook is always based on the most up-to-date information from your accounting system.
- **Comprehensive Financial Picture:** Provides a holistic view of your finances by combining data from bank accounts and your accounting software.

**Wireframe Update:** The "Accounts Management" wireframe will be updated to show the status of the QuickBooks Online connection.

---

## 3. Real-Time Playbook Updates

**Feasibility:** **High**. This is a core requirement and will be achieved through a combination of the QuickBooks integration and background processing.

**Approach:**

1.  **Webhook Integration (for QuickBooks):** We will utilize QuickBooks Online Webhooks. This means that QuickBooks will proactively send a notification to our application whenever a specific event occurs (e.g., a new invoice is created, a payment is received, a bill is paid). This is more efficient than constantly polling the API for changes.
2.  **Background Job Processing:** When our application receives a webhook notification, it will trigger a background job. This job will:
    -   Fetch the updated data from QuickBooks.
    -   Update the relevant information in our application's database.
    -   Re-run the simulation for any "locked-in" playbooks that are affected by the change.
3.  **Real-time Adjustments:** This ensures that your active playbook is always current. For example:
    -   If a large, unexpected invoice is paid, the cash flow projection will be immediately updated, potentially resolving a previously forecasted overdraft.
    -   If a new, significant bill is entered, the playbook will be re-evaluated, and if a new risk is identified (e.g., a projected cash shortfall), a notification will be sent.
4.  **Manual Adjustments:** You will still have the ability to make manual adjustments to your playbooks. These manual overrides will be layered on top of the live data from QuickBooks, allowing you to create "what-if" scenarios based on the most current financial reality.

**Benefits:**
- **Proactive Financial Management:** The system doesn't just show you what happened; it shows you what's *about* to happen based on the latest data.
- **Timely Alerts:** You'll be notified of potential issues as soon as they arise, giving you more time to react.
- **Dynamic Scenarios:** Your financial forecasts will adapt to the changing conditions of your business in near real-time.

**Wireframe Update:** The data flow diagram will be updated to illustrate the webhook-based real-time updates from QuickBooks.

---

### References

[1] Google Identity. (2025, October 23). *Using OAuth 2.0 for Web Server Applications*. Google for Developers. https://developers.google.com/identity/protocols/oauth2/web-server

[2] Intuit Developer. (n.d.). *QuickBooks API*. Intuit. https://developer.intuit.com/app/developer/qbo/docs/develop


---

## Delegated Access Feature Specification

### Overview

The delegated access feature allows the primary user (Dwain) to grant limited, read-only access to specific financial data and reports to external parties, such as a tax professional or accountant. This ensures that sensitive financial information can be shared securely without compromising the user's account security.

---

### Use Case

**Primary User:** Dwain Henderson Jr. (Superior Networks LLC)

**Delegated User:** Tax Professional or Accountant

**Goal:** Allow the tax professional to view financial reports, scenarios, and account summaries without the ability to modify data or settings.

---

### Wireframe: Delegated Access Management (in Settings)

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

### Wireframe: Grant New Delegated Access Dialog

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

### Delegated User Experience

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

### Technical Implementation

#### Database Schema

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

#### Access Control Logic

1. **When a delegated user logs in:**
   - Check the `delegated_access` table for active delegations.
   - If found, display the owner's data with the appropriate restrictions.

2. **Permission Checks:**
   - Before rendering any page, check if the current user is a delegated user.
   - If yes, enforce read-only restrictions (disable edit/delete buttons, prevent API calls for modifications).

3. **Audit Logging:**
   - Log all actions taken by delegated users for security and compliance.

---

#### Security Considerations

1. **Expiration:** All delegated access must have an expiration date.
2. **Revocation:** The primary user can revoke access at any time.
3. **Scope Limitation:** Delegated users can only see what the primary user explicitly grants.
4. **No Cascading:** Delegated users cannot grant access to others.
5. **Audit Trail:** All delegated user actions are logged.

---

### User Stories

1. **As a primary user (Dwain), I want to grant my tax professional read-only access to my financial reports so they can prepare my taxes without needing to log into my account.**

2. **As a tax professional, I want to view my client's financial data in a secure, read-only environment so I can provide accurate tax advice without the risk of accidentally modifying their data.**

3. **As a primary user, I want to revoke delegated access at any time so I can control who has visibility into my financial information.**

4. **As a primary user, I want to set an expiration date for delegated access so I don't have to remember to manually revoke it after tax season.**

---

### Future Enhancements

- **Multiple Delegation Levels:** Add more granular permission levels (e.g., "View Only Summaries", "Full Read Access", "Read + Comment").
- **Delegation Notifications:** Notify the primary user when a delegated user logs in or views specific reports.
- **Delegation Activity Log:** Show the primary user a log of what the delegated user has viewed.
- **Delegation Templates:** Create reusable delegation templates for common use cases (e.g., "Tax Professional", "Business Partner").

---

This feature ensures that Dwain can securely share financial information with his tax professional while maintaining full control over his data and account security.


---

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


---

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


---

# Enhanced Synchronization Controls Specification

## 1. Overview

To provide users with greater control over data freshness and system performance, this specification outlines a set of enhanced synchronization controls for the QuickBooks Online integration. These features will allow for automatic syncing upon login, manual on-demand syncing, and user-configurable background sync frequencies.

---

## 2. Feature Breakdown & Wireframe Updates

### a. Automatic Sync on Login

- **Description:** The system will automatically initiate a data synchronization with QuickBooks Online immediately after a user successfully logs in. This ensures that the user is always greeted with the most up-to-date financial data.
- **Implementation:** A backend job will be triggered post-authentication to run the sync process in the background.

### b. Manual Sync Control & Status Display

- **Description:** The "Accounts Management" page will be updated to display the timestamp of the last successful synchronization and a button to trigger a manual sync at any time.
- **Wireframe Update (Accounts Management Page):**

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  CONNECTED ACCOUNTS                                                    │
│                                                                         │
│  INTEGRATIONS                                                          │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ QuickBooks Online: Connected ✓                             │        │
│  │ Last Synced: 15 minutes ago      [ Sync Now ]               │        │
│  │ [Configure] [Disconnect]                                   │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
... (rest of the page) ...
└─────────────────────────────────────────────────────────────────────────┘
```

### c. Configurable Background Sync Frequency

- **Description:** The "Settings" page will include a new section allowing the user to choose how often the system automatically syncs with QuickBooks in the background. This allows users to balance the need for real-time data with potential API rate limits from Intuit.
- **Wireframe Update (Settings & Notifications Page):**

```
┌─────────────────────────────────────────────────────────────────────────┐
│ [LOGO]  Financial Playbook    [Dashboard][Accounts][Scenarios][Reports] │
│                                                      [User: Dwain] [Logout]│
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  USER SETTINGS                                                         │
│                                                                         │
... (Profile, Notifications, etc.) ...
│                                                                         │
│  SYNCHRONIZATION SETTINGS                                              │
│  ┌───────────────────────────────────────────────────────────┐        │
│  │ Automatic Background Sync Frequency:                       │        │
│  │                                                            │        │
│  │   [ Every Hour ▼]                                          │        │
│  │   (Options: Every Hour, Every 4 Hours, Every 8 Hours, Daily) │        │
│  │                                                            │        │
│  │ [Save Sync Settings]                                       │        │
│  └───────────────────────────────────────────────────────────┘        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Technical Implementation

- **Database Update:** The `users` table (or a new `user_settings` table) will be updated to include a `sync_frequency` column to store the user's preference (e.g., 1, 4, 8, 24 hours).

- **Backend Scheduler:** A cron job scheduler will be used on the backend. When a user updates their sync frequency, the system will update the schedule for that user's background sync job.

- **Sync Process:**
    1.  **Trigger:** The sync process can be triggered in three ways: on-login, manually via the "Sync Now" button, or by the scheduled background job.
    2.  **Execution:** The backend will initiate the QuickBooks API data fetch.
    3.  **Status Update:** The UI will update the "Last Synced" timestamp upon successful completion. If the user triggers a manual sync, the "Sync Now" button should show a "Syncing..." state and become disabled until the process is complete.

---

## 4. Benefits

- **User Control:** Empowers the user to decide how frequently their data is updated, balancing real-time needs with system efficiency.
- **Improved Data Freshness:** The combination of sync-on-login and background syncs ensures data is rarely stale.
- **Transparency:** The "Last Synced" status provides clear visibility into the data's timeliness.
- **Flexibility:** The manual "Sync Now" button provides an immediate way to pull in the very latest data before making a critical decision or running a new scenario.


---

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


---

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
