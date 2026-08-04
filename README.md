# Smart Design — Business Management System

A single-file, self-contained facilities and property management platform: risk-scored job cards, full multi-discipline inspections, compliance & safety checks, contractor on-site tracking, and a live executive dashboard — all in one HTML file with no build step, no server, and no dependencies beyond a browser.

## Open it

`index.html` is completely self-contained. Double-click it, or drag it into any browser tab — nothing to install. It works on desktop, tablet, and phone.

**Sign in:** the login screen accepts any name, department, role, and password combination — this is a front-end demo with no real authentication yet (see **Roadmap** below).

## Design

Deep navy chrome, warm off-white surfaces, hairline borders instead of heavy shadows, and a single precise red accent reserved for primary actions and P1/critical alerts — nothing else competes with it. No gradients, no glow, no decorative color-per-section. The goal was restraint: the same visual language the top-tier SaaS products (Stripe, Linear, Mercury) use, rather than a busier, more decorated look.

## Modules

| Tab | What it does |
|---|---|
| **Dashboard** | Live KPIs (Total, Open, P1 Critical, P2 High, Overdue, Closed, Contractors On-Site), department breakdown with resolution %, category breakdown, and a rolling activity feed |
| **Register** | Every open job card, filterable by priority/category/status/department, sorted by risk score |
| **Log Item** | One page to log a job card: location, issue, action required, a real Risk Scoring engine (Condition × Impact × Urgency → auto-assigned P1/P2/P3 with a suggested due date), assignment, and photo capture (device camera) or upload (gallery) |
| **Archive** | Every closed job card with resolution-time analytics and a speed-tier guide (Excellent → Critical) |
| **Contractors** | On-site contractor tracking: company, contact, scope of work, check-in/check-out, Open/Pending/Closed status |
| **Inspections** | Full multi-discipline walk-through inspections (Room, External, Fencing, Electrical, Plumbing, Fire Safety, Security, Health & Safety), each a simple item/rating/comment checklist. Auto-raises a job card for anything rated Poor |
| **Compliance & Safety Checks** | A single flat checklist covering fire, security, electrical, and general safety equipment — fully editable history, not just create-once |
| **Site Profile** | Business details, buildings, and a real login history audit trail |
| **Reports** | Executive summary generation, CSV export, PDF export (browser print) |

Everything logged, saved, or closed stays in its own history — click into any past record from any module to view it, and edit it if needed.

## Data

All data lives in the browser's memory for the current session only — there is no backend yet. Refreshing or closing the page resets everything. This is intentional for demoing: the app ships with a completely clean slate, no seed data, so it's ready to show a client live.

## Roadmap: moving to Supabase

The data layer was built with this migration in mind — every module (`registerItems`, `inspections`, `complianceChecks`, `contractors`, `loginHistory`) is a flat array of plain, consistently-shaped objects, which maps close to 1:1 onto Postgres tables. The move would involve:

1. Create matching tables in Supabase (one per module above)
2. Replace the in-memory arrays with Supabase queries (`select`/`insert`/`update`)
3. Replace the mock login with Supabase Auth
4. Add row-level security scoped by department/site

## Files

- `index.html` — the application (open this)
- `README.md` — this document
