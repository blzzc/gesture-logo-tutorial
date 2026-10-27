# 04 — Pinch and rotate

## Goal
Turn two finger positions into a gesture and a rotation angle.

The distance between thumb tip (landmark 4) and index tip (landmark 8) is measured in pixels and divided by the palm-width reference from landmarks 5 to 17. This ratio makes the threshold more robust to different distances from the camera.

```js
const ratio = distance / Math.max(palmWidth, 1);
const isPinching = ratio < 0.3;
```

While pinching, the code measures the difference between the current and previous mirrored `x` positions and converts it to radians:

```js
const deltaAngle = (currentX - previousX) * sensitivity;
cube.rotation.y += deltaAngle;
```

## Tiny exercise
Try setting `sensitivity` to `Math.PI` instead of `Math.PI * 2`. What happens to the rotation for the same horizontal drag?

## Known limitation
A single threshold has no hysteresis; noisy landmarks can flicker between pinching and released.
