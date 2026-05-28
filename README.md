# Tic-Tac-Toe

A modern, mobile-friendly Tic-Tac-Toe web app — single-file HTML/CSS/JS, no build step, installable as a PWA.

## Features

- **Modes:** Player vs Player (local) and Player vs AI
- **AI difficulty:**
  - Easy — random moves
  - Medium — ~60% minimax / 40% random, rolled per move
  - Hard — perfect minimax (never loses)
- **PvA fairness:** who goes first alternates each round (human X → AI X → human X …)
- **Persistent scores** via `localStorage` (X / Draws / O), with reset
- **Confetti** on any human win (PvP either player; PvA only when human wins)
- **PWA:** installable, offline-capable via service worker
- **Mobile-first:** large tap targets (≥80px), works from 375px wide up

## Run locally

It's a static site — open `index.html` in a browser, or serve the folder:

```bash
# any static server works; for example:
npx serve .
# or
python -m http.server 8080
```

Then visit `http://localhost:3000` (or whatever port your server prints).

> Service workers and the install prompt require an `http(s)://` origin — they won't activate when opening the file directly via `file://`. Use a local server to test PWA features.

## Deploy to Vercel

Zero config. Either:

**Via CLI:**

```bash
npm i -g vercel
vercel
```

**Via dashboard:** import the repo on [vercel.com/new](https://vercel.com/new). Framework preset: **Other**. Build command: none. Output directory: `.` (root).

`vercel.json` sets correct headers for the service worker and manifest.

## Files

| File | Purpose |
| ---- | ------- |
| `index.html` | App — markup, styles, game logic |
| `manifest.json` | PWA manifest |
| `sw.js` | Service worker (cache-first, offline) |
| `icon.svg` | App icon |
| `vercel.json` | Headers config for Vercel |

## Notes

- For the best PWA install experience on iOS/Android, also add `icon-192.png` and `icon-512.png` (the manifest references them). The SVG icon works as a fallback in most modern browsers.
