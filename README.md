# NNN Countdown

A small, responsive No Nut November countdown and day-by-day calendar. It uses plain HTML, CSS, and JavaScript—no frameworks, build tools, external fonts, analytics, or third-party scripts.

**Live site:** https://yurisxx.github.io/nnn-countdown/

## Features

- **Automatic yearly countdown.** Before November, counts down to November 1 at 00:00 UTC. During November, counts down to December 1 at 00:00 UTC. In December, it moves on to the next year's challenge.
- **Consistent time zone.** All event boundaries use UTC, so everyone sees the same start and end instant regardless of their local time zone.
- **Two editable calendars.** The current/upcoming November is shown alongside a past November calendar. The history selector lets you choose any year from 2000 up to the most recent completed challenge year.
- **Three states per day.** Click a date to cycle through `Unmarked → Success → Failed → Unmarked`. This works before November starts, and past calendars can be filled in manually.
- **Per-year summaries.** Each calendar counts successful, failed, and unmarked days.
- **Responsive and accessible.** The layout adapts to narrow screens, calendar cells are buttons with accessible labels, and keyboard focus is visible.
- **No server or account required.** Calendar entries stay in the visitor's browser.

## How calendar data is stored

The calendar uses the browser's `localStorage`, with a separate key for each year (for example, `nnn-calendar:v1:2026`). Each key stores the 30 daily states as a small JSON array.

This is local-only storage:
- Entries persist across page reloads in the same browser profile.
- Entries are **not** sent to GitHub or any other server.
- Different browsers and devices have separate data; there is no synchronization or account system.
- Clearing site/browser data can erase the calendar.
- Private browsing or browser settings may block persistent storage. The page displays a note if storage is unavailable.

## Run locally

No build step is needed. Open `index.html` in a browser, or serve the folder with any static file server. For example, with Python installed:

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Deploy on GitHub Pages

1. Open **Settings → Pages** in the repository.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Select branch `main` and folder `/ (root)`, then save.
4. After the deployment finishes, open https://yurisxx.github.io/nnn-countdown/.

Because this is a static site, there is no build command or output directory.

## Project structure

- `index.html` — markup, styles, countdown logic, calendar UI, and local storage.

## Implementation notes

The event start is November 1 at 00:00 UTC, and the event end is December 1 at 00:00 UTC. JavaScript calculates the relevant year from the current UTC date; no yearly code edit is needed. The calendar itself can be marked any time and does not automatically decide success or failure based on the current date.

There is no license file yet; add a license if you want to explicitly grant reuse permissions.
