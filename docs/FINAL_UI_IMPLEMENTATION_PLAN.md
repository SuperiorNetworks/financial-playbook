# Financial Playbook - Final UI Implementation Plan

**Date:** November 24, 2025  
**Purpose:** Definitive UI design reference selections with specific element assignments  
**Confidence Level:** 90-95% implementation success

---

## 🎯 My Final Designer Selections

After analyzing both lists and my capabilities, here are the **4 designers/agencies** I will use as primary references:

### Primary Foundation (95% confidence)
1. **Octet** - Design system architecture and component consistency
2. **Ran Liu** - Clean hierarchy and layout structure

### Financial Specifics (90% confidence)
3. **Ana Vadillo** - Financial data tables and dense information display

### Dashboard & Visualization (88% confidence)
4. **Fuselab Creative** - Customizable dashboard and data visualization

### Polish Layer (selective, 92% confidence)
5. **Lazarev** - Professional fintech aesthetic and empty states

---

## 📐 UI Element Breakdown by Designer

Here's exactly which designer I'll reference for each specific UI element in Financial Playbook:

---

### 🔐 Login & Authentication Page [QC: 101-109]

**Primary Reference:** Lazarev  
**Secondary Reference:** Ran Liu

**Why:**
- Lazarev: Professional fintech credibility, clean onboarding flows
- Ran Liu: Simple, uncluttered layout

**Specific Elements:**
- [101] Logo placement → Lazarev (centered, prominent)
- [102] "Sign in with Google" button → Lazarev (large, clear CTA)
- [103] Welcome message → Ran Liu (clean typography, minimal)
- [104] Background → Lazarev (subtle gradient or solid professional color)
- [105] Footer links → Ran Liu (simple, understated)

**Implementation:**
- Clean, centered layout
- Single prominent CTA button
- Minimal distractions
- Professional color palette (blues/grays)
- Simple fade-in animation

---

### 🧭 Global Navigation & Header [QC: 201-208]

**Primary Reference:** Octet  
**Secondary Reference:** Ran Liu

**Why:**
- Octet: Consistent navigation patterns across complex apps
- Ran Liu: Clean, system-like layout grids

**Specific Elements:**
- [201] App logo → Octet (consistent placement, clickable home)
- [202] Main navigation menu → Octet (clear hierarchy, consistent spacing)
- [203] User profile dropdown → Octet (standard pattern, accessible)
- [204] Notifications bell → Octet (badge for count, dropdown)
- [205] QuickBooks sync status → **Ana Vadillo** (financial data indicator)
- [206] Last synced timestamp → Ana Vadillo (subtle, informative)
- [207] Search bar → Ran Liu (clean, minimal, expandable)
- [208] Settings gear icon → Octet (standard placement)

**Implementation:**
- Persistent top navigation bar
- Left: Logo + main nav items
- Right: Search, notifications, sync status, profile
- Sticky on scroll
- Consistent across all pages
- shadcn/ui Navigation Menu component

---

### 📊 Dashboard (Customizable) [QC: 209-220]

**Primary Reference:** Fuselab Creative  
**Secondary Reference:** Ran Liu

**Why:**
- Fuselab: Dashboard and widget specialization
- Ran Liu: Clean hierarchy (one primary chart per view)

**Specific Elements:**
- [209] Dashboard title → Ran Liu (clear, prominent)
- [210] "Customize Layout" button → Fuselab (widget management)
- [211] Widget grid container → Fuselab (drag-and-drop grid)
- [212] Active Alerts widget → **Ana Vadillo** (financial alerts with severity)
- [213] Cash Flow Chart widget → Fuselab (primary chart, prominent)
- [214] Quick Stats widget → Ran Liu (clean cards with numbers)
- [215] Upcoming Bills widget → Ana Vadillo (financial table, compact)
- [216] Account Balances widget → Ana Vadillo (financial data, clear hierarchy)
- [217] Recent Activity widget → Ana Vadillo (transaction list, scannable)
- [218] Scenario Status widget → Ran Liu (status cards, simple)
- [219] Calendar Preview widget → Fuselab (compact calendar with events)
- [220] QuickBooks Sync Status widget → Ana Vadillo (sync indicator with details)

**Implementation:**
- React Grid Layout for drag-and-drop
- 12-column responsive grid
- Each widget = Card component from shadcn/ui
- Resize handles on widgets
- "Lock Layout" toggle
- Layout persistence in database
- Mobile: Stacks vertically

