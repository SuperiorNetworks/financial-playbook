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
