# Financial Playbook - Development TODO

## Phase 1: Project Setup & Basic Authentication ✓
- [x] Initialize Next.js project with TypeScript and Tailwind CSS
- [x] Set up PostgreSQL database and Drizzle ORM
- [x] Create GitHub repository
- [ ] Implement Google OAuth 2.0 authentication
- [ ] Create user registration and login flows
- [ ] Build basic user profile page
- [ ] Implement HTTPS and security headers (CSP, HSTS)
- [ ] Set up development mode flag for UI QC numbers

## Phase 2: QuickBooks Integration & Financial Data Engine
- [ ] Extend database schema for accounts, transactions, bills
- [ ] Create quickbooks_connections table with encrypted tokens
- [ ] Implement QuickBooks OAuth 2.0 connection flow
- [ ] Build QuickBooks data sync service
- [ ] Implement QuickBooks webhook receiver for real-time updates
- [ ] Build Accounts Management UI with connection status
- [ ] Add "Last Synced" timestamp and "Sync Now" button
- [ ] Implement configurable sync frequency in Settings
- [ ] Implement automatic sync on login
- [ ] Build Dashboard with account summaries and quick stats

## Phase 3: AI Strategy Builder with Math Validation
- [ ] Extend database schema for uploaded_documents, scenarios
- [ ] Build Strategy Builder Wizard UI (3-step process)
- [ ] Implement file upload interface with drag-and-drop
- [ ] Implement document processing pipeline (OCR, text extraction)
- [ ] Build AI-powered data extraction service
- [ ] **Build separate validation service for AI math verification**
- [ ] Implement transaction categorization
- [ ] Implement recurring bill identification
- [ ] Build AI-powered strategy recommendation engine
- [ ] Add discrepancy flagging UI for failed validations

## Phase 4: Logic Simulator & Validated Report Generator
- [ ] Extend database schema for simulation_results
- [ ] Build Scenario Logic Editor UI with visual rule builder
- [ ] Implement condition and action definition system
- [ ] Build day-by-day simulation engine
- [ ] Implement event processing (income, bills, user-defined rules)
- [ ] Implement risk flagging system
- [ ] Build Report Generator with AI analysis
- [ ] **Implement AI Math Validation for all report calculations**
- [ ] Build AI-powered root cause analysis
- [ ] Build AI-generated solution recommendations
- [ ] Implement report assembly (Executive Summary, Running Balances, etc.)
- [ ] Build chart generation for reports
- [ ] Implement report export (PDF, Word, Markdown, CSV)

## Phase 5: Automation, Audit Trail & Final UI
- [ ] Extend database schema for audit_logs
- [ ] Update bills/transactions tables with automation fields
- [ ] Build simplified automation system for recurring bills
- [ ] Implement price variance alerts (default 3%)
- [ ] Build Automation Settings UI modal
- [ ] Implement notification engine for email alerts
- [ ] Build Notification Settings UI in Settings page
- [ ] Implement audit trail logging middleware
- [ ] Build Audit Trail Report UI with filters
- [ ] Implement CSV export for audit logs
- [ ] Complete all UI pages with QC numbering system
- [ ] Assign unique 3-digit QC numbers to all UI elements
- [ ] Implement development mode toggle for QC visibility
- [ ] Ensure responsive design across all devices
- [ ] Implement comprehensive error handling
- [ ] Add loading states for all async operations
- [ ] Conduct accessibility audit

## Phase 6: Security Review, Testing & Deployment
- [ ] Conduct comprehensive security audit
- [ ] Test for SQL injection vulnerabilities
- [ ] Test for XSS vulnerabilities
- [ ] Verify all API endpoints are protected
- [ ] Test rate limiting
- [ ] Review all environment variable usage
- [ ] Set up production environment on Vercel
- [ ] Configure environment variables in Vercel
- [ ] Set up PostgreSQL production database
- [ ] Configure custom domain (if applicable)
- [ ] Set up GitHub Actions workflow for automated testing
- [ ] Configure automatic deployment to Vercel
- [ ] Implement Vercel Analytics
- [ ] Set up Sentry for error tracking
- [ ] Create user documentation
- [ ] Create admin guide
- [ ] Create troubleshooting guide
- [ ] Conduct final user acceptance testing
- [ ] Create mechanism to remove QC numbers for production
- [ ] Deploy to production
- [ ] Conduct handover session

