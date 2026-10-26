# BriskWalk — Bilingual Walking Tracker

A mobile-first, English/Hindi walking tracker built with plain HTML, CSS and JavaScript. It is designed for static hosting on GitHub Pages and does not need a backend, build step, API key, or third-party JavaScript library.

## Included files

- `index.html` — complete app UI and application logic.
- `sw.js` — service worker for caching the app shell for offline reopening after the first successful load.
- `manifest.webmanifest` — installable PWA metadata.
- `icon.svg` — app icon.

## Features

- English and Hindi interface.
- Daily duration goal, weekly summary, last-seven-days chart and activity streak.
- Walk timer with start, pause, resume and save/edit flow.
- Optional GPS distance tracking with accuracy and implausible-jump filtering.
- Manual walk entry and editable/deletable history.
- Estimated steps from height and estimated calories from weight and MET values; these are approximations, not measurements.
- Kilometres/miles display setting.
- JSON backup/import and CSV export (UTF-8 BOM for spreadsheet compatibility).
- In-page reminder while the site is open, browser notifications where permitted, and downloadable daily `.ics` calendar reminder.
- Light/dark theme, local browser storage, and service-worker caching.

## Deploy to GitHub Pages

1. Create a new repository on GitHub, for example `briskwalk`.
2. Upload **all four files** from this folder to the repository root (not inside another nested folder).
3. Open the repository's **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select branch `main` and folder `/(root)`, then click **Save**.
6. Wait for GitHub Pages to publish. The site URL normally looks like `https://YOUR-USERNAME.github.io/briskwalk/`.
7. Open the published URL once while online. For the best PWA/offline behavior, use HTTPS and a modern browser.

For a user/organization repository named `YOUR-USERNAME.github.io`, the URL is usually `https://YOUR-USERNAME.github.io/`.

## Test locally

Service workers generally require HTTPS or localhost. You can open `index.html` directly to test most app features, but the PWA installation and offline cache require a local web server or GitHub Pages. For example, if Python is installed, run this from the project folder:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`.

## Important behavior and limitations

- **Data stays in this browser's local storage.** There is no account, cloud sync, analytics, or server upload. Clearing browser data, private browsing, or changing devices can lose the data. Export JSON backups regularly.
- **GPS is approximate.** Location permission is required, and the browser/operating system may suspend tracking when the tab is backgrounded or the phone is locked. Keep the page open and screen active for best results. GPS generally requires HTTPS or localhost.
- **Timer persistence:** the app saves progress periodically. If the page closes unexpectedly, the most recent saved elapsed time can be restored; a few seconds may be lost.
- **Reminders:** in-page reminders run only while the page is open. Browser notifications depend on permission and browser support. The `.ics` file adds a recurring reminder to your calendar app; it does not schedule an operating-system alarm by itself.
- **Calories and steps are estimates**, not clinical measurements. Steps are estimated from distance and a height-based stride approximation unless you manually enter steps. The app does not read a phone's hardware step counter.
- SVG icons work in many modern browsers. For best iOS home-screen icon compatibility, optionally add PNG icons (192×192 and 512×512) and a PNG `apple-touch-icon`.
- The project is a static front-end app; it has not been connected to a health provider or fitness service.

## Updating the app

After changing the app shell, increment `CACHE_NAME` in `sw.js` (for example `briskwalk-shell-v2`) so installed copies fetch the new files. Commit and push the changes; GitHub Pages will redeploy automatically.

## License

You may use, modify and host this project for personal use. Add a license file if you want to grant explicit reuse rights to others.
