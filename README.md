# ironclaw-compose

Docker Compose setup for IronClaw with PostgreSQL and pgvector.

## Files

- `Dockerfile` builds IronClaw from a pinned upstream git ref
- `docker-compose.yml` starts IronClaw and Postgres
- `docker-entrypoint.sh` writes `~/.ironclaw/.env` and starts IronClaw + Caddy
- `Caddyfile` proxies the public port to the internal app port
- `postgres/init/01-enable-vector.sql` enables pgvector on first database init

## Quick start

1. Copy the example env file

    cp .env.example .env

2. Edit `.env` and set these values

    - `OPENAI_API_KEY`
    - `POSTGRES_PASSWORD`
    - `SECRETS_MASTER_KEY`
    - `GATEWAY_AUTH_TOKEN`
    - `HTTP_WEBHOOK_SECRET`

3. Start the stack

    docker compose up --build -d

4. Open the app

    http://localhost:8080

5. Log in with your `GATEWAY_AUTH_TOKEN`

## Notes

- Public app: `http://localhost:8080`
- Internal gateway runs on `127.0.0.1:3000` inside the container
- Webhook server runs on `0.0.0.0:8081` inside the container
- Postgres is internal only
- pgvector is initialized automatically on first database creation

## Logs

    docker compose logs -f ironclaw
    docker compose logs -f db

## Reset

    docker compose down -v
