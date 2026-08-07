# Nango (self-hosted)

## Run

```sh
cp .env.example .env
# set NANGO_ENCRYPTION_KEY (openssl rand -hex 32) and NANGO_DASHBOARD_PASSWORD
docker compose up -d
```

Dashboard: http://localhost:3003
Connect UI: http://localhost:3009

## Connect a provider

1. Dashboard → Integrations → add provider (e.g. `google`, `github`, `slack`), enter its OAuth client id/secret.
2. Dashboard → Environment settings → copy the secret key.
3. Trigger auth from your app with the [Nango frontend SDK](https://docs.nango.dev/reference/sdks/frontend) (`@nangohq/frontend`) pointed at `NANGO_PUBLIC_CONNECT_URL`, or embed the Connect UI.
4. Use the [backend SDK](https://docs.nango.dev/reference/sdks/node) (`@nangohq/node`) server-side, pointed at `NANGO_SERVER_URL`, to fetch valid access tokens / trigger syncs for a `connectionId`.

## Notes

- `nango-data/` (Postgres volume) is gitignored — don't commit it.
- This is the dev/single-node compose file from upstream Nango. For production, see https://docs.nango.dev/guides/self-hosting/free-self-hosting/overview.