**Visual Status System (Traffic Light):**
- 🟢 GREEN glow → Subtle box-shadow with green hue
- 🟡 YELLOW glow → Box-shadow with yellow/amber hue + warning icon
- 🔴 RED glow → Box-shadow with red hue + alert icon + optional pulse
- Info bubble (ℹ️) → Tooltip on hover, modal on click

---

### 💰 Accounts Management Page [QC: 301-329]

**Primary Reference:** Ana Vadillo  
**Secondary Reference:** Ran Liu

**Why:**
- Ana Vadillo: Financial data tables, dense information, clear hierarchy
- Ran Liu: Clean layout structure

**Specific Elements:**

**Header Section:**
- [301] Page title "Accounts" → Ran Liu (clear hierarchy)
- [302] "Sync Now" button → Ana Vadillo (financial action, prominent)
- [303] Last synced timestamp → Ana Vadillo (subtle, informative)
- [304] Filter dropdown → Ana Vadillo (financial data filtering)

**Bank Accounts Section:**
- [305] Section title "Bank Accounts" → Ran Liu (clear section break)
- [306] Account list table → **Ana Vadillo** (finance-grade table)
  - [307] Account name column → Ana Vadillo (bold, primary)
  - [308] Account type column → Ana Vadillo (secondary info)
  - [309] Current balance column → Ana Vadillo (prominent, right-aligned)
  - [310] Status indicator → **Custom** (traffic light glow)
  - [311] "View in QuickBooks" link → Ana Vadillo (external link pattern)

**Bills Section:**
- [312] Section title "Bills" → Ran Liu
- [313] Bills table → Ana Vadillo
  - [314] Bill name column → Ana Vadillo
  - [315] Vendor column → Ana Vadillo
  - [316] Amount column → Ana Vadillo (right-aligned, bold)
  - [317] Due date column → Ana Vadillo (date formatting)
  - [318] Status indicator → Custom (traffic light)
  - [319] "View in QuickBooks" link → Ana Vadillo

**Accounts Receivable Section:**
- [320] Section title "Accounts Receivable" → Ran Liu
- [321] AR table → Ana Vadillo
  - [322] Invoice number → Ana Vadillo
  - [323] Customer → Ana Vadillo
  - [324] Amount → Ana Vadillo
  - [325] Due date → Ana Vadillo
  - [326] Status → Custom (traffic light)
  - [327] "View in QuickBooks" link → Ana Vadillo

**Empty States:**
- [328] No accounts message → **Lazarev** (friendly empty state)
- [329] "Connect QuickBooks" CTA → Lazarev (clear action)

**Implementation:**
- shadcn/ui Table component
- Sortable columns
- Filter by status (green/yellow/red)
- Search functionality
- Responsive: Cards on mobile
- Read-only (no edit/delete buttons)
- "View in QuickBooks" opens new tab

---

### 🎯 Scenario Planning Page [QC: 401-425]

**Primary Reference:** Ran Liu  
**Secondary Reference:** Lazarev

**Why:**
- Ran Liu: Clean hierarchy for complex workflows
- Lazarev: Scenario management patterns from their SaaS work

**Specific Elements:**

**Header:**
- [401] Page title "Scenario Planning" → Ran Liu
- [402] "Create New Scenario" button → Lazarev (primary CTA)
- [403] View toggle (Grid/List) → Ran Liu (simple toggle)

**Scenario Cards:**
- [404] Scenario card container → Lazarev (card-based layout)
  - [405] Scenario name → Ran Liu (bold, clear)
  - [406] Status badge (Active/Draft/Locked) → Octet (consistent badges)
  - [407] Created date → Ran Liu (subtle metadata)
  - [408] Quick stats (Cash flow, Risk level) → Ran Liu (compact metrics)
  - [409] Status indicator → Custom (traffic light glow on card border)
  - [410] "Edit" button → Octet (secondary action)
  - [411] "View Report" button → Octet (primary action)
  - [412] "Lock Scenario" toggle → Octet (toggle switch)
  - [413] "Duplicate" button → Octet (tertiary action)
  - [414] "Delete" button → Octet (destructive action, confirm modal)

**Comparison View:**
- [415] "Compare Scenarios" button → Lazarev
- [416] Scenario selector (multi-select) → Octet
- [417] Side-by-side comparison table → **Ana Vadillo** (financial comparison)
  - [418] Metric rows → Ana Vadillo
  - [419] Scenario columns → Ana Vadillo
  - [420] Difference indicators → Custom (green/red delta)

**Empty State:**
- [421] No scenarios message → Lazarev
- [422] "Start with AI Strategy Builder" CTA → Lazarev

