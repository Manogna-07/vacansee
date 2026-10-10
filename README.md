# Vacansee

A bilingual (English / Telugu) job portal connecting job seekers and employers across India, built for the Indian rural and semi-urban context.

## Tech Stack
- **Frontend**: React 19 + Vite
- **Styling**: Tailwind CSS
- **Routing**: React Router v6
- **Backend / Auth / DB**: Supabase (Postgres + Auth + Storage)
- **Icons**: Lucide React
- **i18n**: Custom LanguageContext (English + Telugu)
- **Voice**: Browser Web Speech API (SpeechRecognition + SpeechSynthesis)

## Getting Started

### 1. Install dependencies
```bash
npm install
```

### 2. Configure Supabase (required for auth, jobs, applications)
```bash
cp .env.example .env
# Edit .env and add your Supabase project URL and anon public key
```

The `.env` file must be in the project root, beside `package.json` and `vite.config.js`:
```dotenv
VITE_SUPABASE_URL=https://your-project-ref.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-public-key
```
On macOS in VS Code, open the extracted project folder (the folder containing `package.json`),
copy `.env.example` to `.env`, and replace both placeholders with values from the Supabase
dashboard under **Project Settings → API**. Use the browser-safe **anon public** or supported
publishable key, never the service-role key. Vite reads `.env` only when the dev server starts,
so stop and restart `npm run dev` after creating or changing it. The validator trims whitespace,
accepts hosted `https://*.supabase.co` URLs and local `http://localhost`/`127.0.0.1` URLs, and
rejects blank, placeholder, or malformed values. When configuration is genuinely missing or
invalid, the application intentionally shows “Supabase is not configured” rather than hiding the
warning or bypassing authentication.
That warning is a configuration check, not an authentication bypass. The Phase 6 ZIP contains
only `.env.example`; real credentials are intentionally excluded.

Never put a Supabase service-role key or a paid translation API secret in frontend/Vite variables;
`VITE_*` values are shipped to the browser.

### 3. Set up the database
Run these files, in order, in the **Supabase SQL Editor** of an authorized project:
1. `supabase/setup.sql` — tables, RLS policies, auth trigger.
2. `supabase/upgrade_v2.sql` — links jobs to employer profiles (needed for job lists to load),
   plus follow, notifications and stored translations. Safe to run more than once.
3. `supabase/fix_auth_v3.sql` — creates missing profile rows (fixes "Welcome back, there!"), lets employers
   see their applicants' names, and allows salaries with paise. Safe to run more than once.
4. `supabase/security_hardening_v4.sql` — forward-only security migration that narrows role and ownership
   policies, protects employer contact information, restricts editable columns, and enforces eligible
   applications. Review its preflight checks against the target schema before applying it; do not run it
   against production without a separate approved rollout. Disposable pgTAP assertions are in
   `supabase/tests/security_hardening_v4.pgtap.sql`.

The application does not apply SQL automatically. Database setup and migration execution require an
authorized operator; validate the security migration in a disposable test project first.

### 4. Run locally
```bash
npm run dev
# Open http://localhost:5173
```

### 5. Build for production
```bash
npm run build
```

## Follow employers & notifications
- Job seekers press **Follow** on a job's employer card. The follower count is public; who follows is private.
- When a followed employer publishes a job (or re-publishes a paused one), a database trigger
  creates a notification for each follower. Nobody can create notifications from the browser.
- The bell in the header shows an unread badge and updates live (Supabase Realtime is enabled for the
  `notifications` table by `upgrade_v2.sql`). Followed employers are listed under **Following**.
- These are in-app notifications. Email/SMS/push are not included.

## English ↔ Telugu translation of job listings
- When an employer publishes a job, its title, description, responsibilities, skills and experience are
  translated to the other language (English → Telugu, or Telugu → English if they wrote in Telugu) and
  stored in `jobs.translations`. Seekers see it in their chosen language, with a "Show original" toggle.
- Jobs without a stored translation (older jobs, or the service was unavailable) are translated when opened
  and cached in the browser.
- Telugu keywords also match stored Telugu titles in search.
- Translation uses the free **MyMemory** API: no key, but a daily character limit per visitor. Set
  `VITE_TRANSLATE_EMAIL` in `.env` to raise it. Machine translation can be wrong, so the UI says so.
  For production, swap `translateChunk()` in `src/services/translateService.js` for a paid API
  (Google Cloud Translation / Azure) — nothing else needs to change.

## Security and validation notes
- Public browsing requests only `published` jobs. Supabase RLS remains the authoritative control; client-side
  route protection is not a replacement for database authorization.
- The project does not contain a service-role key. Only the Supabase URL, anon key, and optional MyMemory
  contact parameter are expected in `.env`.
- Run `npm test`, `npm run lint`, `npm run build`, and `npm audit` for local checks. Do not use `npm audit fix`
  blindly; review upgrades because the current audit reports transitive vulnerabilities in the Vite/Tailwind
  toolchain and a direct React Router advisory.
- This audit does not connect to or modify a live Supabase project. Live authentication, RLS, browser microphone,
  speech, responsive layout, and realtime checks remain unverified without an authorized test environment.

## Project Structure
```
src/
├── pages/
│   ├── auth/         # Login, Register, Forgot/Reset Password
│   ├── seeker/       # Dashboard, Profile, Saved Jobs, My Applications
│   ├── employer/     # Dashboard, Profile, Post Job, Manage Jobs, Applicants
│   ├── HomePage.jsx
│   ├── FindJobsPage.jsx
│   └── JobDetailsPage.jsx
├── components/       # JobCard, JobSearchBar, Header, Footer, etc.
├── layouts/          # MainLayout
├── hooks/            # useAuth (Supabase auth + profile)
├── i18n/             # translations.js + LanguageContext
├── services/         # jobs, applications, profiles, savedJobs, follow, notifications, translate
├── routes/           # ProtectedRoute, RoleBasedRoute
└── lib/              # supabase.js client
supabase/
├── setup.sql         # DB schema + baseline RLS policies
├── upgrade_v2.sql    # employer link fix, follow, notifications, translations
├── fix_auth_v3.sql   # missing profiles, applicant names, salary paise
└── security_hardening_v4.sql # forward-only role, ownership, grants, and privacy hardening
```

## Features
- 🔐 Auth: Register (seeker/employer), Login, Forgot & Reset Password
- 💼 Job Seeker: Search jobs, apply with cover letter, save jobs, track applications
- 🏢 Employer: Post/edit/pause/close jobs, review applicants, update application status
- 🌐 Bilingual: English + Telugu (switch at any time)
- 🎙 Voice: Search by voice, read job descriptions aloud, dictate job postings
- 📱 Responsive: Mobile-first design


## Telugu text, fonts and read-aloud
- Fixed page text is translated by the dictionary in `src/i18n/phrases.js` (applied by `AutoTranslate.jsx`).
  To fix or add a Telugu phrase, edit/add a line there. Text people type (names, job titles) is left alone.
- The Telugu font is Noto Sans Telugu (loaded in `src/index.css`).
- Speaker buttons next to job titles read them aloud; the blue **Read this page** button reads the whole page
  (or the text you have selected). Telugu voices need "Google Text-to-speech" on Android.
- Salary boxes accept paise (e.g. `12500.50`). Category / industry lists have an **Other** choice where people can
  type (or speak) their own.
