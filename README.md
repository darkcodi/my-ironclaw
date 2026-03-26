# ironclaw-coolify

IronClaw + PostgreSQL + pgvector for Coolify.

## Deploy

1. Create a new resource in Coolify from this repo
2. Choose the **Docker Compose** build pack
3. Assign your domain to the `ironclaw` service
4. Set `OPENAI_API_KEY`
5. Deploy

## Notes

- No local `.env` file is needed
- Postgres stays internal to the stack
- Coolify generates the database password and app secrets automatically
- IronClaw is exposed on internal port `3000`

## Optional variables

- `IRONCLAW_REF` default: `v0.20.0`
- `IRONCLAW_REPO` default: `https://github.com/nearai/ironclaw.git`
- `LLM_BACKEND` default: `openai`
- `SANDBOX_ENABLED` default: `false`
- `RUST_LOG` default: `ironclaw=info`
