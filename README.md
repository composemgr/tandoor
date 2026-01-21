# Tandoor

A self-hosted application for managing tandoor.

## Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/tandoor/main/docker-compose.yaml" | docker compose -f - up -d
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/tandoor" ~/.local/srv/docker/tandoor
cd ~/.local/srv/docker/tandoor
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install tandoor
```

## Configuration

See docker-compose.yaml for environment variables and configuration options.

## Documentation

Check the official project documentation for detailed setup and usage information.
