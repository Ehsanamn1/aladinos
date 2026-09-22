# Aladdin OS

Central AI operations, automation and business orchestration control plane.

## Current release

v1.1.0 — Control Center + Agent Runtime + Workflows + persistent Task Queue + Autopilot Scheduler + Outreach + CRM + Finance + Inventory + Memory + MCP + connector boundaries + signed payment webhook handling.

## Architecture

- FastAPI control plane
- SQLAlchemy + PostgreSQL production path / SQLite development path
- Dedicated worker process for persistent tasks
- Dedicated scheduler process for interval-based autopilot
- MCP tool gateway
- Telegram / WhatsApp / WooCommerce / SMTP / OpenAI-compatible provider adapters
- Explicit approval gates for consequential operations

## Source bundle

The complete source snapshot is stored in `aladdin-os-source.tgz`. It is the exact tested source tree for v1.1.0, excluding generated local databases, test caches and the large design PNG assets. Extract it into a clean directory with `tar -xzf aladdin-os-source.tgz`.

SHA-256: `6e7b918d0358b46a694598b99350fc596c542e7923c2ef87ea57251eb13e537d`

## Verification

The release snapshot passed 12 automated tests, Python compilation, JavaScript syntax validation, clean Alembic migration to 33 tables, and HTTP smoke tests.

## Production

See `docs/PRODUCTION_RUNBOOK.md`, `docs/ARCHITECTURE.md`, and `docs/SECURITY.md` in the source bundle. Real provider credentials and production secrets must be supplied by the operator; the application does not fake successful external actions when credentials are missing.
