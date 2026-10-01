# Active Context

## Project Status
- Next.js application scaffolded at root directory.
- Using `bun` for package management and script execution.
- Phase 1 (MVP) in progress: Auth, Hierarchy, Residents, Announcements.

## Tech Stack & Tools
- **Framework:** Next.js (App Router), React 19.
- **Styling/UI:** Tailwind CSS v4, `shadcn/ui`.
- **Package Manager:** Bun.
- **Backend/DB Strategy:**
  - **Current (Offline First):** In-memory/local mock store utilizing `faker` for data generation matching Supabase schema.
  - **Future (Production):** Supabase (PostgreSQL, Auth, RLS).

## Current Decisions
- Development is strictly offline-first. Mock data structures mirror the `docs/DATABASE.md` definitions.
- Admin dashboard, RBAC interfaces, and resident lists are currently being scaffolded with mock data.
- The `tmpapp` scaffold has been extracted to the root folder.

## Mock Schema Mapping (vs Supabase)
- **Users:** Mocked with `faker.person`, matching `users` and `roles`.
- **Administrative Units:** Mocked hierarchy (RT/RW/Desa).
- **Residents:** Mocked with household relations.
