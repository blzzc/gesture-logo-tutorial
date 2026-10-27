# 02 — Three.js scene

## Goal
Display one cube in a WebGL canvas.

The scene is the virtual world. The perspective camera determines the viewpoint; `camera.position.z = 4` moves the camera back. The renderer draws the world into `<canvas id="scene">`. A mesh combines geometry (`BoxGeometry`) and material (`MeshNormalMaterial`).

```js
const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshNormalMaterial();
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);
```

## Tiny exercise
Change `cube.rotation.x = 0.4` to `0` and explain how the visible faces change. Then restore the original value.
