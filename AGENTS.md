# Base44 Dev Environment

## Project
Static Pac-Man game — plain HTML/CSS/JS, no build step, no backend, no dependencies.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
Serves the repo root via `nginx:alpine` on host port 3000.

## Notes
- The repo directory has restrictive (700, root-owned) permissions, so nginx must run as `root` via the custom config `nginx.base44.conf` (mounted into the container). Without it, nginx workers (uid 101) get 403 Forbidden.
- Source is bind-mounted read-only; edits to HTML/CSS/JS/images are reflected immediately on browser refresh (no build step, no live-reload server needed).
- No secrets, no external services, no databases.
