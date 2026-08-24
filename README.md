# Chris Mentzer Log

A single-file progressive web app for tracking strength training built around
Mike Mentzer's Heavy Duty methodology: one all-out set to failure per exercise
in the 6–10 rep range, with full recovery between sessions.

**Live app:** https://chris-mentzer-log.netlify.app

## Features

- **Four-workout rotation** that auto-advances, so the next session is always
  the one that comes up — no manual tracking of where you are in the cycle
- **Double-progression recommendations** — the app proposes the next target
  based on whether the previous set hit the top of the rep range
- **Failure logging** — records reps completed, load used, and whether the set
  was taken to failure
- **Full session history** with editing, so a mis-entered session can be
  corrected after the fact
- **Progress views** across sessions and exercises
- **Backup and restore** — export and reimport all data as JSON
- **Configurable units** (lb/kg) and default weight increments
- **Installable** to a phone home screen, works offline

## Technical Notes

The entire application is one `index.html` file — markup, styles, and logic
inline, with no build step and no dependencies. Data lives in `localStorage`
on the device; nothing is sent to a server.

Two implementation details worth calling out:

**Schema migration.** Version 2 changed how sessions were date-stamped to fix
a bug where sessions could be attributed to the wrong day. Rather than reset
existing data, the app detects the old schema on load and migrates it in
place, so users kept their history across the upgrade.

**PWA installability.** Getting a reliable install prompt required flat-color
icons at the correct sizes and an explicit `beforeinstallprompt` handler that
surfaces a custom install banner, rather than relying on the browser's default
behavior.

## Stack

HTML5, CSS, vanilla JavaScript, Service Worker, Web App Manifest,
localStorage. Deployed on Netlify.

## Running Locally

Clone the repository and open `index.html` in a browser. No build, no server,
no install step.

## Author

Chris Nhul — https://github.com/nhulchris