**Filters:**
- [423] Filter by status → Octet
- [424] Sort by (Date, Name, Risk) → Octet
- [425] Search scenarios → Ran Liu

**Implementation:**
- Card grid layout (3 columns desktop, 1 mobile)
- shadcn/ui Card, Badge, Button components
- Comparison view = shadcn/ui Table
- Delete confirmation = shadcn/ui Alert Dialog
- Drag to reorder (optional)

---

### 🔧 Scenario Editor / Logic Builder [QC: 501-526]

**Primary Reference:** Octet  
**Secondary Reference:** Ran Liu

**Why:**
- Octet: Complex flows, interaction patterns
- Ran Liu: Clean hierarchy for dense interfaces

**Specific Elements:**

**Header:**
- [501] Scenario name (editable) → Octet (inline edit)
- [502] Save button → Octet (primary action)
- [503] "Back to Scenarios" link → Octet (breadcrumb)
- [504] Status badge → Octet

**Left Sidebar (Inputs):**
- [505] "Starting Conditions" section → Ran Liu (clear section)
  - [506] Account balances (from QuickBooks) → Ana Vadillo (read-only, financial)
  - [507] Date range selector → Octet (date picker)
  - [508] "Refresh from QuickBooks" button → Ana Vadillo

**Center Panel (Logic Rules):**
- [509] "Business Rules" section → Octet
  - [510] Rule list → Octet (sortable, draggable)
  - [511] "Add Rule" button → Octet
  - [512] Rule card → Octet
    - [513] IF condition dropdown → Octet (select)
    - [514] Comparison operator → Octet (select: <, >, =, etc.)
    - [515] Value input → Octet (number/text input)
    - [516] THEN action dropdown → Octet (select)
    - [517] Action details → Octet (conditional inputs)
    - [518] "Delete Rule" button → Octet (icon button)
    - [519] Status indicator → Custom (validation: green = valid, red = error)

**Right Sidebar (Preview):**
- [520] "Cash Flow Preview" section → Fuselab
  - [521] Mini chart → Fuselab (line chart, simplified)
  - [522] Risk indicators → Custom (traffic light badges)
  - [523] "Run Full Simulation" button → Lazarev (CTA)

**Bottom Panel (Timeline):**
- [524] "Event Timeline" → Fuselab (horizontal timeline)
  - [525] Event markers → Fuselab (dots on timeline)
  - [526] Event details on hover → Fuselab (tooltip)

**Implementation:**
- Three-column layout (sidebar-main-sidebar)
- Rule builder = Form with shadcn/ui Select, Input components
- Drag-and-drop rules with react-beautiful-dnd
- Real-time validation
- Preview chart = Chart.js line chart
- Timeline = custom component with CSS

---

### 🤖 AI Strategy Builder Wizard [QC: 601-651]

**Primary Reference:** Lazarev  
**Secondary Reference:** Octet

**Why:**
- Lazarev: Onboarding flows, wizard patterns
- Octet: Form patterns, multi-step flows

**Specific Elements:**

**Step 1: Upload Documents [601-610]:**
- [601] Wizard progress indicator → Lazarev (step dots)
- [602] Step title "Upload Financial Documents" → Lazarev
- [603] Step description → Lazarev (helpful copy)
- [604] File upload dropzone → Octet (drag-and-drop area)
- [605] File list → Octet (uploaded files with remove button)
- [606] Supported formats note → Ran Liu (subtle helper text)
- [607] "Next" button → Lazarev (primary CTA)
- [608] "Cancel" button → Octet (secondary)
- [609] Upload progress bar → Octet (linear progress)
- [610] Error message → Octet (alert component)

**Step 2: AI Analysis [611-620]:**
- [611] Step title "Analyzing Documents" → Lazarev
- [612] Loading animation → Lazarev (spinner or skeleton)
- [613] Progress text "Extracting transactions..." → Lazarev
- [614] Analysis results card → Ran Liu (clean summary)
  - [615] Detected income → Ana Vadillo (financial metric)
  - [616] Detected expenses → Ana Vadillo
  - [617] Average monthly cash flow → Ana Vadillo
  - [618] Number of transactions → Ana Vadillo
- [619] "Looks good" button → Lazarev
- [620] "Re-analyze" button → Octet (secondary)

