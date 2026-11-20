# Yevqo — Official Website

A lightweight static website for Yevqo, a personal server platform built around Android and Termux.

## Project structure

- `index.html` — homepage
- `features/`, `how-it-works/`, `templates/`, `pricing/`, `faq/` — product pages
- `docs/` — documentation pages
- `css/global.css` — shared styles
- `js/main.js` — shared navigation and FAQ interactions
- `public/favicon.svg` — site icon

## Run locally

No Node.js, package manager, framework, build step or dependencies are required.

Open `index.html` directly, or start a local static server from the repository root:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080`.

On Android, the same files can be served from Termux with Python or another static HTTP server. Keep the working directory at the repository root so relative paths resolve.

## Deployment

Publish the repository root as the static document root. The entry point is `index.html`; do not configure an Astro, Vite or Node build command.

## Product status

This repository contains the public website only. Dashboard visuals are illustrative. The Yevqo Agent, live device pairing, backend, authentication, deployments, monitoring and AI agents are not represented as released functionality unless a page explicitly says otherwise.
