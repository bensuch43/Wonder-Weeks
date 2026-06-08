# ✦ Wonder Weeks Tracker

A mobile-first Progressive Web App (PWA) that plots your baby's developmental leaps, fussy periods, and sunny windows from the Wonder Weeks framework — all calculated from their due date.

![Wonder Weeks screenshot](https://img.shields.io/badge/PWA-ready-3d5a47?style=flat-square&logo=googlechrome&logoColor=white)

---

## Features

- **Due date input** — all dates calculated from corrected age (due date), not birth date
- **Visual timeline** — scrollable colour-coded strip across all 84 weeks; tap any segment to open details
- **Current status card** — tells you exactly which phase you're in today with the next milestone date
- **Leap detail modals** — tap any leap or timeline segment for full info: abilities, signs, tips, and real calendar dates
- **Coming up next** — the next 3 milestones with week countdown and calendar date
- **All 10 leap cards** — grid overview with Now / Soon / Done badges
- **Push notifications** — opt-in browser notifications that fire on the day each fussy period, leap, and sunny window starts (requires page open that day)
- **Offline support** — works without internet after first load via Service Worker
- **Installable PWA** — add to home screen on Android or iOS for a native app feel
- **Swipe to dismiss** — modal sheets dismiss with a natural downward swipe

---

## Hosting on GitHub Pages

### 1. Create the repository

```bash
git init wonder-weeks
cd wonder-weeks
```

### 2. Copy files into the repo root

Your repo should look like this:

```
wonder-weeks/
├── index.html          ← rename wonder-weeks.html to this
├── manifest.json
├── sw.js
├── README.md
└── icons/
    ├── icon-72x72.png
    ├── icon-96x96.png
    ├── icon-128x128.png
    ├── icon-144x144.png
    ├── icon-152x152.png
    ├── icon-192x192.png
    ├── icon-384x384.png
    ├── icon-512x512.png
    ├── apple-touch-icon.png
    └── favicon-32x32.png
```

### 3. Push to GitHub

```bash
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/wonder-weeks.git
git push -u origin main
```

### 4. Enable GitHub Pages

1. Go to your repo on GitHub
2. **Settings → Pages**
3. Under **Source**, select `Deploy from a branch`
4. Branch: `main`, folder: `/ (root)`
5. Click **Save**

Your app will be live at:
```
https://YOUR_USERNAME.github.io/wonder-weeks/
```

> It can take 1–2 minutes for the first deployment to go live.

---

## Installing as a PWA

### Android (Chrome)
1. Open the GitHub Pages URL in Chrome
2. Tap the **⋮ menu → Add to Home screen**
3. The app installs with its own icon and opens full-screen

### iOS (Safari)
1. Open the GitHub Pages URL in **Safari** (must be Safari, not Chrome)
2. Tap the **Share button → Add to Home Screen**
3. Tap **Add**

> Push notifications on iOS require the app to be installed to the home screen first (iOS 16.4+).

---

## Updating the due date

The due date is stored in `localStorage` under the key `ww_due_date`. Changing it in the app automatically recalculates all dates and milestone timings.

---

## Tech stack

- Vanilla HTML / CSS / JavaScript — no frameworks, no build step
- Google Fonts (Playfair Display + DM Sans)
- Web Notifications API
- Service Worker (Workbox-free, hand-rolled)
- localStorage for persistence

---

## Wonder Weeks data

All leap timings are based on the original Wonder Weeks research by Frans Plooij. Weeks are measured from the baby's **due date** (corrected age), not birth date — this is especially important for premature babies.

| Leap | Name | Fussy starts (week) | Leap peaks (week) |
|------|------|-------------------|------------------|
| 1 | The World of Changing Sensations | 4 | 5 |
| 2 | The World of Patterns | 7 | 8 |
| 3 | The World of Smooth Transitions | 11 | 12 |
| 4 | The World of Events | 14 | 17 |
| 5 | The World of Relationships | 22 | 26 |
| 6 | The World of Categories | 33 | 37 |
| 7 | The World of Sequences | 41 | 46 |
| 8 | The World of Programs | 51 | 55 |
| 9 | The World of Principles | 60 | 64 |
| 10 | The World of Systems | 71 | 75 |

---

## Notification behaviour

Notifications fire **on page load** — they are not background push notifications. The app checks whether today matches any milestone date, fires any relevant notifications, then stores today's date to avoid double-firing on repeated opens.

To receive notifications reliably, consider opening the app each morning, or setting a daily reminder to open it.
