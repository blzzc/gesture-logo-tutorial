# 01 — Project structure and Vite

## Goal
Understand what Vite does before adding 3D or computer vision.

`index.html` holds the current prototype. `package.json` names the dependencies and scripts. `public/` stores files served without JavaScript bundling. Vite runs a local development server and builds deployable assets into `dist/`.

## Tiny exercise
Run `npm run dev`, open the `Local` address, and change the `<h1>` text in `index.html`. Refresh the page. Why did changing HTML not require restarting Vite?

## Notes
The production website runs the output of `npm run build`, not the development server. Deployment-specific asset paths are configured in `vite.config.js`.
