# Architecture

Serverless-first. Multi-tenant. Hierarchical.
Stack: Next.js, TypeScript, Supabase (PostgreSQL, Auth, Storage, Realtime, Edge Functions).

## Data Flow
[Existing Sources: Excel/CSV/DB/API] -> [Adapter Layer] -> [Schema Mapping] -> [LocalHost Canonical DB] -> [RLS/Access Control] -> [Client]