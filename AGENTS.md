# SAEM — Backend SAEM

ESM Node.js backend using Express 5.

## Commands

```sh
npm run dev       # nodemon --legacy-watch index.js
npm test          # placeholder — no test framework configured yet
docker compose up # dev server with hot reload via nodemon
```

`--legacy-watch` is intentional (WSL/compatibility); do not remove.

## Structure

- `index.js` — entry point (not yet created)
- `Dockerfile.dev` / `docker-compose.yml` — dev container with volume mount
- `package.json` — ESM (`"type": "module"`); Express 5, nodemon

## Notes

- No lint, typecheck, formatter, or git repo configured yet.
