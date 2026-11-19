# Shuka Marketplace

A single-process Node.js 22+ marketplace with SQLite, built-in HTTP server, responsive frontend, multi-seller checkout, seller order lifecycle, and cash on delivery.

## Run locally

```bash
npm start
```

Visit http://localhost:3000. No npm dependencies needed. Node >=22.13 is required.

## Deploy to Render

Push the repository to GitHub, then create a **Blueprint** in Render pointing at the repository. `render.yaml` provisions a paid Starter service with a persistent disk. Use the resulting HTTPS URL. Do **not** deploy the database to Netlify or Render free ephemeral storage. Persistent disk is essential for SQLite and uploads.

## Operational notes

- Set `DATA_DIR` to a persistent disk directory.
- Schedule a daily backup of the SQLite file with `VACUUM INTO` to a separate backup destination.
- Session tokens are in memory and logins expire on server restart.
- Image uploads validate signature and size, but image resizing is not yet implemented.
- Demo catalog seed (3 sellers / 40+ products) and automated acceptance suite are not yet included.
- Before production use, add durable sessions, request throttling, CSRF protections, image processing, backups and tests.
