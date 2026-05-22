# local-services

Small, practical Docker Compose recipes for running common local services.

## What this repository is

A simple collection of self-contained service folders. Each service can be started, stopped, and reset independently with Docker Compose.

## What this repository is not

- Not a DevOps platform
- Not a lab environment
- Not a framework or custom tooling stack

## Available services

| Service | Path | Default port(s) | Start command |
|---|---|---|---|
| Redis | `services/redis` | `6379` | `cd services/redis && cp .env.example .env && docker compose up -d` |
| MySQL | `services/mysql` | `3306` | `cd services/mysql && cp .env.example .env && docker compose up -d` |
| PostgreSQL | `services/postgres` | `5432` | `cd services/postgres && cp .env.example .env && docker compose up -d` |
| Azurite | `services/azurite` | `10000, 10001, 10002` | `cd services/azurite && cp .env.example .env && docker compose up -d` |
| LocalStack | `services/localstack` | `4566` | `cd services/localstack && cp .env.example .env && docker compose up -d` |

## How to run a service

1. Change into a service directory under `services/`.
2. Copy `.env.example` to `.env`.
3. Start the service:

```bash
docker compose up -d
```

## How to stop a service

From the same service directory:

```bash
docker compose down
```

## How to reset service data

From the same service directory:

```bash
docker compose down -v
```

This removes containers and named volumes for that service.

## Safety note

These configurations are for **local development only**. Do not use them as-is in production.
