# Afintrix Forms

White-labeled deployment customized for **Afintrix** (forked from the OpnForm open-source form builder).

This repository contains:

- `client/` — Nuxt 3 frontend
- `api/` — Laravel API

## Local development (Docker)

Use the dedicated local compose file (does not modify the stock `docker-compose.yml` or `docker-compose.dev.yml`):

**One-time on the host** (Laravel dependencies; required because `./api` is bind-mounted):

```bash
cd /path/to/OpnForm/api
composer install
```

Then:

```bash
cd /path/to/OpnForm
docker compose -f docker-compose.local.yml up --build
```

On **Fedora / RHEL with SELinux**, the compose file labels mounts with `:z` so containers can read your project files.

- Frontend: [http://localhost:3000](http://localhost:3000)
- API: [http://localhost:8000](http://localhost:8000)
- PostgreSQL on host port **5433** (user/database/password default to `afintrix`)

Environment for this stack lives in **`.env.local`**. Adjust secrets before any non-local use.

On first self-hosted run, complete setup at `/setup` when prompted.

## Manual install (without Docker)

- **Client:** `cd client && npm install && npm run dev`
- **API:** `cd api && composer install` — see `api/.env.example` for configuration.

## License

The upstream project is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**. See the `LICENSE` file in this repository. Enterprise-only code under `api/app/Enterprise/` remains subject to its separate license terms where applicable.
