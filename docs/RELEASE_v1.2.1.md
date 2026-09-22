# Aladdin OS v1.2.1 — Operational Hardening Release

## Included

- Persistent task execution with retries, orphan recovery and execution-time agent policies.
- CRM/discovery deduplication, lead scoring/activity history and outreach suppression/rate limits.
- Telegram, WhatsApp, WooCommerce and generic payment webhook idempotency/signature boundaries.
- Financial ledger, payment posting and reconciliation endpoints.
- Workforce/Guild queue, connector health history and Prometheus-style operational metrics.
- PBKDF2 password hashing, password-change flow, optional TOTP 2FA, rotating CSRF tokens and DB-backed login rate limiting.
- Trusted-host enforcement and production fail-closed webhook configuration checks.
- PostgreSQL/Alembic schema with 40 application tables at revision `b71c3a2d004b`.
- Docker Compose production topology with PostgreSQL, migration job, web, worker, scheduler, internal MCP and optional Caddy edge TLS.
- Railway deployment manifest and backup scripts for PostgreSQL/SQLite.
- Readiness probe at `/api/ready` and operational metrics endpoints.

## Verification

- 19/19 automated tests pass.
- Fresh Alembic migration from an empty SQLite database reaches `b71c3a2d004b` and creates 40 application tables.
- Python compile checks pass.
- JavaScript syntax check passes.
- `make smoke` passes and reports 79 registered routes.
- Live Uvicorn smoke: `/api/health` and `/api/ready` both returned HTTP 200.
- Docker Compose structure parses as YAML and the production environment mapping was reviewed.

## Environment-dependent activation

The software does not invent third-party credentials or remote service success. Production activation still requires operator-owned values for the services actually used: AI provider, Telegram, Meta/WhatsApp, WooCommerce, payment provider, SMTP and any external object storage/market-data registries.

Docker Engine was not available in the build environment, so full container startup/inter-container networking was not executable here.
