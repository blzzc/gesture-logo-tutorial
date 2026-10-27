# Gesture Logo — 3D Hand Gesture Tutorial

**Version 0.3 · working milestone: pinch-to-rotate + inertial spin.**

A beginner-friendly, project-driven tutorial for interactive 3D in the browser with **Three.js**, **MediaPipe Hand Landmarker** and **Vite**.

## What works

- Live webcam input and one-hand tracking (the detector is configured for up to two hands)
- Thumb/index fingertip pinch detection, normalized to palm width
- Horizontal pinch-drag to rotate a Three.js cube
- Inertial rotation with exponential damping after release
- Motion stops when the hand is no longer detected

Not implemented yet: two-hand zoom, Blender `.glb` loading, robust multi-hand tracking, gesture hysteresis, or production UX.

## Tutorial chapters

1. [Project structure and Vite](docs/01-project-setup.md)
2. [Rendering with Three.js](docs/02-three-scene.md)
3. [Camera and MediaPipe](docs/03-hand-tracking.md)
4. [Pinch-to-rotate](docs/04-pinch-rotation.md)
5. [Inertia and damping](docs/05-inertia.md)
6. [Roadmap: zoom and Blender](docs/06-roadmap.md)

## Prepare local assets (important)

This starter ZIP **does not include the binary hand-tracking model and WASM runtime**, because those files are only on the original development machine. Copy these from the existing working project:

```bash
cp ~/gesture-logo/public/models/hand_landmarker.task public/models/
cp -R ~/gesture-logo/public/wasm/. public/wasm/
```

Run those commands inside the **new** `gesture-logo-tutorial` folder. Without these assets, the 3D cube can render, but hand detection will not start.

## Run locally

Requires Node.js 24 or a compatible version.

```bash
npm install
npm run dev
```

Open the `Local` address printed by Vite. Click **开启摄像头**, grant camera permission, and pinch your thumb and index finger to rotate the cube.

## Publish to GitHub Pages

1. Create a new **public** GitHub repository named **`gesture-logo-tutorial`** (the repository name must match `vite.config.js`). Leave it empty; do not initialize with another README.
2. Copy the missing model/WASM files into this project before publishing.
3. From the new project's directory:

```bash
git init
git branch -M main
git add .
git commit -m "Initial release: gesture logo tutorial v0.3"
git remote add origin https://github.com/YOUR_USERNAME/gesture-logo-tutorial.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your account handle. If Git asks you to authenticate, follow GitHub's browser login instructions; never paste passwords or tokens into the repository.

4. In the repository's **Settings → Pages → Build and deployment**, set **Source = GitHub Actions**.
5. Open the **Actions** tab and confirm `Deploy Vite to GitHub Pages` succeeds. If deployment did not run, manually run the workflow.
6. Visit `https://YOUR_USERNAME.github.io/gesture-logo-tutorial/` after GitHub reports the Pages URL.

The workflow builds with `GITHUB_PAGES=true` to use the repository subpath. The code also uses `import.meta.env.BASE_URL` for model and WASM paths so resources work on Pages. Camera access requires a secure context, which GitHub Pages HTTPS provides.

## How to troubleshoot

- Cube works, hand tracking fails: confirm `public/models/hand_landmarker.task` and WASM files were copied and committed.
- 404 errors on Pages: check repository name matches `gesture-logo-tutorial` and deployment succeeded.
- No webcam permission: inspect site permissions and console errors. GitHub Pages uses HTTPS.
- Publishing to a different repository name: edit `vite.config.js` `base` value before building.

## Development philosophy

Small working steps, understandable source code, and one interactive capability per milestone. The original learning prototype is kept separate from this public tutorial repository.
