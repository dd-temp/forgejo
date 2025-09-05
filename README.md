# forgejo (docker compose)

A minimal Forgejo (self-hosted Git) + PostgreSQL stack via Docker Compose

## Quick Start
1) Install Docker and the Docker compose plugin
2) Copy the environment template and fill in the values:
```bash
cp materials/.env.example .env
# edit .env file
```
3) Start the stack:
```bash
docker compose up -d
```
4) Access
- WEB UI: http://localhost:3000 (or the port you set in .env)
- If the setup wizard appears, choose PostgreSQL and use:
  - Host: db:5432
  - DB name, user, password from `.env`
- Set your external URL (e.g. https://git.example.com/) so links work correctly

## Useful commands
```bash
# view logs
docker compose logs -f forgejo

# restart after changes
docker compose down && docker compose up -d

# update images
docker compose pull && docker compose up -d

# follow DB logs
docker compose logs -f db
```

## Notes / security
- Replace all passwords and secrets with strong random values
- Consider disabling open user registration in Forgejo if you don’t need it
- If running behind a reverse proxy, set the external URL accordingly. Do not publish Forgejo's HTTP port on the host — just expose it to the proxy (container port 3000). The proxy will handle ports 80/443 on the public side
