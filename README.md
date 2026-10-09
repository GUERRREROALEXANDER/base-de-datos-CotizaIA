# base-de-datos-CotizaIA

PostgreSQL 16 database for [CotizaIA](https://github.com/GUERRREROALEXANDER/backend-cotizaIA).

## Contents

| Path | What it is |
|---|---|
| `migrations/V1..V19__*.sql` | Flyway migrations, the source of truth (copied from the backend's `src/main/resources/db/migration`) |
| `schema.sql` | Full schema dump (`pg_dump --schema-only`) after applying all 19 migrations on real Postgres |

## Restore

```bash
createdb -U cotizaia cotizaia
psql -U cotizaia -d cotizaia -v ON_ERROR_STOP=1 -f schema.sql
```

Or let the backend create it: `docker compose up -d` then `./mvnw spring-boot:run` and Flyway applies the migrations on startup.

Verified on 2026-10-09: all 19 migrations applied with no error, and `schema.sql` restores cleanly into an empty database (26 tables, including `flyway_schema_history`).

## Tables

- `agencies`
- `agent_executions`
- `agent_steps`
- `brief_questions`
- `briefs`
- `clauses`
- `clients`
- `contracts`
- `extracted_requirements`
- `notifications`
- `payments`
- `phase_dependencies`
- `phases`
- `proposal_documents`
- `proposal_extras`
- `proposals`
- `proposal_status_changes`
- `quoted_items`
- `rates`
- `requirement_types`
- `roles`
- `schedules`
- `service_catalog`
- `service_categories`
- `users`
