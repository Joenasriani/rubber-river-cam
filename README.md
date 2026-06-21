# Rubber River Cam

Browser-first camera recorder prototype with elastic hand trails and cheek/mouth stretch effects.

## What it does
- Requests camera + microphone permission after pressing **Allow Camera + Mic**.
- Shows a processed live canvas feed.
- Tracks hands and face with MediaPipe Tasks Vision.
- Creates liquid/river-style finger extension trails.
- Creates elastic cheek/mouth-corner stretch when you pinch near a mouth corner and pull outward.
- Records the processed canvas and microphone audio.

## How to run
Camera/microphone APIs require HTTPS or localhost.

```bash
python3 -m http.server 8080
```

Open:

```text
http://localhost:8080
```

## Browser notes
- Best target: Chrome or Edge desktop/Android.
- Safari/iOS may show the live effect but can fail or vary when recording canvas + microphone.
- The app now checks for required APIs before requesting devices.
- The recorder uses MIME fallbacks: VP9 WebM, VP8 WebM, WebM, then MP4 if supported.

## Offline / itch.io packaging
This build tries local assets first, then CDN fallback.

For a fully offline/itch.io-safe package, add:

```text
vendor/mediapipe/tasks-vision/vision_bundle.mjs
vendor/mediapipe/tasks-vision/wasm/*
models/hand_landmarker.task
models/face_landmarker.task
```

If local files are missing, it falls back to:

```text
https://cdn.jsdelivr.net/npm/@mediapipe/tasks-vision@0.10.18/
https://storage.googleapis.com/mediapipe-models/
```

## IP / naming note
The public UI avoids copyrighted character names, logos, or copied assets. The effect is described as original elastic cheek stretch / rubber-mouth deformation.
