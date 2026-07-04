
# Tribal Kingdom — Facilities Operations Platform

Premium property management platform for Tribal Kingdom.
Developed by **Smart Design Business Operations**. Created by Brad. Version 1.0.

---

## What's in this drop

This is the **first delivery**, scoped so you can get something live on Vercel today and see the branding, dashboard and navigation working end-to-end:

- `app/page.tsx` — the login / index screen
- `README.md` — this file
- `package.json` — project dependencies and scripts

The rest of the application code (dashboard, Maintenance, Inspections, Contractors, Deliveries, Reports, shared components, Tailwind config, etc.) is included in the full project bundle alongside these three, exactly as you asked — these three are just called out separately because they're the ones you need to get a deployment live first.

Right now the app runs on **mock/local data** so every screen is clickable and demoable immediately. Nothing is wired to a real database yet — that's Phase 2, below.

---

## Stage 1 — Get it live (GitHub → Vercel)

You said you're comfortable with this part, so just the checklist:

1. Create a new GitHub repository (e.g. `tribal-kingdom-platform`).
2. Push this whole project folder to that repo (keep the folder structure exactly as-is).
3. In Vercel: **New Project → Import** the GitHub repo.
4. Framework preset: Vercel will auto-detect **Next.js** — leave the defaults.
5. Deploy.

You do **not** need any environment variables for this first deploy — the app will build and run on mock data without Supabase. That's intentional, so you can confirm the branding, layout and navigation look right before we connect a real database.

Locally, if you want to preview before pushing:

```bash
npm install
npm run dev
```

Then open `http://localhost:3000`.

---

## Stage 2 — Connecting Supabase (once you're happy with the look)

This is the part you said you haven't done before — when you're ready, tell me and I'll walk you through it step by step, in order:

1. **Create a Supabase project** — the database, auth and storage backend.
2. **Design the schema** — tables for `maintenance`, `inspections`, `inspection_items`, `contractors`, `deliveries`, `properties`, `users/roles`, with timestamps and "updated by" fields per the blueprint's data requirements.
3. **Enable Row Level Security (RLS)** — so Administrator / Manager / Staff roles see and edit only what they should.
4. **Connect Supabase Auth** — replace the mock login in `app/page.tsx` with real authentication.
5. **Connect Supabase Storage** — for maintenance photos and report attachments.
6. **Wire each module's forms** to real inserts/updates instead of mock state.
7. **Add environment variables in Vercel** (`NEXT_PUBLIC_SUPABASE_URL`, `NEXT_PUBLIC_SUPABASE_ANON_KEY`) and redeploy.

We'll do this one step at a time so you understand what each piece does, not just copy-paste it.

---

## Project structure

```
tribal-kingdom/
├── app/
│   ├── page.tsx              # Login / index screen
│   ├── layout.tsx            # Root layout, fonts, metadata
│   ├── globals.css           # Design tokens & shared styles
│   ├── dashboard/page.tsx    # Executive dashboard
│   ├── maintenance/page.tsx  # Maintenance module
│   ├── inspections/page.tsx  # Property inspection module
│   ├── contractors/page.tsx  # Contractor module
│   ├── deliveries/page.tsx   # Delivery module
│   └── reports/page.tsx      # Reports module
├── components/
│   ├── Sidebar.tsx
│   ├── Header.tsx
│   ├── Footer.tsx
│   ├── StatCard.tsx
│   └── QuickActions.tsx
├── lib/
│   └── mock-data.ts          # Placeholder data (removed once Supabase is connected)
├── package.json
├── tailwind.config.ts
├── tsconfig.json
└── next.config.js
```

## Design system

| Token | Value |
|---|---|
| Deep Navy | `#0A1930` |
| Slate Blue | `#3E5C87` |
| Champagne Gold | `#C9A968` |
| Status – Completed | `#3F9C6D` |
| Status – Attention | `#D6A339` |
| Status – Overdue | `#C25450` |
| Status – Information | `#4E7FBF` |
| Display type | Fraunces |
| Body / data type | Inter |
| Monospace (timestamps, IDs) | IBM Plex Mono |

Login screen uses a dark navy gradient with frosted glass panels and a gold crest mark. The dashboard and internal modules use a lighter soft blue-grey gradient with frosted-white glass cards, per the blueprint's brief.

## Roles (UI-level for now, enforced by Supabase RLS in Phase 2)

- **Administrator** — full access
- **Manager** — view all operations, manage maintenance & inspections, generate reports
- **Staff** — capture maintenance, complete inspections, record deliveries, update assigned work

---

Questions any time — just tell me what you want to tackle next.
