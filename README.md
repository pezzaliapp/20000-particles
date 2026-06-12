# 20000 Particles

An interactive sphere of 20,000 glowing particles, built with Three.js. Installable as a PWA, works offline.

**Two states:** Calm (ordered golden grid) and Swarm (pulsing orange cloud). Drag to rotate, touch to heat the particles.

## Deploy on GitHub Pages (pezzaliAPP)

1. Create a new repository named `20000-particles` on GitHub
2. Upload these files keeping the structure:
   ```
   index.html
   manifest.json
   sw.js
   icons/icon-192.png
   icons/icon-512.png
   ```
3. Go to **Settings → Pages → Source: Deploy from a branch → main / (root)** and save
4. After a minute the app will be live at:
   `https://pezzaliapp.github.io/20000-particles/`

All paths are relative, so it works in any subdirectory. On iPhone: open in Safari → Share → **Add to Home Screen** to install it as an app.

## Tech

- Vanilla JS + Three.js r128 (CDN, cached by the service worker for offline use)
- `THREE.Points` with additive blending and a soft canvas sprite for the glow
- Fibonacci-sphere distribution for even particle spacing
- Adaptive particle count (9,000 on small screens for smooth 60 fps)
- Respects `prefers-reduced-motion`

MIT License

## Audio reactivity

- **🎤 Mic** — listens to your voice, claps, or any rhythm around you (asks for microphone permission; nothing is recorded or sent anywhere, audio is analyzed locally in real time)
- **♫ Track** — load a song from your device; tap Track again to pause/resume
- Bass makes the whole sphere breathe and pulse on the beat
- The spectrum is mapped onto the sphere's latitudes like a 3D equalizer: bass at the equator, treble at the poles
- Highs drive the sparkle flicker; beats flash the particles hotter

Note: the microphone requires HTTPS — it works on GitHub Pages and as an installed PWA.

## Photo mode

- **📷 Photo** — load a picture or take a shot (on phones the picker offers the camera directly)
- The image is decomposed: each of the 20,000 particles is assigned to a pixel in shuffled order, so during the morph they cross and mix mid-air before recomposing the picture
- Luminance becomes a 3D relief; touch makes pixels pop toward you and flare
- With audio active the photo dances: bass pumps the relief, the spectrum sweeps it left (bass) to right (treble) like a spectrogram, beats flash the brightness
- Tap Photo again to load a different image; Calm or Swarm morph back to the sphere

## Demo track

- **▶ Demo** — plays the bundled track "stay in the loop" (EP-133 K.O., original music by the app author) so the sphere comes alive instantly, no file needed. Cached by the service worker: works offline too. Tap Demo to pause/resume; Track replaces it with your own file.
