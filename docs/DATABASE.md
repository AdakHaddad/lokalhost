# Database Schema

Core entities (PostgreSQL via Supabase):
`organizations`, `administrative_units`, `administrative_unit_memberships`, `users`, `roles`, `permissions`, `households`, `residents`, `services`, `facilities`, `requests`, `request_responses`, `contributions`, `verifications`, `announcements`, `forum_posts`, `forum_comments`, `conversations`, `messages`, `notifications`, `data_sources`, `data_source_mappings`, `sync_jobs`, `sync_records`, `audit_logs`

Rule: All relevant entities MUST reference `administrative_unit_id` for scope-based RLS.