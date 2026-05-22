# Redis

## Purpose

Run a local Redis instance with password protection and append-only persistence enabled.

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

- Host: `${REDIS_PORT}` (default `6379`)
- Container: `6379`

## Default credentials

- Password: value of `REDIS_PASSWORD` in `.env`

## Basic connection example

```bash
redis-cli -h 127.0.0.1 -p 6379 -a local-redis-password ping
```

Expected response: `PONG`.

## Data reset command

```bash
docker compose down -v
```

## Notes and limitations

- This setup is intended for local development only.
- Data persists in the named volume `redis-data` until you reset it.