**Step 3: Verification [621-635]:**
- [621] Step title "Verify Extracted Data" → Lazarev
- [622] Verification table → **Ana Vadillo** (financial data table)
  - [623] Transaction date → Ana Vadillo
  - [624] Description → Ana Vadillo
  - [625] Amount → Ana Vadillo (bold, right-aligned)
  - [626] Category → Ana Vadillo
  - [627] Confidence score → Custom (green/yellow/red indicator)
  - [628] Edit icon → Octet (inline edit)
- [629] "Approve All" button → Lazarev
- [630] "Edit Selected" button → Octet
- [631] Filter by confidence → Octet
- [632] Search transactions → Ran Liu
- [633] Pagination → Octet
- [634] "Next" button → Lazarev
- [635] "Back" button → Octet

**Step 4: AI Recommendations [636-645]:**
- [636] Step title "Recommended Strategies" → Lazarev
- [637] Recommendation cards → Lazarev (card-based selection)
  - [638] Strategy name → Lazarev (bold, clear)
  - [639] Strategy description → Lazarev (concise copy)
  - [640] Key benefits list → Lazarev (bullet points)
  - [641] Risk level badge → Custom (green/yellow/red)
  - [642] "Select This Strategy" radio → Octet
- [643] "Create Scenario" button → Lazarev (primary CTA)
- [644] "Customize" button → Octet (secondary)
- [645] "Back" button → Octet

**Step 5: Completion [646-651]:**
- [646] Success icon → Lazarev (checkmark animation)
- [647] Success message → Lazarev (celebratory copy)
- [648] Scenario summary → Ran Liu (clean card)
- [649] "View Scenario" button → Lazarev (primary CTA)
- [650] "Create Another" button → Octet (secondary)
- [651] "Go to Dashboard" link → Octet (tertiary)

**Implementation:**
- Multi-step wizard with shadcn/ui Stepper pattern
- File upload with react-dropzone
- AI analysis with loading states
- Table with shadcn/ui Table component
- Cards with shadcn/ui Card component
- Form validation with Zod
- Success animation with simple CSS

---

### 📈 Playbook Report View [QC: 701-744]

**Primary Reference:** Ana Vadillo  
**Secondary Reference:** Fuselab Creative

**Why:**
- Ana Vadillo: Financial reporting, dense data display
- Fuselab: Data visualization, charts

**Specific Elements:**

**Header:**
- [701] Report title → Ran Liu (clear, prominent)
- [702] Scenario name → Ran Liu (subtitle)
- [703] Date range → Ran Liu (metadata)
- [704] "Export PDF" button → Octet (secondary action)
- [705] "Share" button → Octet (secondary action)
- [706] "Back to Scenarios" link → Octet (breadcrumb)

**Executive Summary Section:**
- [707] Section title "Executive Summary" → Ran Liu
- [708] Summary cards → Ran Liu (metric cards)
  - [709] Starting cash → Ana Vadillo (financial metric)
  - [710] Ending cash → Ana Vadillo
  - [711] Net change → Ana Vadillo (with delta indicator)
  - [712] Risk level → Custom (traffic light badge)

**Cash Flow Chart Section:**
- [713] Section title "Cash Flow Projection" → Ran Liu
- [714] Chart container → **Fuselab** (primary visualization)
  - [715] Line chart → Fuselab (Chart.js line chart)
  - [716] Legend → Fuselab (chart legend)
  - [717] Axis labels → Fuselab (clear labeling)
  - [718] Tooltip on hover → Fuselab (data point details)
- [719] Chart controls → Fuselab (zoom, pan, reset)

**Risk Analysis Section:**
- [720] Section title "Risk Analysis" → Ran Liu
- [721] Risk table → Ana Vadillo (financial risk table)
  - [722] Risk description → Ana Vadillo
  - [723] Severity → Custom (traffic light indicator)
  - [724] Date detected → Ana Vadillo
  - [725] Recommended action → Ana Vadillo
  - [726] Status → Custom (resolved/active badge)

**Transaction Register Section:**
- [727] Section title "Detailed Register" → Ran Liu
- [728] Register table → **Ana Vadillo** (finance-grade table)
  - [729] Date → Ana Vadillo
  - [730] Description → Ana Vadillo
  - [731] Category → Ana Vadillo
  - [732] Debit → Ana Vadillo (red, right-aligned)
  - [733] Credit → Ana Vadillo (green, right-aligned)
  - [734] Balance → Ana Vadillo (bold, right-aligned)
  - [735] Source → Ana Vadillo (QuickBooks/Manual badge)
  - [736] Status → Custom (traffic light)
- [737] Filter by category → Octet
- [738] Search transactions → Ran Liu
- [739] Pagination → Octet

