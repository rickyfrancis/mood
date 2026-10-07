# mood

A private journal built with Next.js. Write entries, have them saved as you
type, and come back to them later.

## What it does

- Write and edit journal entries
- Entries save automatically while you type, so there is no save button
- Each entry has its own page
- Sign in and sign up handled by Clerk
- New users land on a setup route that creates their record before the dashboard

## Stack

| Area | Choice |
| --- | --- |
| Framework | Next.js, App Router |
| Language | TypeScript |
| Database | Prisma |
| Auth | Clerk |
| Styling | Tailwind |
| Autosave | react-autosave |

## Structure

- `app/(dashboard)/journal` lists entries, `journal/[id]` is a single entry
- `app/api/journal` holds the create and update routes
- `app/new-user` runs once after sign up to create the user record
- `utils/` holds the database client, auth helpers and API helpers

## Running it locally

```bash
npm install
cp example.env .env
```

Fill in the values:

- `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` and `CLERK_SECRET_KEY` from a Clerk app
- `DATABASE_URL` for your database

Then:

```bash
npx prisma migrate dev
npm run dev
```

## Status

The journal works. There is a `utils/ai.ts` file that is currently empty: the
original plan was to analyse entries and show mood over time, and that part was
never built. Treat this as a journal app, not an AI one.
