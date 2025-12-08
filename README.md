
# AIMAC — "he's that guy"

AIMAC is a focused dashboard interface for sales teams that surfaces performance, bidding analytics, risk monitoring, and audit analysis — built with a modern React + Next.js stack and accessible UI primitives.

![AIMAC Featured](/assets/featured.png)
![AIMAC Logo](/assets/logo.svg)

Badges
- Next.js • React • TanStack Query • Convex • Radix UI • Base Web • Tailwind CSS • Redis • AWS S3 • Cloudflare R2

Table of contents
1. About
2. Key features
3. Tech stack
4. Quick start
5. Environment variables
6. Project structure (suggested)
7. Assets: logo & featured image
8. Deployment & notes
9. License & contact

About
AIMAC (he's that guy) is a dashboard app that helps sales and bidding teams measure, monitor, and act on the metrics that matter. It focuses on time-series analytics, risk scoring, competition insights, and audit-ready KPIs — surfaced in a clear, accessible UI.

Key features (metrics & reports)
- Inherent risk
  - Risk scenarios over time, grouped by risk level (Low / Medium / High)
- Quote-to-Deal ratio
  - Number of quotes compared to total deal size for a given month
- Bidder density
  - Competition level measured by the number and size of bidders over time
- ESG impact
  - Evaluation of addressed ESG criteria in biddings over time

Audit & operational analysis
- Lead-to-Quote ratio
- Project load (active projects per period / capacity)
- Win probability (calibrated by historical patterns & current signals)

Tech stack (concise)
- Framework: `Next.js` + `React`
- Data fetching / caching: `@tanstack/react-query` (TanStack)
- Backend & serverless data layer: `Convex`
- UI primitives: `Radix UI` + `Base Web (BaseUI)`
- Styling: `Tailwind CSS`
- Caching / ephemeral metrics: `Redis`
- Object storage: `AWS S3` (primary) and `Cloudflare R2` (alternative)
- Icons / accessible controls: Radix patterns / Icon button components

Quick start (local)
1. Install dependencies:
   - `npm install` or `pnpm install` or `yarn`
2. Create environment variables (see next section).
3. Start development server:
   - `npm run dev` (or the script your project uses)
4. Open `http://localhost:3000` and sign in to your dev account / seed data.

Environment variables (example keys)
- `NEXT_PUBLIC_APP_NAME` — app display name ("AIMAC")
- `NEXT_PUBLIC_FEATURED_IMAGE` — `/assets/featured.png`
- `CONVEX_URL` — Convex deployment URL
- `CONVEX_KEY` — Convex key for serverless operations
- `REDIS_URL` — Redis connection string (e.g. `redis://:password@host:6379/0`)
- `AWS_ACCESS_KEY_ID` / `AWS_SECRET_ACCESS_KEY` / `AWS_REGION` / `S3_BUCKET`
- `R2_ACCOUNT_ID` / `R2_ACCESS_KEY_ID` / `R2_SECRET_ACCESS_KEY` / `R2_BUCKET`
- Optional: `SENTRY_DSN`, `LOG_LEVEL`, `FEATURE_FLAGS`

Suggested project structure
- `app/` or `pages/` — Next.js routes & pages
- `components/` — UI components (charts, KPI cards, tables)
- `hooks/` — TanStack Query hooks like `useQuotesTrend`, `useBidderDensity`, `useRiskScenarios`
- `lib/` — Convex / Redis / storage wrappers
- `styles/` — Tailwind config, global CSS
- `assets/` — `logo.svg`, `featured.png`, and other images
- `scripts/` — utilities for seeding or data migration
- `docs/` — design tokens, API notes, and onboarding docs

Assets: logo & featured image
- Logo: place an SVG at `assets/logo.svg`. Prefer vector for crisp rendering.
- Featured image: `assets/featured.png` recommended at 1200×630 for social previews.
- When committing new featured images, version filenames (e.g. `featured-v2.png`) to avoid CDN cache issues.

UI & accessibility notes
- Use Radix primitives (dialog, tooltip, dropdown) for accessible interactions.
- Ensure KPI chips and risk badges meet color-contrast guidelines.
- Provide keyboard navigation and ARIA labels for chart drill-ins and icon buttons.

Data & caching guidance
- Use Convex for your primary dataset and serverless functions (time-series ingestion, heavy aggregations).
- Use TanStack Query on the client for caching, background refetch, and optimistic updates.
- Use Redis for rolling counters, leaderboards, short-lived aggregates (bidder density), and rate-limiting.
- Persist large artifacts or exported reports to S3 and optionally mirror to Cloudflare R2 for cost-effective egress.

Deployment notes (concise)
- Deploy the frontend on Vercel or any platform that supports Next.js.
- Keep Convex and Redis credentials in encrypted env vars in your deployment provider.
- Use CI to run tests and production builds; invalidate CDN caches after major asset updates.

Contributing
- Please open issues or PRs with clear descriptions, screenshots, and relevant environment details.
- Follow the branching and PR conventions your team prefers (e.g., branch from `main`, open PR to `develop`).

License & contact
- License: MIT (or pick your license)
- Contact / product inquiries: contact@aimac.app

That's it — this README gives you a focused, copy-ready overview for the AIMAC project. Add screenshots, a short demo GIF, and your actual `assets/logo.svg` and `assets/featured.png` to complete the repository's visual identity.

