# Rubber River Cam

Browser-first camera recorder prototype with elastic hand trails and cheek/mouth stretch effects.

## Live URL

After GitHub Pages is enabled from the repository settings, the app should be available at:

```text
https://joenasriani.github.io/rubber-river-cam/
```

## What it does

- Requests camera + microphone permission after pressing **Allow Camera + Mic**.
- Shows a processed live canvas feed.
- Tracks hands and face with MediaPipe Tasks Vision.
- Creates liquid/river-style finger extension trails.
- Creates elastic cheek/mouth-corner stretch when you pinch near a mouth corner and pull outward.
- Records the processed canvas and microphone audio.

## Browser notes

- Best target: Chrome or Edge desktop/Android.
- Safari/iOS may show the live effect but can fail or vary when recording canvas + microphone.
- Camera and microphone APIs require HTTPS or localhost.
- GitHub Pages uses HTTPS, so the published URL is suitable for camera/mic permission.
- The app checks for required APIs before requesting devices.
- The recorder uses MIME fallbacks: VP9 WebM, VP8 WebM, WebM, then MP4 if supported.

## GitHub Pages setup

This repo now includes `.nojekyll` on `main`, which is correct for a plain static HTML app.

Enable Pages manually in GitHub:

```text
Settings → Pages → Build and deployment
Source: Deploy from a branch
Branch: main
Folder: /root
Save
```

Then open:

```text
https://joenasriani.github.io/rubber-river-cam/
```

## How to run locally

Camera/microphone APIs require HTTPS or localhost.

```bash
python3 -m http.server 8080
```

Open:

```text
http://localhost:8080
```

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
