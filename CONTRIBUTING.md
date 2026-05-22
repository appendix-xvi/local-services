# Contributing

This repository is intentionally small and practical. A good contribution should make one local service easier to run without adding a framework around it.

## Service folder rules

Every service must live under `services/<service-name>/` and include:

```text
services/<service-name>/
├── .env.example
├── README.md
└── compose.yml
```

Use lowercase folder names. Prefer short, common service names such as `redis`, `postgres`, `localstack`, or `minio`.

## Compose rules

- Prefer official or widely trusted container images.
- Pin a major or minor image version instead of using `latest`.
- Use environment variables from `.env.example` for ports, credentials, and common options.
- Use named volumes for persistent data.
- Keep services isolated unless the service genuinely requires dependencies.
- Avoid host-specific paths.
- Do not add real credentials, cloud profiles, kubeconfig files, tokens, or internal endpoints.

## README rules

Each service README should include:

- Purpose
- Start command
- Stop command
- Default ports
- Default credentials, if any
- Basic connection example
- Data reset command
- Notes and limitations

Keep the README direct and usable. Someone should be able to copy the commands and run the service quickly.

## Example service README shape

````markdown
# Service Name

## Purpose

Run a local instance of ...

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

- Host: `${SERVICE_PORT}` (default `1234`)
- Container: `1234`

## Basic connection example

```bash
example-cli --host 127.0.0.1 --port 1234
```

## Data reset command

```bash
docker compose down -v
```
````

## Scope boundaries

Do not add:

- Kubernetes manifests
- Terraform modules
- Helm charts
- CI/CD pipelines unless they validate this repository itself
- Company-specific configuration
- Multi-service platforms that hide what is running

This is a local service recipe collection, not a DevOps platform or lab framework.
