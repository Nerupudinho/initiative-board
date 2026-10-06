# Initiative Board

A single-file, browser-based initiative tracker. No server, no login, no install—open the file and start working.

**Live URL:** https://nerupudinho.github.io/initiative-board/ *(after Pages is enabled)*

## What It Does

Initiative Board gives you a live, editable table of everything you're tracking—with priority tiers, status labels, and rich-text task notes—and saves your changes automatically so nothing is lost between sessions.

### Features

- **Editable table** with six columns: #, Initiative, Task, Priority Tier, Status, and Context
- **Rich-text editing** in task cells: bold, italic, underline, strikethrough, highlight, bullet lists, and text colors via a floating toolbar
- **7 priority tiers** (Production Risk, Sprint Dependency, Leadership Visibility, Compliance, Parked, Admin Hygiene, Exploration) with color-coded badges and filter chips
- **8 status labels** (Not Started, In Progress, Monitoring, Pending, At Risk, Blocked, Done, Parked)
- **Auto-save to localStorage**: every edit is saved instantly with a "Saved ✓" toast confirmation
- **Daily snapshots**: each day's state is stored separately, never overwritten
- **History viewer**: browse and view past snapshots in read-only mode via the date picker
- **Dark mode**: respects your OS preference automatically
- **Resolved section**: a separate table for closed-out initiatives
- **Optional file sync**: connect a local JSON file for external tool integration (Chrome/Edge only)

### How It Works

1. Open `index.html` in any modern browser
2. Click any cell to edit; changes save automatically
3. Use the dropdown badges to set priority tier and status
4. Click filter chips to show only specific tiers
5. Select text to reveal the rich-text formatting toolbar
6. Use the History dropdown to view past snapshots

All data stays on your machine in the browser's localStorage. The file itself is the only thing you need—copy it anywhere, share it, or keep it on your desktop.

## Privacy

No data is sent to any server. Data is stored in your browser's localStorage. The only external resource loaded is the Tabler Icons font from the jsDelivr CDN. See [PRIVACY.md](PRIVACY.md) for details.

## License

[MIT](LICENSE) © 2026 Sree Sai Ganesh A