**AI Insights Section:**
- [740] Section title "AI Insights & Recommendations" → Lazarev
- [741] Insight cards → Lazarev (card-based layout)
  - [742] Insight text → Lazarev (readable copy)
  - [743] Confidence score → Custom (percentage with color)
  - [744] "Apply Recommendation" button → Lazarev (CTA)

**Implementation:**
- Long-form report layout
- Print-friendly CSS
- Charts with Chart.js
- Tables with shadcn/ui Table
- Export PDF with html2pdf.js or similar
- Responsive: Stacks on mobile
- Sticky table of contents sidebar (desktop)

---

### ⚙️ Settings & Notifications [QC: 801-823]

**Primary Reference:** Octet  
**Secondary Reference:** Ran Liu

**Why:**
- Octet: Settings patterns, form-heavy pages
- Ran Liu: Clean, organized layout

**Specific Elements:**

**Sidebar Navigation:**
- [801] Settings sidebar → Octet (vertical tab navigation)
  - [802] General tab → Octet
  - [803] QuickBooks Connector tab → Octet
  - [804] Notifications tab → Octet
  - [805] Audit Trail tab → Octet
  - [806] QC Numbers tab → Octet (dev mode)

**General Settings:**
- [807] Section title "General Settings" → Ran Liu
- [808] App title input → Octet (text input)
- [809] Theme toggle (Light/Dark) → Octet (switch)
- [810] Language selector → Octet (select dropdown)
- [811] "Save Changes" button → Octet (primary action)

**QuickBooks Connector:**
- [812] Section title "QuickBooks Connector" → Ran Liu
- [813] Connection status → **Ana Vadillo** (financial integration status)
- [814] "Connect QuickBooks" button → Lazarev (primary CTA if not connected)
- [815] "Disconnect" button → Octet (destructive action if connected)
- [816] Sync frequency selector → Octet (radio group: 1h, 4h, 8h, 24h)
- [817] "Sync on Login" toggle → Octet (switch)
- [818] Last synced timestamp → Ana Vadillo

**Notifications:**
- [819] Section title "Notification Settings" → Ran Liu
- [820] Notification preferences → Octet (checkbox list)
  - Email on new risk detected
  - Email on overdue task
  - Email on sync failure
  - Email on scenario completion
- [821] Overdue threshold input → Octet (number input with unit)
- [822] "Save Preferences" button → Octet

**QC Numbers (Dev Mode):**
- [823] "Show QC Numbers" toggle → Octet (switch)

**Implementation:**
- Two-column layout (sidebar + content)
- shadcn/ui Tabs for navigation
- Forms with shadcn/ui Form components
- Toggle switches with shadcn/ui Switch
- Save confirmation toast
- Validation with Zod

---

### 🔍 Audit Trail Report [QC: 901-920]

**Primary Reference:** Ana Vadillo  
**Secondary Reference:** Fuselab Creative

**Why:**
- Ana Vadillo: Dense data tables, financial logging
- Fuselab: Timeline visualization

**Specific Elements:**

**Header:**
- [901] Page title "Audit Trail" → Ran Liu
- [902] Date range filter → Octet (date range picker)
- [903] User filter → Octet (select dropdown)
- [904] Action type filter → Octet (multi-select)
- [905] "Export CSV" button → Octet (secondary action)
- [906] "Clear Filters" button → Octet (tertiary)

**Audit Log Table:**
- [907] Audit table → **Ana Vadillo** (detailed log table)
  - [908] Timestamp → Ana Vadillo (precise date/time)
  - [909] User → Ana Vadillo (name + role)
  - [910] Action → Ana Vadillo (bold, clear)
  - [911] Entity → Ana Vadillo (what was changed)
  - [912] Before value → Ana Vadillo (strikethrough if changed)
  - [913] After value → Ana Vadillo (highlighted if changed)
  - [914] IP address → Ana Vadillo (security metadata)
  - [915] "View Details" button → Octet (expands row)

**Timeline View:**
- [916] "Switch to Timeline" toggle → Octet
- [917] Timeline container → **Fuselab** (vertical timeline)
  - [918] Event markers → Fuselab (dots on timeline)
  - [919] Event cards → Fuselab (card with details)
  - [920] Time axis → Fuselab (date labels)

**Implementation:**
- shadcn/ui Table with expandable rows
- Filter bar with shadcn/ui components
- Timeline with custom CSS (vertical line + cards)
- Pagination for large datasets
- Export to CSV with papaparse or similar
- Search functionality

---

### 💡 Feature Request System [QC: 1001-1050]

