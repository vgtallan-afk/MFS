# Multifamily Strategy Sales Academy — MVP

Static, GitHub/Vercel-ready gamified onboarding app built from the supplied **MFS Sales Team Master SOP v2 (Sept 9, 2026)**, with non-conflicting useful context from v1.

## What is included

- First-run role picker: **Appointment Setter** or **Closer**
- Separate locked learning paths
- Duolingo/Tabelingo-style sequential lesson road
- Lesson → knowledge check → XP loop
- Click-ahead **Test Out** flow: 100% required to skip prerequisites
- Exact local resume: role, current view, active lesson, screen index, XP and completed lessons persist in `localStorage`
- Optional technical glossary (does not block the path)
- Role-filtered SOP index and source links
- Responsive desktop/mobile layout
- PWA manifest + offline cache
- No build step and no external dependencies

## Deploy to Vercel

1. Create a new GitHub repository.
2. Upload **all files in this folder to the repository root**.
3. In Vercel, choose **Add New Project** and import the repo.
4. Framework preset: **Other** (or leave auto-detected).
5. No build command is required.
6. Deploy.

`index.html` is the app entry point.

## Progress storage

The MVP uses local browser storage under:

`mfs_sales_academy_progress_v1`

This means a rep returns to the exact lesson/screen on the same browser/device.

## Supabase-ready next step

The state layer contains an optional adapter hook:

```js
window.MFSProgressAdapter = {
  async save(state) {
    // upsert by authenticated user id
  }
}
```

For team-wide manager tracking, the next production step is:

- Supabase Auth (one user per rep)
- `rep_progress` table: user_id, role, completed_lessons, xp, active_lesson, screen, updated_at
- Manager dashboard: completion %, last activity, checkpoints passed, current lesson
- Row Level Security so reps only edit/read their own progress; managers can read team progress

Do **not** put a Supabase service-role key in front-end code.

## Source precedence / v1 conflicts resolved

The v2 document explicitly says it replaces v1, so this MVP uses v2 when the documents conflict. Key examples:

- **Payment / contract sequence:** v1 said contract first; v2 says **payment first → contract → onboarding**.
- **PIF language:** v1 contains stale $8,500 PIF language; v2 uses the current $9,800 flagship pricing and a separate eligible $500 show-up discount rule.
- **Old unit counts:** v2 says use **850+** for Christian; older 200/550/600/650 references are stale.

## Files

- `index.html` — app shell
- `styles.css` — responsive Tabelingo-inspired UI
- `curriculum.js` — lesson paths, glossary, SOP index and resources
- `app.js` — progress, locking, quizzes, test-out challenges, resume logic
- `service-worker.js` / `manifest.json` — PWA support
- `vercel.json` — Vercel static config

## Demo login

This static MVP includes a client-side login gate:

- Username: `admin`
- Password: `freesample`

The session is remembered locally in the browser until the user signs out. Because this is a static front-end demo, these credentials are not secure access control; use Supabase Auth or another server-side authentication layer before using this for sensitive/internal-only content.
