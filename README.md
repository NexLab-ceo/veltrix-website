# Yevqo — Official Website

A static landing page for Yevqo, a personal server platform built around Android and Termux.

## Stack
- Astro 5 (static output)
- Svelte 5 for the interactive navigation and FAQ
- TypeScript
- Lucide icons

## Run locally
```bash
npm install
npm run dev
```

## Build for Android / Termux
```bash
npm run build
```

The production website is generated into `dist/`. It can be served from Android with a lightweight static HTTP server, for example `npx serve dist -l 8080`.

This repository contains the public landing page only. Dashboard visuals are illustrative mockups; no backend, authentication, device connection, deployments or AI agents are implemented here.
