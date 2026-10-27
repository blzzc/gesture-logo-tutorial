# 05 — Inertial rotation

## Goal
Continue rotating briefly after a release and slow down naturally.

Angular velocity is measured in **radians/second**. During a drag, estimate it from `deltaAngle / dt` and smooth it with an exponential blend. When the pinch ends but the hand remains visible, retain velocity.

After release, the animation loop integrates an exponentially decaying angular velocity:

```js
const decay = Math.exp(-damping * dt);
cube.rotation.y += angularVelocity * (1 - decay) / damping;
angularVelocity *= decay;
```

The animation update runs only when `!isDragging`. A fresh pinch resets `angularVelocity` to `0`; a missing hand also stops movement immediately in this version.

## Tiny exercise
Change `damping` from `3` to `1` and then `6`. Compare how far the cube keeps spinning after the same flick.

## Important distinction
The inner `else` handles a hand that is visible but not pinching: preserve velocity. The outer `else` handles no detected hand: reset velocity.
