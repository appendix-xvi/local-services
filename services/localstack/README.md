# LocalStack

## Purpose

Run a local AWS cloud emulator for common services.

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

- Gateway: `${LOCALSTACK_PORT}` (default `4566`)

## Default credentials

No real AWS credentials are required for local emulation. Use any placeholder values in your shell when needed.

## Basic connection example

```bash
aws --endpoint-url=http://localhost:4566 s3 mb s3://demo-bucket
aws --endpoint-url=http://localhost:4566 s3 ls
aws --endpoint-url=http://localhost:4566 sqs create-queue --queue-name demo-queue
```

## Data reset command

```bash
docker compose down -v
```

## Notes and limitations

- This setup is intended for local development only.
- LocalStack behavior may differ from real AWS services.
- Docker socket is mounted to support services (for example Lambda) that rely on Docker execution.
- Data persists in the named volume `localstack-data` until you reset it.