## Future Phase: Multi-User Expansion (Deferred)
- [ ] Implement row-level security in database
- [ ] Build user management system
- [ ] Implement delegated access for tax professionals
- [ ] Build delegate profile creation with permissions
- [ ] Implement AI delegation system for task assignment
- [ ] Build permission enforcement (API and UI level)
- [ ] Implement delegated user invitation flow
- [ ] Build multi-user audit trail

## Bugs & Issues
(Track bugs here as they are discovered)

## Notes
- All AI-generated calculations must be validated with traditional programming methods
- Single-user architecture for initial release
- Multi-user features deferred to future phase
- QC numbering system for easy UI element reference
- All code pushed to GitHub: https://github.com/SuperiorNetworks/financial-playbook


## Documentation Updates
- [x] Add QC numbers to all wireframes in complete documentation


## Design Clarifications
- [x] Update wireframes: Remove edit/delete buttons from QuickBooks-sourced data (accounts, transactions, bills, invoices are READ-ONLY)
- [x] Add "View in QuickBooks" links for all QuickBooks data instead of edit buttons
- [x] Clarify that only user-created scenarios and rules are editable

## External Connectors & Integrations
- [ ] QuickBooks Online API integration (OAuth 2.0)
- [ ] Google OAuth for user authentication
- [ ] Email service integration for notifications (SendGrid, AWS SES, or similar)
- [ ] AI/LLM API integration (OpenAI GPT-4 or Grok) for document analysis
- [ ] S3 or cloud storage for uploaded documents
- [ ] Future: Plaid API for additional bank connections (if needed beyond QuickBooks)
- [ ] Future: Stripe API for payment processing (if monetizing)


## Visual Status System (Traffic Light Design Language)
- [ ] Design and implement global status indicator system
- [ ] GREEN status: QuickBooks and Playbook are in sync, no issues
- [ ] YELLOW status: Warning - variance detected, sync issue, or duplicate found
- [ ] RED status: Critical - upcoming activity not in QuickBooks, expected payment missing from register
- [ ] Implement visual halo/background effect for status indicators
- [ ] Add info icon (ℹ️) next to all status indicators
- [ ] Build tooltip/modal system for "More Info" explanations
- [ ] Create status explanation templates for common scenarios
- [ ] Apply status system consistently across all pages (Dashboard, Accounts, Scenarios, Reports)
- [ ] Add status indicators to: account balances, bills, transactions, scenario items, playbook activities
- [ ] Implement real-time status updates when sync occurs

## Status Logic Rules
- [ ] GREEN: QuickBooks transaction matches playbook expectation within tolerance
- [ ] YELLOW: Price variance exceeds threshold (default 3%), sync delayed >24 hours, duplicate detected
- [ ] RED: Expected activity within 5 days not found in QuickBooks, expected payment within 3 days missing from register
- [ ] Build configurable thresholds for status transitions in Settings

## Google Calendar Integration
- [ ] Add Google Calendar API connector (OAuth 2.0)
- [ ] Build Calendar view page showing upcoming activities and tasks
- [ ] Sync playbook activities to Google Calendar
- [ ] Sync delegated tasks to Google Calendar
- [ ] Display upcoming bills as calendar events
- [ ] Display expected payments as calendar events
- [ ] Add two-way sync: changes in Calendar reflect in Playbook
- [ ] Implement calendar event creation from within Playbook
- [ ] Add calendar reminders for critical activities (RED status items)
- [ ] Build calendar filtering by category (bills, income, tasks, delegations)

- [ ] Google Calendar API integration (OAuth 2.0) for task and activity management


