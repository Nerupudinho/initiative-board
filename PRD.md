# Now Dashboard — Product Requirements Document

**Tool:** now.html
**Type:** Local, browser-based productivity tool
**Last updated:** 19 May 2026
**Status:** Live

---

## What Is This

`now.html` is a single-file, offline initiative tracker that runs entirely in the browser. No server, no login, no install. Open the file, start working.

It gives you a live, editable table of everything you're tracking — with priority tiers, status labels, and rich-text task notes — and saves your changes automatically so nothing is ever lost between sessions.

---

## Problem It Solves

Most initiative tracking lives in tools that are either too heavy (JIRA, Notion) or too transient (a doc you stop updating). A PM's "Now" list — the 20–40 things actively in flight — needs to be:

- Fast to open and edit
- Always up to date (no friction to save)
- Structured enough to filter and scan quickly
- Owned locally, not locked in a SaaS

`now.html` is a single file you keep on your desktop. It behaves like a live, structured scratchpad.

---

## Features

### 1. Editable Table

The core of the tool is a table with six columns:

| Column | Type | Behaviour |
|---|---|---|
| # | Auto | Row number, auto-incremented |
| Initiative | Rich text | Editable, bold by default |
| Task | Rich text | Full contenteditable — supports bold, italic, underline, strikethrough, highlight, bullet lists |
| Priority Tier | Badge dropdown | 7 tiers (see below), click to change |
| Status | Badge dropdown | 8 statuses (see below), click to change |
| Context | Plain text chip | Reference pointer (file path, doc name, etc.) |

All cells are directly editable in the browser — click and type.

---

### 2. Priority Tiers

Seven tiers for classifying urgency and visibility:

| Tier | Label | Colour |
|---|---|---|
| 🔴 | Production Risk | Red |
| 🟠 | Sprint Dependency | Orange |
| 🟡 | Leadership Visibility | Yellow |
| 🔵 | Compliance | Blue |
| ⚪ | Parked | Grey |
| 🟢 | Admin Hygiene | Green |
| 🔷 | Exploration | Purple |

Tiers are assigned via a click dropdown on each row. They drive the filter chips at the top of the page.

---

### 3. Status Labels

Eight statuses reflecting real initiative states:

| Status | Colour |
|---|---|
| Not Started | Grey |
| In Progress | Blue |
| Monitoring | Green |
| Pending | Amber |
| At Risk | Orange |
| Blocked | Red |
| Done | Teal |
| Parked | Light grey |

Assigned via a click dropdown. Colour-coded pill badges for at-a-glance scanning.

---

### 4. Filter Chips

A row of filter chips above the table — one per priority tier plus an "All" chip. Clicking a chip hides all rows not in that tier. The item count in the header updates to show `X of Y` when filtered.

---

### 5. Floating Rich-Text Toolbar

Select any text in a cell and a floating toolbar appears above the selection. Supports:
- Bold, Italic, Underline
- Strikethrough
- Highlight (yellow)
- Bullet list
- Text color (6 colour swatches + clear — Red, Amber, Blue, Green, Purple, Grey)

Useful for marking tasks done inline (~~strikethrough~~) or calling out next actions.

---

### 6. Add Row

A persistent "Add row" button at the bottom of the table (and a duplicate in the header) appends a new blank row and focuses the Initiative cell immediately. New rows are auto-saved.

---

### 7. Resolved Section

A separate static table at the bottom for items that are closed out. Columns: Initiative, Resolution, Date, Context. Also fully editable.

---

### 8. Auto-Save (localStorage)

Every change — cell edit, status change, tier change, new row — is written to the browser's `localStorage` instantly. A "Saved ✓" toast confirms each write.

- **No save button needed.** The save is invisible and automatic.
- **Data survives browser close, tab close, and system restart.**
- Opens the file tomorrow and your data is exactly where you left it.

---

### 9. Daily Snapshots

Each day's state is stored under its own date key (`now_YYYY-MM-DD`). Previous days are never overwritten.

**Load behaviour on open:**
1. Finds the most recent saved date in localStorage
2. Loads from that — could be today or a previous session
3. Falls back to the template SEED data only on the very first open

This means: opening on a new day automatically continues from where you left off. You never start from scratch.

---

### 10. History Viewer

A **📅 History** dropdown in the header lists every date for which a snapshot exists. Selecting a past date:

- Renders that day's table in **read-only mode**
- Shows a yellow banner: *"Viewing snapshot: 14 Apr 2026"*
- Locks all cells and disables all dropdowns
- Hides the Add row buttons
- Offers a **"← Return to Today"** button to exit back to live mode

The history is a permanent audit trail. Each day you use the tool, a new snapshot is automatically added to the picker.

---

### 11. Dark Mode

Respects the OS-level `prefers-color-scheme: dark` setting. All tier and status colours are remapped for dark backgrounds automatically.

### 12. File Sync (Claude-readable export)

A **Connect file** button in the header lets you link a local `now-state.json` file. Once connected:
- Every save writes the current table state to that JSON file automatically
- The file handle is persisted in IndexedDB so the connection survives browser restarts (requires re-granting permission on next open)
- Button states: Connect file → Synced ✓ → ↺ Reconnect file (if permission lapses)

Use case: makes your Now state readable by Claude Code or any local script — no copy-paste needed.

Requires a browser that supports the File System Access API (Chrome/Edge; not Safari or Firefox).

---

## Non-Features (Intentional Omissions)

- **No server.** Everything runs locally. Nothing is sent anywhere.
- **No accounts.** The file is yours; it lives where you put it.
- **No cloud sync.** Data stays on your machine — localStorage + optional local file export. No server, no account required.
- **No export.** The file itself is the export — copy it, email it, open it anywhere.

---

## File Structure

Single `.html` file. No dependencies except one CDN-loaded icon font (Tabler Icons). Works offline after first load if icons are cached.

```
now.html
  ├── CSS (embedded)
  ├── HTML structure
  └── JavaScript (embedded)
        ├── SEED[] — default template rows
        ├── localStorage helpers (save, load, allKeys)
        ├── renderRows() — bulk render with read-only flag
        ├── buildHistoryPicker() — populates date dropdown
        ├── addRow() — appends and saves
        ├── Tier / Status dropdown logic
        ├── Filter logic
        └── Rich-text toolbar
```

---

## Setup

1. Copy `now.html` to wherever you work from (desktop, project folder, etc.)
2. Open in any browser
3. Edit the SEED array to pre-populate with your own starting rows, or start blank and add rows manually
4. Everything from that point is automatic
