# PostgreSQL

## Purpose

Run a local PostgreSQL server with a default database and user.

## Start command

```bash
cp .env.example .env
docker compose up -d
```

## Stop command

```bash
docker compose down
```

## Default ports

- Host: `${POSTGRES_PORT}` (default `5432`)
- Container: `5432`

## Default credentials

- Database: `POSTGRES_DB`
- User: `POSTGRES_USER`
- Password: `POSTGRES_PASSWORD`

## Basic connection example

```bash
psql "postgresql://app_user:local-postgres-password@127.0.0.1:5432/app_db"
```

## Data reset command

```bash
docker compose down -v
```

## Notes and limitations

- This setup is intended for local development only.
- Data persists in the named volume `postgres-data` until you reset it.
