# 03 — Camera and hand landmarks

## Goal
Understand how a video frame becomes 21 detected hand landmarks.

Clicking the start button calls `getUserMedia` to ask for permission to use the camera. MediaPipe's `HandLandmarker` is initialized in `VIDEO` mode with a locally hosted `.task` model and WASM runtime. The loop calls `detectForVideo` only when a new video frame is available.

A landmark has normalized `x` and `y` positions. The current prototype uses only `result.landmarks[0]`, even though `numHands` is set to 2. It does not track stable hand identity.

## Tiny exercise
Find `hand[4]`, `hand[8]`, `hand[5]`, and `hand[17]` in `detectHands()`. Match them to thumb tip, index fingertip, and two palm-width reference points.
