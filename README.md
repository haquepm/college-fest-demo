# College Fest Demo

A dedicated demo environment for a college fest management platform.

## Current status

This repository is the application source for the College Fest Demo Vercel project. The Supabase project is:
- Project ref: `bczumadufjquimjlydev`
- Region: `ap-south-1` (Mumbai)
- Intended use: demo-only data; never import a real college roster here.

## Product scope

The platform should demonstrate the complete fest workflow:

1. **Institution setup** — create a fest, academic departments, faculty accounts and permissions.
2. **Student onboarding** — bulk upload students from CSV/XLSX with validation and duplicate detection.
3. **Groups** — create groups by department, auto-shuffle students fairly, or combine selected departments into a group. Support competitions between groups or departments.
4. **Programme items** — configure individual and group competitions, registration rules, eligibility, schedules and capacity.
5. **Registration** — student self-registration for individual and group events; coordinators can review and download their group registrations.
6. **Chest numbers** — generate unique chest numbers and QR codes per candidate/entry.
7. **Stage reporting** — stage managers scan QR codes; reported candidates become visible in the relevant judges' workspace.
8. **Judging** — create per-item judging criteria, enter marks, validate totals and maintain judge submissions.
9. **Results** — fest convenor reviews submitted scores and explicitly publishes results.
10. **Live scoreboard** — update group and department standings only when results are published.
11. **Certificates** — generate participation and 1st/2nd/3rd place achievement certificates as PDFs; support bulk generation and student download/sharing.
12. **Paperless evidence** — maintain downloadable digital records and reports to support the college's green-campus documentation.

## Demo data rules

- Use only fictional names, student IDs, phone numbers and email addresses.
- Label the institution, fest, records and all logins visibly as **DEMO**.
- Never use live student personal data, production credentials or real payment details.
- Seed a coherent demo dataset (for example: 5 departments, 300 students, 4 mixed groups, faculty coordinators, 25 items, registrations, QR credentials, sample judge scores and a small set of published results).
- Use an explicit seed version and an idempotent seed script so repeated runs do not duplicate data.
- Provide a reset path restricted to the demo administrator.

## Suggested roles

- Demo administrator / fest convenor
- Group coordinator
- Stage manager
- Judge
- Student
- Public scoreboard viewer

Role permissions must be enforced server-side and in database policies, not only by hiding UI controls.

## Supabase safety

- Keep the Supabase service-role/secret key server-side only. Never prefix it with `NEXT_PUBLIC_`.
- Enable Row Level Security on every exposed application table.
- Scope every record to its demo institution/fest and verify role-based access in policies.
- Use a publishable/anon key only in the browser.
- Do not create public signup or shared demo credentials until a safe authentication flow and rate limits are implemented.

## Configuration

Expected frontend variables (names may be adapted to the selected framework):
- `NEXT_PUBLIC_SUPABASE_URL`
- `NEXT_PUBLIC_SUPABASE_ANON_KEY` (or current Supabase publishable key)

Server-side only:
- `SUPABASE_SERVICE_ROLE_KEY` (or current secret key)

Do not commit actual values to Git. Configure them as encrypted Vercel environment variables.

## Next implementation milestone

Build the application shell, migrations, secure auth and role model first. Then implement demo seed data against the actual schema, test core workflows end-to-end, and deploy the functioning demo. The initial repository deployment is only a starter placeholder until these source files exist.
