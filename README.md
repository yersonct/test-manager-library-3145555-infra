# Manager Library Local Infrastructure

This repository contains the local service composition only. PostgreSQL starts **empty**; Laravel business migrations run only when explicitly requested. The frontend, API, public website, and demo seeder remain in their respective repositories.

## Requirements and setup

Install Docker Desktop with Docker Compose v2. Clone all six repositories as sibling directories under the same parent directory.

1. Copy this repository's `.env.example` to `.env`. Example values are for local development only.
2. Copy `test-manager-library-3145555-api/.env.example` to `test-manager-library-3145555-api/.env`.
3. In the API `.env`, set a random `JWT_SECRET` with at least 32 characters and configure `ADMIN_USERNAME` and `ADMIN_PASSWORD`. Do not commit these values.
4. Generate Laravel's key, which is persisted in the mounted API `.env`: `docker compose run --build --rm api php artisan key:generate --force`.
5. From this repository directory, run `docker compose up --build`.
6. The API is available at `http://localhost:8000`, the React app at `http://localhost:5173`, and the public website at `http://localhost:8080`. PostgreSQL does not publish a host port.
7. Create the six business tables and categories with `docker compose exec api php artisan migrate --force`. The Laravel HTTP application provisions the administrator from environment credentials after migration.
8. To load fictional demo records, run `docker compose --profile seed run --rm seed`. This writes through the API; it cannot create overdue loans because the current contract does not allow setting a due date in the past.

The `db` service uses a persistent volume. To intentionally reset the local database, stop the stack and remove that volume with `docker compose down -v`. This permanently deletes local database data.

PostgreSQL is not exposed on a host port. Replace all example credentials before using any shared or public environment.
