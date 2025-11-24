# Financial Playbook

**Organize the chaos. Trust your numbers. Grow with confidence.**

A comprehensive financial planning and scenario modeling application designed for small business owners who need to make confident decisions even when their financial data isn't perfect.

---

## 🎯 What is Financial Playbook?

Financial Playbook is an intelligent financial planning tool that helps business owners:

- **Validate QuickBooks data** against bank statements for independent verification
- **Visualize discrepancies** with an intuitive traffic light status system (🟢🟡🔴)
- **Plan scenarios** with AI-powered what-if analysis and logic simulation
- **Make confident decisions** based on validated, reconciled financial data
- **Save time** by automating financial analysis and reporting

### The Problem We Solve

Most small business owners don't have 100% faith in their QuickBooks data. Transactions get missed, bills aren't recorded on time, and discrepancies creep in. But decisions still need to be made.

Financial Playbook provides **independent verification** through bank statement analysis, **intelligent reconciliation** to highlight where systems diverge, and **forward-looking intelligence** to plan the future with confidence.

---

## ✨ Key Features

### 🔐 Authentication & Security
- Google OAuth 2.0 integration
- Secure session management
- Comprehensive audit trail

### 📊 QuickBooks Online Integration
- Real-time data synchronization
- Configurable sync frequency (hourly, 4h, 8h, 24h)
- Webhook integration for instant updates
- Read-only data policy (edit at source)
- "View in QuickBooks" links

### 🤖 AI-Powered Strategy Builder
- Upload bank statements (PDF/images)
- OCR and intelligent document analysis
- Automated scenario recommendations
- **AI Math Validation** - all calculations verified by traditional code
- Root cause analysis and insights

### 🎮 Logic Simulator & Scenario Planning
- Multi-scenario support with lock-in capability
- Business rule engine (IF/THEN logic)
- Day-by-day simulation
- Risk detection and flagging
- Comprehensive reports with charts

### 🚦 Visual Status System
- **🟢 GREEN** - In sync, healthy, no issues
- **🟡 YELLOW** - Warning, attention needed (variance, delays, duplicates)
- **🔴 RED** - Critical, action required (missing transactions, overdraft risk)
- Info bubbles (ℹ️) with detailed explanations
- Applied consistently site-wide

### 📐 Customizable Dashboard
- Drag-and-drop widget repositioning
- Resizable widgets
- 9 available widgets (alerts, cash flow, stats, bills, balances, etc.)
- Layout persistence
- Mobile responsive

### 📅 Google Calendar Integration
- Two-way sync with Playbook activities
- Color-coded events matching status system
- Automatic event creation for bills, payments, tasks
- Calendar view page

### 🔍 Audit Trail System
- Immutable logging of all changes
- Before/after snapshots
- User tracking
- Filterable audit reports

### 💡 Feature Request System
- Built-in feedback portal
- User submission and voting
- Status tracking
- Public roadmap
- Admin dashboard

---

## 🛠️ Tech Stack

**Frontend:**
- React 19
- Tailwind CSS 4
- Next.js
- React Grid Layout
- Chart.js

**Backend:**
- Express 4
- tRPC 11 (type-safe API)
- NextAuth.js (OAuth)
- Prisma ORM

**Database:**
- PostgreSQL (MySQL/TiDB)
- Row-level security
- Audit logging

**Deployment:**
- Vercel
- GitHub Actions CI/CD
- Automated testing (Vitest)

**AI/LLM:**
- OpenAI GPT-4 or Grok
- Document OCR and analysis
- Math validation layer

---

## 🔌 External Integrations

**Core:**
- QuickBooks Online API (OAuth 2.0)
- Google OAuth 2.0 (Authentication)
- Google Calendar API (OAuth 2.0)
- AI/LLM API (GPT-4 or Grok)
- Email Service (SendGrid/AWS SES)
- Cloud Storage (S3)

**Future:**
- Plaid API (additional bank connections)
- Stripe API (payment processing)
- Tax software integration
- Cryptocurrency APIs

---

## 📋 Development Status

**Current Phase:** Phase 1 - Project Setup & Basic Authentication

**Timeline:** 7-10 weeks (single-user MVP)

### Development Phases

