# Tribal Kingdom — Facilities Operations Platform

Developed by **Smart Design Business Operations**. Created by Brad. Version 1.0.

---

## What this is

**`index.html` is the whole app — genuinely just one file.** The icon, the "Add to Home Screen" capability, everything is built directly into it. You will never need to juggle a manifest file, an icon file, or a service worker file separately — they're all embedded inside this one file.

Open it and it runs — login screen, dashboard, Maintenance, Inspections, Contractors, Deliveries, Reports, all connected, all working: add, edit, delete, status changes, photo capture/upload, everything live-updating on the dashboard.

## Step 1 — Look at it now

Double-click `index.html`. It opens straight in your browser. Click "Enter Platform" and you're in.

## Step 2 — Deploy it

1. Create a GitHub repo (e.g. `tribal-kingdom-platform`)
2. Add `index.html` and `vercel.json` to it (that's it — two files)
3. In Vercel: **New Project → Import** that repo
4. Vercel detects it as a static site automatically — no build config needed
5. Deploy

## Step 3 — "Add to Home Screen" / Install as an app

Once it's live on your Vercel URL (this part needs a real web address — it won't work by double-clicking the file locally, browsers block app installs from local files as a security measure):

- **On a phone (iPhone/Android):** open the link in the browser, then use the browser's "Add to Home Screen" option. It'll sit on the home screen with the gold TK icon and open full-screen, no browser bar.
- **On a laptop (Chrome/Edge):** look at the right side of the address bar for a small install icon, click it, then "Install." It'll appear on your desktop/taskbar like a real app.

That's the whole PWA layer — no extra files, no extra steps beyond what you were already doing.

## Being straight with you about where this is right now

Everything in the app works — but right now it all lives in your browser's memory. If you close the tab or reload the page, it resets back to the sample data. That's not a bug — it's simply that there's no database behind it yet. Nothing has been lost or broken; there's just nothing saving it permanently yet.

That's exactly what **Stage 2** is for, whenever you're ready:

1. **Create a Supabase project** — real, permanent database + authentication + file storage
2. **Connect it to this same `index.html`** — Supabase has a browser-ready library, so we don't need to rebuild anything or introduce a framework; we add real save/load calls into the file you already have
3. **Real login** — replacing the current "Enter Platform" button with real accounts and passwords
4. **Real photo storage** — photos captured or uploaded get saved permanently, not just held in the browser
5. **Roles** — Administrator, Manager, Staff, each seeing and editing only what they should

We do this one step at a time, and I'll walk you through each one when you say you're ready. Nothing about how the app looks or works will change — we're just connecting what's already built to a real, permanent backend.

---

Developed by Smart Design Business Operations · Created by Brad · Version 1.0
