# Azurite

## Purpose

Run a local Azure Storage emulator (Blob, Queue, and Table APIs).

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

- Blob: `${AZURITE_BLOB_PORT}` (default `10000`)
- Queue: `${AZURITE_QUEUE_PORT}` (default `10001`)
- Table: `${AZURITE_TABLE_PORT}` (default `10002`)

## Default credentials

Azurite development account:

- Account name: `devstoreaccount1`
- Account key: `Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==`

Default development connection string:

```text
DefaultEndpointsProtocol=http;AccountName=devstoreaccount1;AccountKey=Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==;BlobEndpoint=http://127.0.0.1:10000/devstoreaccount1;QueueEndpoint=http://127.0.0.1:10001/devstoreaccount1;TableEndpoint=http://127.0.0.1:10002/devstoreaccount1;
```

## Basic connection example

Use the connection string above in Azure SDK clients (with your local ports).

## Data reset command

```bash
docker compose down -v
```

## Notes and limitations

- This setup is intended for local development only.
- Emulator behavior may differ from real Azure Storage.
- Data persists in the named volume `azurite-data` until you reset it.
