# NNN Countdown

A lightweight, responsive No Nut November countdown and day-by-day calendar. Built with plain HTML, CSS, and JavaScript—no frameworks, build tools, external fonts, analytics, or third-party scripts.

**Live site:** https://yurisxx.github.io/nnn-countdown/

## Features

- **Automatic yearly countdown.** Before November, counts down to November 1. During November, counts down to December 1. From December onward, it advances to the next year's challenge.
- **Visitor-local time zones.** NNN starts at local midnight on November 1 and ends at local midnight on December 1 in the visitor's own time zone. The displayed target offset accounts for daylight-saving changes.
- **English and Russian interface.** Use the EN / RU switch in the top-right corner. The choice is remembered in the current browser.
- **Current and historical calendars.** The current/upcoming November appears alongside a past November. Choose a previous year from the selector (2000 through the most recently completed challenge year).
- **Context menu for each day.** Past dates and today can be marked **Success**, **Failed**, or **Unmarked**. Future dates are disabled. Click outside the menu or press Escape to dismiss it. Keyboard users can navigate the menu with the arrow keys, Home, and End.
- **Past-day statistics.** Shows successful marked days, the current and longest success streak, and success rate. Future and unmarked days are excluded from the success-rate denominator. Unmarked days do not break a streak; a marked failed day does. Streaks can be updated later by marking missed dates.
- **Today's marker.** A restrained red outline identifies today's date in the current November calendar and refreshes after local midnight.
- **JSON backup and restore.** Export all saved years into one JSON file and import a backup later. Import validates the file and asks before replacing data for the included years; other years remain unchanged. Future-date marks are cleared on import/export.
- **Cross-tab updates.** Changes made in another tab of the same browser profile refresh the calendar.
- **Per-year summaries.** Each calendar counts success, failed, and unmarked days.
- **Responsive layout.** Calendars stack on narrow screens and the day menu stays within the visible viewport.
- **Local-only data.** No account or server is needed, and calendar entries are never uploaded.

## Calendar data and privacy

Daily statuses use the browser's `localStorage`, with one key per year (for example, `nnn-calendar:v1:2026`). Each key stores an array of 30 values: `unmarked`, `success`, or `failed`.

The language preference is stored separately under `nnn-language:v1`.

- Data persists across reloads in the same browser profile.
- Data is not sent to GitHub or any other server.
- Browsers and devices do not share data; there is no synchronization or account system.
- Clearing site/browser data can erase saved entries.
- Private browsing or browser settings may block persistent storage. The page displays a notice if saving is unavailable.

## Run locally

No build step is required. Open `index.html` in a browser, or run a local static server. For example, with Python installed:

```sh
python3 -m http.server 8000
```

Then visit http://localhost:8000.

## Deploy on GitHub Pages

1. Open **Settings → Pages** in the repository.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select branch `main` and folder `/ (root)`, then save.
4. Wait for deployment, then open https://yurisxx.github.io/nnn-countdown/.

This is a static site: there is no build command or output directory.

## Project structure

- `index.html` — page markup, styles, countdown logic, bilingual interface, calendar menus, and local storage.

## Date logic

- Challenge start: November 1 at 00:00:00 in the visitor's local time zone.
- Challenge end: December 1 at 00:00:00 in the visitor's local time zone.
- Before November, the countdown targets that year's start; during November it targets that year's end; from December onward it targets the next year's start.
- The displayed timestamp includes the target date's UTC offset (for example, `UTC+03:00`). The offset is calculated for the target date, so daylight-saving changes are accounted for.
- Only dates up to and including today can be marked. Future dates are disabled and are cleared from imported or exported backups.
- Statistics count only completed days (up to yesterday). The success rate uses marked completed days only. Unmarked days are ignored when calculating streaks; a failed day resets the streak.
- Calendar statuses are user-entered notes, not an automatic judgement. The app does not verify behavior or prevent someone from editing past statuses; this is a personal tracker, not an enforcement system.

## License

No license file is included yet. Add one if you want to explicitly permit reuse of the project.
