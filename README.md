# NNN Countdown — November Protocol

A tiny, dependency-free No Nut November countdown website built with plain HTML, CSS, and JavaScript.

## Features
- Countdown to November 1, 2026 at 00:00 in each visitor's local timezone
- After the start, changes into an elapsed-time counter
- Responsive layout, reduced-motion support, no external fonts, libraries, analytics, or trackers
- Designed for GitHub Pages

## Publish with GitHub Pages
1. Open **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select branch `main` and folder `/ (root)`, then save.
4. Wait for GitHub Pages to publish the site.

The site URL will usually be `https://yurisxx.github.io/nnn-countdown/`.

## Customize
The target date is defined in `index.html` as:
```js
const start = new Date(2026, 10, 1, 0, 0, 0, 0);
```
JavaScript months are zero-indexed, so `10` means November. The target is midnight in each visitor's local timezone.
