# AKCLNT CHRONO — Time, Engineered

A cinematic 3D watch-store demo by **AKCLNT Studio** (https://akclnt.com).
The page *is* the watch: scroll and the AK-01 skeleton tourbillon comes apart
layer by layer — 211 parts, every gear turning at its true ratio — then
reassembles into a three-reference collection you can actually buy from.

![AKCLNT CHRONO](public/og-image.jpg)

## What's inside

- **3D experience** (`index.html` + `main.js`) — three.js (r186) with an HDR
  post stack (N8AO ambient occlusion, bloom, AgX/neutral tone mapping, film
  grain, depth of field), Lenis + GSAP scroll choreography, a procedural
  movement (`movement.js` / `geo.js` / `finish.js`), hold-the-crown winding
  with a live power-reserve gauge, and a deep-navy + champagne-gold AKCLNT theme.
- **The AKCLNT Edit** — a photo gallery section (Midnight / Sovereign / The Bench).
- **Shop** (`shop.html`) — catalogue with category filters, search and a detail
  modal with WhatsApp ordering. **Demo mode is ON** (`USE_BACKEND = false` in
  `shop.js`): the live site uses the built-in catalogue and makes no API calls.
- **Admin** (`admin/login.html`, `admin/dashboard.html`) — add / edit / delete
  watches, view orders, export orders to Excel. Protected by JWT.
- **Backend** (`backend/`, **not deployed**) — Express + lowdb (JSON file DB),
  Multer photo uploads, order capture with automatic Excel export. It lives in
  this repo for code showcase and local runs only; the public demo is
  frontend-only.

## Run the frontend

```bash
npm install
npm run dev        # http://127.0.0.1:5190
npm run build      # -> dist/  (deploy this on Vercel)
```

## Run the backend (local only — it is not hosted for this demo)

```bash
cd backend
cp .env.example .env   # set JWT_SECRET, ADMIN_USERNAME, ADMIN_PASSWORD
npm install
npm start              # http://localhost:5000
```

On localhost the shop and admin talk to `http://localhost:5000` automatically.
Seed data lives in `backend/data/db.json`; product photos in `backend/uploads/`.

## Deploy on Vercel

Import this repo, framework preset **Vite** (or use the included `vercel.json`).
Build command `npm run build`, output `dist`. No environment variables, no
backend hosting, nothing else to configure — **frontend only**. The shop runs
in demo mode on its built-in catalogue, and the admin login shows a demo-mode
notice (the panel itself works when the backend is run locally). If this ever
becomes a real store: host `backend/`, set `USE_BACKEND = true` in `shop.js`,
and point `API_BASE` at it.

## Credits & license

Code: MIT. The 3D engine approach and the hero watch model originate from the
open-source *Dioramas* framework (three.js ecosystem — see
`THIRD_PARTY_NOTICES.md`); AKCLNT CHRONO is an independent rebrand and rewrite
(new brand, copy, palette, photography and shop data) built by AKCLNT Studio.
Fonts: Fraunces + Manrope (Google Fonts, OFL).