## Customizable Dashboard Layout System
- [ ] Implement drag-and-drop grid system for dashboard widgets
- [ ] Allow users to resize widgets (stretch/shrink)
- [ ] Allow users to reposition widgets on the dashboard
- [ ] Implement widget library/catalog for adding new modules
- [ ] Build layout persistence (save user's custom layout to database)
- [ ] Add "Reset to Default Layout" option
- [ ] Add "Lock Layout" toggle to prevent accidental changes
- [ ] Implement responsive behavior (layout adapts on mobile/tablet)
- [ ] Build widget configuration panel (show/hide specific widgets)
- [ ] Add visual grid guides during drag operations
- [ ] Implement snap-to-grid functionality
- [ ] Add undo/redo for layout changes
- [ ] Build widget templates/presets (e.g., "Executive View", "Detailed Analysis")

## Available Dashboard Widgets
- [ ] Active Alerts widget (resizable, repositionable)
- [ ] Cash Flow Chart widget (resizable, repositionable)
- [ ] Quick Stats widget (resizable, repositionable)
- [ ] Upcoming Bills widget (resizable, repositionable)
- [ ] Account Balances widget (resizable, repositionable)
- [ ] Recent Activity widget (resizable, repositionable)
- [ ] Scenario Status widget (resizable, repositionable)
- [ ] Calendar Preview widget (resizable, repositionable)
- [ ] QuickBooks Sync Status widget (resizable, repositionable)


## Feature Request System (Feedback Portal)
- [ ] Design and build Feature Request submission page
- [ ] Create database schema for feature_requests table
- [ ] Implement feature request submission form
- [ ] Add feature request voting system (upvote/downvote)
- [ ] Build feature request list/board view
- [ ] Implement status tracking (Submitted, Under Review, Planned, In Progress, Completed, Declined)
- [ ] Add commenting system for feature requests
- [ ] Build admin panel for managing feature requests
- [ ] Implement email notifications when feature status changes
- [ ] Add filtering by status and category
- [ ] Add search functionality for feature requests
- [ ] Build public roadmap view showing planned features
- [ ] Implement "My Requests" view for users to track their submissions
- [ ] Add request merging (combine duplicate requests)
- [ ] Build analytics dashboard for feature request trends

- [x] Rebuild master playbook incorporating UI implementation plan with designer assignments

- [x] Update TODAYS_ADDITIONS_SUMMARY to include UI design decisions (Octet, Ran Liu, Ana Vadillo, Fuselab, Lazarev)
- [x] Integrate FINAL_UI_IMPLEMENTATION_PLAN into MASTER_PLAYBOOK_COMPLETE


## Integrated Onboarding System v2.0 (Tiered with Bank Statement Control)

### Core Onboarding Infrastructure
- [ ] Design and implement initial branching question UI ("How organized are your financial records?")
- [ ] Build 4-path routing system (Fast Track, Guided Cleanup, Manual Entry, Simplified)
- [ ] Create progress tracking system with visual indicators (0-100%)
- [ ] Implement skip/resume functionality with state persistence
- [ ] Build onboarding completion analytics and metrics tracking
- [ ] Design celebration/milestone screens for each completion point
- [ ] Implement positive affirmation messaging system throughout onboarding

### Bank Statement Processing Engine (Universal Requirement)
- [ ] Build AI-powered OCR system for bank statement extraction (PDF, JPG, PNG, HEIC)
- [ ] Implement transaction parsing and categorization from bank statements
- [ ] Build math validation system (beginning + deposits - withdrawals = ending)
- [ ] Create 3-month statement collection UI with drag-and-drop upload
- [ ] Implement statement quality checks and validation error handling
- [ ] Build transaction matching engine (bank statements vs QuickBooks)
- [ ] Create discrepancy detection and reporting system
- [ ] Implement pattern recognition for recurring transactions
- [ ] Build seasonal trend detection from 3-month baseline
- [ ] Create anomaly detection system based on bank statement patterns

### Path A: Fast Track (QB Managed)
- [ ] Build QuickBooks OAuth connection flow UI
- [ ] Implement automatic data extraction from QuickBooks
- [ ] Create bank statement verification UI for QB users
- [ ] Build discrepancy report for QB vs bank statement comparison
- [ ] Implement business profile confirmation screen (auto-populated from QB)
- [ ] Create 5-minute onboarding flow for organized users
- [ ] Build "96.8% accurate" success messaging

### Path B: Guided Cleanup (QB But Behind)
- [ ] Build encouraging messaging for users with QB issues
- [ ] Create guided discrepancy resolution UI (one-by-one walkthrough)
- [ ] Implement AI-assisted transaction categorization suggestions
- [ ] Build "Add to QuickBooks" one-click action buttons
- [ ] Create progress tracking for cleanup (X of Y discrepancies resolved)
- [ ] Implement before/after comparison display
- [ ] Build 15-20 minute cleanup flow with milestone celebrations

### Path C: Manual Entry (Chaos/Need Help)
- [ ] Build empathetic encouragement messaging for overwhelmed users
- [ ] Create account entry UI with live cash position updates
- [ ] Implement immediate value display (30 seconds to first insight)
- [ ] Build debt entry UI with net position calculation
- [ ] Create AI-powered income/expense detection from bank statements
- [ ] Implement recurring transaction confirmation UI
- [ ] Build comprehensive business profile questionnaire (8-10 questions)
- [ ] Create 20-25 minute "chaos to clarity" flow

### Path D: Simplified (New Business)
- [ ] Build new business encouragement messaging
- [ ] Create simplified account entry flow
- [ ] Implement optional bank statement upload (1-2 months acceptable)
- [ ] Build expected income/expense entry UI
- [ ] Create forward-looking projection system for new businesses
- [ ] Implement 10-15 minute simplified onboarding flow

### Business Profile System Integration
- [ ] Create database schema for 7-pillar business profile system
- [ ] Build business identity collection UI (name, entity type, industry, etc.)
- [ ] Implement money flow mapping UI (revenue sources, expense categories)
- [ ] Create organizational structure questionnaire (bookkeeper, decision authority)
- [ ] Build revenue model collection UI (pricing, payment terms, seasonality)
- [ ] Implement expense framework UI (fixed vs variable costs)
- [ ] Create strategic goals collection UI (debt reduction, growth targets, etc.)
- [ ] Build financial statement generation from available data
- [ ] Implement progressive disclosure system (collect data over time, not all at once)

### Forensic Analysis System
- [ ] Build 8-module forensic analysis engine
- [ ] Implement pattern recognition module (recurring transactions, seasonal trends)
- [ ] Create anomaly detection module (unusual transactions, outliers)
- [ ] Build efficiency analysis module (money leaks, unnecessary fees)
- [ ] Implement fraud detection module (suspicious activity flagging)
- [ ] Create vendor intelligence module (payment patterns, consolidation opportunities)
- [ ] Build cash flow forensics module (timing issues, float optimization)
- [ ] Implement seasonal intelligence module (peak/trough detection)
- [ ] Create predictive insights module (forecast based on patterns)
- [ ] Build forensic analysis report UI with actionable recommendations

### Dashboard & Post-Onboarding Experience
- [ ] Build immediate dashboard display after onboarding completion
- [ ] Create financial snapshot widget (cash, debt, net position, traffic lights)
- [ ] Implement 90-day cash flow forecast display
- [ ] Build forensic analysis summary card
- [ ] Create recommended actions prioritized list (High/Medium/Low)
- [ ] Implement scenario planning quick-start UI
- [ ] Build monthly re-analysis notification system
- [ ] Create continuous improvement tracking (forecast accuracy over time)

### Data Quality & Validation
- [ ] Implement statement-level validation checks
- [ ] Build transaction-level quality checks
- [ ] Create user feedback system for validation errors
- [ ] Implement confidence scoring for AI-extracted data
- [ ] Build manual override system for incorrect AI extractions

### Onboarding Analytics & Optimization
- [ ] Track completion rates by path (A/B/C/D)
- [ ] Measure time to first value by path
- [ ] Implement user confidence scoring (post-onboarding survey)
- [ ] Build onboarding funnel analytics (drop-off points)
- [ ] Create A/B testing framework for onboarding messaging
- [ ] Implement onboarding performance dashboard for product team