**Primary Reference:** Lazarev  
**Secondary Reference:** Octet

**Why:**
- Lazarev: User engagement patterns, feedback flows
- Octet: Form patterns, voting UI

**Specific Elements:**

**Feature Request List:**
- [1001] Page title "Feature Requests" → Ran Liu
- [1002] "Submit New Request" button → Lazarev (primary CTA)
- [1003] Filter by status → Octet (tabs: All, Submitted, Planned, In Progress, Completed)
- [1004] Sort by → Octet (dropdown: Votes, Date, Status)
- [1005] Search requests → Ran Liu

**Request Cards:**
- [1006] Request card → Lazarev (card-based layout)
  - [1007] Request title → Lazarev (bold, clickable)
  - [1008] Status badge → Octet (color-coded)
  - [1009] Vote count → Octet (number with up arrow)
  - [1010] "Upvote" button → Octet (toggle button)
  - [1011] Category tag → Octet (badge)
  - [1012] Submitted by → Ran Liu (user name + date)
  - [1013] Comment count → Octet (icon + number)
  - [1014] "View Details" link → Lazarev

**Request Detail Modal:**
- [1015] Modal container → Octet (dialog)
  - [1016] Request title → Lazarev
  - [1017] Status badge → Octet
  - [1018] Full description → Lazarev (formatted text)
  - [1019] Attachments → Octet (file list)
  - [1020] Vote button → Octet (prominent)
  - [1021] Comment section → Octet (threaded comments)
  - [1022] "Add Comment" form → Octet (textarea + button)
  - [1023] "Close" button → Octet

**Submit Request Form:**
- [1024] Form modal → Octet
  - [1025] Title input → Octet (text input)
  - [1026] Description textarea → Octet (rich text)
  - [1027] Category selector → Octet (select)
  - [1028] Attachment upload → Octet (file upload)
  - [1029] "Submit Request" button → Lazarev (primary CTA)
  - [1030] "Cancel" button → Octet

**Admin Dashboard (Owner Only):**
- [1031] "Admin View" toggle → Octet
- [1032] Admin table → Ana Vadillo (detailed table)
  - [1033] Request title → Ana Vadillo
  - [1034] Votes → Ana Vadillo (sortable)
  - [1035] Status dropdown → Octet (change status)
  - [1036] Assigned to → Octet (user selector)
  - [1037] Priority → Octet (select: Low, Medium, High)
  - [1038] "Merge" button → Octet (merge duplicates)
  - [1039] "Delete" button → Octet (destructive)

**Roadmap View:**
- [1040] "View Roadmap" link → Lazarev
- [1041] Roadmap timeline → Fuselab (horizontal quarters)
  - [1042] Q1 2026 column → Fuselab
  - [1043] Q2 2026 column → Fuselab
  - [1044] Q3 2026 column → Fuselab
  - [1045] Q4 2026 column → Fuselab
  - [1046] Feature cards in columns → Lazarev (draggable)
- [1047] "Public Roadmap" toggle → Octet (show/hide from users)

**Analytics (Admin):**
- [1048] Analytics dashboard → Fuselab
  - [1049] Top requested categories chart → Fuselab (bar chart)
  - [1050] Request trend chart → Fuselab (line chart)

**Implementation:**
- Card grid layout
- shadcn/ui Dialog for modals
- shadcn/ui Form for submission
- Voting with optimistic updates
- Comments with threaded replies
- Admin table with inline editing
- Roadmap with drag-and-drop (react-beautiful-dnd)
- Charts with Chart.js

---

### 📅 Calendar View [QC: 1051-1070]

**Primary Reference:** Fuselab Creative  
**Secondary Reference:** Octet

**Why:**
- Fuselab: Calendar and timeline visualization
- Octet: Event management patterns

**Specific Elements:**

**Header:**
- [1051] Page title "Calendar" → Ran Liu
- [1052] View toggle (Month/Week/Day) → Octet (button group)
- [1053] Today button → Octet (quick navigation)
- [1054] Date navigation (prev/next) → Octet (arrow buttons)
- [1055] Current date display → Ran Liu (prominent)
- [1056] "Sync with Google Calendar" button → Lazarev (integration CTA)

**Calendar Grid:**
- [1057] Calendar container → **Fuselab** (calendar grid)
  - [1058] Day cells → Fuselab (grid cells)
  - [1059] Event markers → Fuselab (colored dots or bars)
  - [1060] Event titles → Fuselab (truncated text)
  - [1061] Status colors → Custom (green/yellow/red matching traffic light)
  - [1062] "More events" link → Fuselab (if overflow)

