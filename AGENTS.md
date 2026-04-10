# Brandisky Codex Setup

## Workspace shape

- Main product code lives in [app](/D:/Musafirwithcamera/app).
- Treat the repo root as coordination space, but do most coding work inside `D:\Musafirwithcamera\app`.
- The public Brandisky landing page is [app/app/brandisky/page.jsx](/D:/Musafirwithcamera/app/app/brandisky/page.jsx).
- The root route re-exports that page from [app/app/page.jsx](/D:/Musafirwithcamera/app/app/page.jsx).

## Brandisky product map

- `Brandisky` is the service-led creator network.
- `Musafir` is the expression-led artist network.
- `Brandisky OS` is the admin and operations surface at `/brandisky-os`.
- Public creator directory data comes from Notion-backed APIs, especially `/api/creators/get`.

## Commands

- Install: `npm install`
- Dev server: `npm run dev`
- Production build: `npm run build`
- Lint: `npm run lint`
- Codex environment check: `npm run codex:brandisky`
- Notion verification: `npm run notion:verify`
- Notion setup: `npm run notion:setup`

Run commands from `D:\Musafirwithcamera\app`.

## Environment expectations

For the Brandisky project to behave fully in local development, these values matter most:

- `NOTION_API_KEY`
- `NOTION_CREATORS_DB_ID`
- `NOTION_LEADS_DB_ID`
- `NOTION_REVENUE_DB_ID`
- `NOTION_MUSAFIR_DB_ID` or `NOTION_ARTISTS_DB_ID`

If those are missing, `/creators`, `/musafir`, and admin data surfaces can render shell UI but fail to load records.

## Working rules

- Prefer extending the existing Next.js App Router app instead of reviving the old Vite client under `src/`.
- Keep Brandisky-first copy and navigation consistent across landing, creators, join, and admin routes.
- When debugging data-loading issues, check the env/config state before changing UI logic.
- If a directory page is visually fine but shows an empty or error state, inspect the related API route and Notion ids first.

## Quick verification

1. Run `npm run codex:brandisky`
2. Start the app with `npm run dev`
3. Check `/brandisky`
4. Check `/creators`
5. Check `/brandisky-os`

If `/creators` reports missing database ids, fix env vars before changing frontend components.
