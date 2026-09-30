# Security

1. Row-Level Security (RLS) in PostgreSQL is mandatory. Frontend checks are insufficient.
2. Data Sovereignty: Source-owned vs LocalHost-owned vs Derived. Don't overwrite source data blindly.
3. Audit Logs: Record `actor, action, target, timestamp, scope, before, after` for all admin actions.
4. Least privilege. Tenant isolation by `organization_id`.