**Event Detail Popover:**
- [1063] Event popover → Octet (popover component)
  - [1064] Event title → Lazarev
  - [1065] Event type badge → Octet (Bill, Payment, Task, etc.)
  - [1066] Date/time → Ran Liu
  - [1067] Status indicator → Custom (traffic light)
  - [1068] Description → Lazarev
  - [1069] "View in QuickBooks" link → Ana Vadillo (if applicable)
  - [1070] "Mark Complete" button → Octet (if task)

**Implementation:**
- Calendar with react-big-calendar or custom component
- Event colors match traffic light system
- Click event to open popover
- Google Calendar two-way sync via API
- Responsive: List view on mobile
- Filter by event type

---

## 🎨 Design System Foundation

### Typography (Ran Liu + Octet)

**Font Stack:**
```css
font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

**Scale:**
- Display: 2.5rem (40px) - Page titles
- Heading 1: 2rem (32px) - Section titles
- Heading 2: 1.5rem (24px) - Subsection titles
- Heading 3: 1.25rem (20px) - Card titles
- Body: 1rem (16px) - Default text
- Small: 0.875rem (14px) - Metadata, captions
- Tiny: 0.75rem (12px) - Labels, badges

**Weights:**
- Bold (700) - Primary headings, important numbers
- Semibold (600) - Secondary headings, table headers
- Medium (500) - Buttons, labels
- Regular (400) - Body text

### Color Palette (Ana Vadillo + Ran Liu)

**Base Colors:**
```css
/* Neutrals (Ran Liu - calm palette) */
--background: 0 0% 100%;           /* White */
--foreground: 222 47% 11%;         /* Near black */
--muted: 210 40% 96%;              /* Light gray */
--muted-foreground: 215 16% 47%;   /* Medium gray */
--border: 214 32% 91%;             /* Border gray */

/* Primary (Ana Vadillo - financial blue) */
--primary: 221 83% 53%;            /* Professional blue */
--primary-foreground: 210 40% 98%; /* White text on blue */

/* Status Colors (Traffic Light System) */
--success: 142 76% 36%;            /* Green - In sync */
--warning: 38 92% 50%;             /* Amber - Warning */
--destructive: 0 84% 60%;          /* Red - Critical */

/* Financial Colors (Ana Vadillo) */
--credit: 142 76% 36%;             /* Green for income/credits */
--debit: 0 84% 60%;                /* Red for expenses/debits */
```

**Traffic Light Glows:**
```css
/* Green glow */
box-shadow: 0 0 0 3px rgba(34, 197, 94, 0.2);

/* Yellow glow */
box-shadow: 0 0 0 3px rgba(251, 191, 36, 0.3);

