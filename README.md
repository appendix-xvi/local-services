# local-services

Ready-to-use Docker Compose recipes for common local development services.

Clone the repository, enter a service folder, copy the sample environment file, and start the service. No framework, no custom platform, no unnecessary abstraction.

## Why this exists

Local development often needs the same supporting services again and again: Redis, databases, cloud emulators, queues, object storage, and similar tools.

This repository keeps those setups in one place so you do not have to search for a new Compose file every time.

## Quick start

```bash
git clone https://github.com/appendix-xvi/local-services.git
cd local-services/services/redis
cp .env.example .env
docker compose up -d
```

Check Redis:

```bash
redis-cli -h 127.0.0.1 -p 6379 -a local-redis-password ping
```

Expected response:

```text
PONG
```

Stop the service:

```bash
docker compose down
```

Reset the service data:

```bash
docker compose down -v
```

## Available services

| Service | Path | Default port(s) | Good for | Start command |
|---|---|---:|---|---|
| Redis | `services/redis` | `6379` | Cache, sessions, queues | `cd services/redis && cp .env.example .env && docker compose up -d` |
| MySQL | `services/mysql` | `3306` | Relational database testing | `cd services/mysql && cp .env.example .env && docker compose up -d` |
| PostgreSQL | `services/postgres` | `5432` | Relational database testing | `cd services/postgres && cp .env.example .env && docker compose up -d` |
| Azurite | `services/azurite` | `10000`, `10001`, `10002` | Azure Storage emulation | `cd services/azurite && cp .env.example .env && docker compose up -d` |
| LocalStack | `services/localstack` | `4566` | AWS service emulation | `cd services/localstack && cp .env.example .env && docker compose up -d` |

Each service folder includes:

- `compose.yml`
- `.env.example`
- `README.md`

## Repository structure

```text
local-services/
├── AGENTS.md
├── CONTRIBUTING.md
├── PROMOTION.md
├── README.md
└── services/
    ├── azurite/
    ├── localstack/
    ├── mysql/
    ├── postgres/
    └── redis/
```

## Requirements

- Docker
- Docker Compose v2
- Optional CLI clients for testing, such as `redis-cli`, `mysql`, `psql`, `aws`, or Azure SDK tools

## Design principles

- One service per folder
- Prefer Docker Compose over custom Dockerfiles
- Keep defaults usable for local development
- Keep each service isolated with its own named volume
- Avoid company-specific endpoints, credentials, or internal assumptions
- Do not turn this into a framework, platform, or lab environment

## Roadmap

Planned candidates:

- [ ] MinIO
- [ ] Kafka
- [ ] RabbitMQ
- [ ] MongoDB
- [ ] Keycloak
- [ ] Elasticsearch / OpenSearch
- [ ] Vault
- [ ] Mailpit
- [ ] NATS
- [ ] Prometheus + Grafana

## Safety note

These configurations are for **local development only**. Do not use them as-is in production.

## Contributing

Small, practical service recipes are welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md) for the expected structure and rules.
