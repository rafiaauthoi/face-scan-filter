# Face Scan Filter

A sci-fi style face tracking scan effect you can capture and save. No touching, no controller, just a webcam and your face.

## What it does

- **Idle mode**: a pulsing ring waits for a face to enter frame.
- **Active mode**: the instant a face is detected, a bounding box with corner brackets locks on, a wireframe mesh traces the jawline, eyes, and lips, and a glowing scan line sweeps down repeatedly.
- **Rotating readout**: a playful fictional biometric readout cycles every couple seconds ("SYNC RATE: 98.7%", "AURA COLOR: NEON PINK", and similar), giving the scan a living, game-like feel.
- **Capture button**: saves an actual PNG snapshot combining your live face and the full scan overlay, with a camera shutter sound and flash, ready to share.

## How to run it

1. Clone this repo.
2. Open the folder in VS Code.
3. Right click `index.html` and choose "Open with Live Server" (or open the file directly in a browser).
4. Click "Start Scan."
5. Allow camera access when prompted.
6. Face the camera directly to trigger the scan effect, then click "Capture Snapshot" to save an image.

No installs, no build step, no paid services. Everything runs client side using MediaPipe for face tracking and Tone.js for the scan beep and shutter sound, both loaded from public CDNs.

## Tools used

- MediaPipe Tasks Vision (face landmark detection, 478 points per face)
- Canvas API (all visual rendering, including the scan box, wireframe mesh, scan line, and readout text)
- Tone.js (scan beep and camera shutter sound)

## How the capture works

The visible video and the effects canvas are two separate layers, each individually mirrored using CSS so they look correct as a live selfie view. When capturing, a brand new canvas is created, a single mirror flip is applied to it, and both the current video frame and the current effects canvas are drawn onto it in that already-mirrored space. This produces one flattened image where both layers end up correctly aligned and mirrored together, matching exactly what you saw on screen the moment you clicked capture.

## Notes for tabling setup

- Works best with a clear, mostly static background and reasonably even lighting on faces.
- The bordered display box scales with the browser window rather than a fixed pixel size, adjust `width` and `max-width` on `#video-wrapper` in the CSS to fit whatever monitor is used at the event.
- Run the browser in fullscreen (F11) for the actual showcase.
- Captured images download directly to the device running the browser, worth checking where downloads land on the showcase laptop ahead of time.

## Status

Complete.