/* Red glow (with pulse) */
box-shadow: 0 0 0 3px rgba(239, 68, 68, 0.3);
animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
```

### Spacing (Octet + Ran Liu)

**Scale (Tailwind default):**
- 0.5 = 0.125rem (2px)
- 1 = 0.25rem (4px)
- 2 = 0.5rem (8px)
- 3 = 0.75rem (12px)
- 4 = 1rem (16px)
- 6 = 1.5rem (24px)
- 8 = 2rem (32px)
- 12 = 3rem (48px)
- 16 = 4rem (64px)

**Component Spacing:**
- Card padding: 6 (24px)
- Section spacing: 12 (48px)
- Element spacing: 4 (16px)
- Button padding: 4 horizontal, 2 vertical

### Components (shadcn/ui + Custom)

**From shadcn/ui:**
- Button (with variants: default, secondary, outline, ghost, destructive)
- Card (with header, content, footer)
- Table (with sorting, filtering)
- Form (with validation)
- Dialog / Modal
- Dropdown Menu
- Select
- Input
- Textarea
- Switch / Toggle
- Badge
- Alert
- Tooltip
- Tabs
- Popover
- Sheet (sidebar)

**Custom Components:**
- Traffic Light Status Indicator
- Widget Container (for dashboard)
- Chart Wrapper (for data viz)
- Timeline Component
- Calendar Component
- File Upload Dropzone

---

## 🔄 UI Flow Summary

### User Journey with Designer References

**1. Login (Lazarev)**
- Clean, professional entry point
- Single Google OAuth button
- Minimal distractions

**2. Dashboard (Fuselab + Ran Liu)**
- Customizable widget grid
- One primary chart (cash flow)
- Traffic light status indicators throughout
- Quick access to all features

**3. Accounts Management (Ana Vadillo)**
- Finance-grade tables
- Clear hierarchy
- Read-only QuickBooks data
- "View in QuickBooks" links

**4. Scenario Planning (Ran Liu + Lazarev)**
- Card-based scenario selection
- Clear status indicators
- Comparison view for analysis

**5. Scenario Editor (Octet + Ran Liu)**
- Complex logic builder
- Clean, organized interface
- Real-time validation
- Preview panel

**6. AI Strategy Builder (Lazarev + Octet)**
- Guided wizard flow
- Clear progress indication
- Verification step
- AI recommendations

**7. Playbook Report (Ana Vadillo + Fuselab)**
- Comprehensive financial report
- Charts and tables
- AI insights
- Export functionality

**8. Settings (Octet + Ran Liu)**
- Organized tab navigation
- Clear form patterns
- QuickBooks connector management

**9. Audit Trail (Ana Vadillo + Fuselab)**
- Detailed log table
- Timeline visualization
- Filter and search

**10. Feature Requests (Lazarev + Octet)**
- Community feedback portal
- Voting system
- Roadmap view

**11. Calendar (Fuselab + Octet)**
- Event visualization
- Google Calendar sync
- Status-coded events

---

## 🎯 Implementation Confidence by Page

| Page | Primary Designer | Confidence | Notes |
|------|-----------------|------------|-------|
| Login | Lazarev | 95% | Simple, clean pattern |
| Navigation | Octet | 95% | Standard component-based |
| Dashboard | Fuselab + Ran Liu | 90% | React Grid Layout proven |
| Accounts | Ana Vadillo | 92% | Tables are my strength |
| Scenario Planning | Ran Liu + Lazarev | 93% | Card layouts straightforward |
| Scenario Editor | Octet + Ran Liu | 88% | Complex but doable |
| AI Wizard | Lazarev + Octet | 90% | Multi-step form pattern |
| Report | Ana Vadillo + Fuselab | 90% | Tables + charts |
| Settings | Octet + Ran Liu | 95% | Standard settings patterns |
| Audit Trail | Ana Vadillo + Fuselab | 92% | Table + timeline |
| Feature Requests | Lazarev + Octet | 90% | Card + voting pattern |
| Calendar | Fuselab + Octet | 85% | Calendar library available |

**Overall Confidence: 91%**

---

## 🚀 Development Prompt

When I begin Phase 1 development, I will use this exact prompt internally:

> "Build the Financial Playbook application using the following UI design references:
> 
> **Foundation:** Octet's component-based design system approach + Ran Liu's clean, hierarchical layouts with calm color palettes
> 
> **Financial Specifics:** Ana Vadillo's finance-grade tables with strong typographic hierarchy and carefully constrained colors for financial data display
> 
> **Dashboard & Visualization:** Fuselab Creative's configurable widget-based dashboards and data visualization patterns
> 
> **Polish & Flows:** Lazarev's professional fintech aesthetic, onboarding flows, and empty states (applied selectively)
> 
> **Technical Stack:** React 19, Tailwind CSS 4, shadcn/ui components, Chart.js for visualization, React Grid Layout for dashboard
> 
> **Visual Language:** Traffic light status system (green/yellow/red glows) applied consistently across all pages. Clean, professional, data-dense without clutter. Component-based architecture for consistency and scalability."

---

## ✅ Final Selections Summary

**My 4 Primary Designer/Agency References:**

1. **Octet** (95% confidence) - Design system foundation, component consistency
2. **Ran Liu** (95% confidence) - Clean hierarchy, layout structure
3. **Ana Vadillo** (92% confidence) - Financial tables, dense data display
4. **Fuselab Creative** (90% confidence) - Dashboard, widgets, data visualization

**Polish Layer:**
5. **Lazarev** (92% confidence, selective) - Professional fintech aesthetic, empty states, onboarding

**Overall Implementation Confidence: 91%**

**No complexities beyond my capabilities** with this combination.

---

## 📋 Next Steps

1. ✅ Designer selections finalized
2. ⏳ Begin Phase 1: Set up design system foundation
3. ⏳ Build component library based on Octet + Ran Liu
4. ⏳ Implement dashboard with Fuselab patterns
5. ⏳ Create financial tables with Ana Vadillo patterns
6. ⏳ Apply Lazarev polish selectively
7. ⏳ Implement traffic light status system
8. ⏳ Complete all 11 pages
9. ⏳ Test, refine, deploy

**Ready to begin Phase 1 development with these exact UI references.**