1. ✅ **Phase 0:** Planning & Documentation (COMPLETE)
2. 🚧 **Phase 1:** Project Setup & Basic Authentication (1 week)
3. ⏳ **Phase 2:** QuickBooks Integration & Financial Data Engine (2 weeks)
4. ⏳ **Phase 3:** AI Strategy Builder with Math Validation (2-3 weeks)
5. ⏳ **Phase 4:** Logic Simulator & Validated Report Generator (2-3 weeks)
6. ⏳ **Phase 5:** Automation, Audit Trail & Final UI (1-2 weeks)
7. ⏳ **Phase 6:** Security Review, Testing & Deployment (1 week)

See [todo.md](./todo.md) for detailed task tracking (90+ tasks).

---

## 📚 Documentation

Comprehensive documentation is available in the `docs/` directory:

- **[MASTER_PLAYBOOK_COMPLETE.pdf](./docs/MASTER_PLAYBOOK_COMPLETE.pdf)** (200+ pages)
  - Complete project specification
  - All wireframes with QC numbering
  - System specifications
  - Technical architecture
  - Security analysis
  - Development plan

- **[TODAYS_ADDITIONS_SUMMARY.pdf](./docs/TODAYS_ADDITIONS_SUMMARY.pdf)** (20 pages)
  - Recent feature additions
  - Design decisions
  - Key insights
  - Statistics overview

---

## 🎨 UI/UX Design

### Quality Control Numbering System

Every UI element has a unique 3-digit QC number for easy reference during development:

- **100s:** Login/Authentication
- **200s:** Global navigation and Dashboard
- **300s:** Accounts Management
- **400s:** Scenario Planning
- **500s:** Scenario Editor/Logic Builder
- **600s:** AI Strategy Builder Wizard
- **700s:** Playbook Report View
- **800s:** Settings & Notifications
- **900s:** Audit Trail Report
- **1000s:** Feature Request System
- **1050s:** Calendar View

QC numbers can be toggled on/off in Settings for production deployment.

---

## 🚀 Getting Started

### Prerequisites

- Node.js 22.13.0+
- pnpm
- PostgreSQL database
- QuickBooks Online developer account
- Google OAuth credentials

### Installation

```bash
# Clone the repository
git clone https://github.com/SuperiorNetworks/financial-playbook.git
cd financial-playbook

# Install dependencies
pnpm install

# Set up environment variables
cp .env.example .env
# Edit .env with your credentials

# Push database schema
pnpm db:push

# Start development server
pnpm dev
```

### Environment Variables

See `.env.example` for required environment variables including:
- Database connection
- OAuth credentials (Google, QuickBooks)
- AI/LLM API keys
- Email service credentials
- Storage credentials

---

## 🧪 Testing

```bash
# Run all tests
pnpm test

# Run tests in watch mode
pnpm test:watch

# Run tests with coverage
pnpm test:coverage
```

---

## 📈 Roadmap

### Current Focus (Single-User MVP)
- Google OAuth 2.0 authentication
- QuickBooks Online integration
- AI Strategy Builder
- Logic Simulator
- Visual status system
- Customizable dashboard

### Future Enhancements (Post-MVP)
- Multi-user support
- Delegated access for tax professionals
- Mobile app (iOS/Android)
- Advanced AI delegation
- Additional integrations (Plaid, Stripe, tax software)
- Cryptocurrency tracking

---

## 💡 Value Proposition

**For:** Small business owners ($500K-$5M revenue)

**Who:** Don't have 100% faith in their QuickBooks data but need to make critical decisions

**Financial Playbook is:** An intelligent financial planning tool

**That:** Validates QuickBooks against bank statements, visualizes discrepancies, and provides AI-powered insights

**Unlike:** Traditional bookkeeping software or manual spreadsheets

**Our solution:** Organizes the chaos, builds trust in your numbers, and enables confident decision-making

### ROI
- **Time savings:** 4 hours/week → 15 minutes/week
- **Cost savings:** $10,000+/year in avoided mistakes
- **Revenue impact:** 5-10% increase through better decisions
- **Total ROI:** 10-25x return on investment

---

## 🤝 Contributing

This is currently a private project in active development. Contributions will be welcomed once the MVP is complete.

---

## 📄 License

Proprietary - All rights reserved.

---

## 📞 Contact

For questions or feedback, please use the built-in Feature Request System once deployed, or contact through the repository issues.

---

## 🙏 Acknowledgments

Built with modern web technologies and AI-powered analysis to help small business owners make confident financial decisions.

**Tagline:** *Organize the chaos. Trust your numbers. Grow with confidence.*

---

**Status:** 🚧 In Active Development | **Version:** 0.1.0 | **Last Updated:** November 24, 2025
