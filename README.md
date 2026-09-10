# Office Hours Tracker

A single-file, no-backend web app for tracking office attendance and calculating WFH timesheet entries. Built for a 3.5-hour minimum office presence requirement and a 9:15 total daily working-hour target.

Runs entirely client-side — no server, no build step, no data collection. Works offline once loaded, and installs as a Home Screen app on iPhone.

## Features

**Live Timer**
- Enter (or tap "Now" for) your office in-time.
- Shows live elapsed time in office, updating every second.
- Progress bar toward a 3h 30m minimum.
- On-screen alert + audio beep (and a push notification, if the browser/OS allows it) once 3h 30m is reached.
- Resumes automatically if the page reloads mid-session, using saved state and the current clock time — no background process required.

**Timesheet Calculator**
- Enter office in/out time (24-hour format).
- Set your total daily target (default 9:15).
- Calculates remaining WFH time needed and suggests an exact WFH slot to log.
- "Auto" placement fills WFH *after* office if you clocked in before noon, or *before* office if you clocked in during the afternoon/evening — switchable manually.
- Configurable buffer (minutes) between office and WFH slots.

All entered values are saved locally in the browser (`localStorage`) so they persist across reloads on the same device/browser.

## Hosting

This is a static HTML file — any static host works. Recommended free options:

- **GitHub Pages**: rename the file to `index.html`, push to a repo, enable Pages in repo Settings → Pages, source = `main` branch.
- **Netlify Drop**: drag-and-drop the file at [app.netlify.com/drop](https://app.netlify.com/drop) for an instant HTTPS link.

Hosting it on a real `https` URL (rather than opening the raw file locally) is required for:
- Push notification permission (iOS/Safari blocks this on local `file://` pages).
- Reliable persistence when the page is backgrounded or the tab is reopened.

## Installing on iPhone

1. Open the hosted URL in Safari.
2. Tap **Share → Add to Home Screen**.
3. Launch it like a normal app from the Home Screen icon going forward.

## Notes / limitations

- Times only support a single continuous office in/out pair (no split shifts).
- The live timer calculates elapsed time from the entered clock time vs. current time — it does not run as a true background process, so if iOS fully suspends the tab for an extended period, reopening it will still show the correct elapsed time (it's always recalculated), but a notification fired while suspended may be delayed or missed.
- No data is sent anywhere; everything stays on-device.

## Files

- `index.html` — the entire app (HTML, CSS, JS in one file).


