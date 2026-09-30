# API

Domains (Next.js server-side / Supabase Edge Functions):
- `/api/auth`
- `/api/users`, `/api/residents`, `/api/households`, `/api/administrative-units`
- `/api/services`, `/api/facilities`, `/api/requests`, `/api/contributions`, `/api/announcements`
- `/api/forum`, `/api/notifications`, `/api/data-sources`, `/api/sync`, `/api/admin`

Rule: Prefer direct Supabase client + RLS for standard CRUD. Use API only for privileged actions.