# Multifamily Strategy Sales Academy — Foundation MVP Build

Static, GitHub/Vercel-ready onboarding demo for Multifamily Strategy.

## Included in this build

- Branded login gate (`admin` / `freesample`)
- Appointment Setter and Closer role selection
- Complete **Unit 1: MFS Foundation** for both paths
- Foundation lessons, factual knowledge checks, spoken-response scenarios, explanations, XP and the Foundation Check
- Back/review flow after mistakes
- Exact local resume using `localStorage`
- Visible roadmap for later units
- Progress and Call Readiness preview
- Responsive desktop/mobile layout
- PWA/offline support

## Deliberately excluded

Detailed lesson content for Unit 2 onward is **not shipped in this build**. The roadmap metadata remains visible so the broader academy structure can be demonstrated, but those lessons contain no hidden screens to bypass. Glossary and Resources remain available in the MVP.

## Deploy to Vercel

1. Upload every file in this folder to the repository root.
2. Import the repository into Vercel.
3. Framework preset: **Other** (or auto-detected).
4. No build command is required.
5. Deploy.

`index.html` is the entry point.

## Progress storage

Foundation progress is stored locally under:

`mfs_sales_academy_progress_foundation_sample_v1`

The rep returns to the exact lesson and screen on the same browser/device.

## Authentication note

The login gate is intentionally client-side for the demo. It is not secure authentication for sensitive production content. A production implementation should use authenticated server-side/user-account access (for example Supabase Auth).

## Files

- `index.html` — app shell
- `styles.css` — responsive branded UI
- `curriculum.js` — Foundation curriculum plus roadmap-only metadata for later units
- `app.js` — login, progress, locking, quizzes, scenarios and MVP gating
- `service-worker.js` / `manifest.json` — PWA support
- `vercel.json` — Vercel static config

- Glossary and Resources remain available; only Unit 2+ training curriculum is locked.
