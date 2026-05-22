# MySQL

## Purpose

Run a local MySQL server with a default database and non-root application user.

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

- Host: `${MYSQL_PORT}` (default `3306`)
- Container: `3306`

## Default credentials

- Root user: `root`
- Root password: `MYSQL_ROOT_PASSWORD`
- App database: `MYSQL_DATABASE`
- App user: `MYSQL_USER`
- App password: `MYSQL_PASSWORD`

## Basic connection example

```bash
mysql -h 127.0.0.1 -P 3306 -u app_user -plocal-app-password app_db
```

## Data reset command

```bash
docker compose down -v
```

## Notes and limitations

- This setup is intended for local development only.
- Data persists in the named volume `mysql-data` until you reset it.
