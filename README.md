## 👋 Welcome to tandoor 🚀

Recipe manager and meal planner

## 📋 Description

Recipe manager and meal planner

## 🚀 Services

- **tandoor**: vabene1111/recipes:latest
- **tandoor-db**: postgres:15-alpine

## 📦 Installation

### Option 1: Quick Install

```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/tandoor/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone

```bash
git clone "https://github.com/composemgr/tandoor" ~/.local/srv/docker/tandoor
cd ~/.local/srv/docker/tandoor
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr

```bash
composemgr install tandoor
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=...
BASE_HOST_NAME=...
APP_SECRET_KEY=...
DB_USER_NAME=...
DB_USER_PASS=...
DB_CREATE_DATABASE_NAME=...
```

See `docker-compose.yaml` for the complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

The stack also boots with the inline defaults in `docker-compose.yaml`, so no
env file is strictly required.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64362` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

The proxy variants publish no host ports; the app is reached only through the
proxy network.

## 🌐 Access

- **Web Interface**: <http://172.17.0.1:64362>

## 📂 Volumes

- `./volumes/data/tandoor/staticfiles` - Collected static files
- `./volumes/data/tandoor/mediafiles` - Recipe images and attachments
- `./volumes/db/postgres/tandoor` - Postgres database

## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

## 🔍 Logging

```shell
docker compose --env-file .env logs -f tandoor
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose --env-file .env pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
