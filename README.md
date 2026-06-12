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

## Photo skin

- **📷 Photo** — load a picture or take a shot; it wraps the sphere like a planet texture, each particle taking the color of its pixel
- Works WITH Calm and Swarm: a slowly turning globe of your photo in Calm, the same photo burning and shaking in Swarm
- Luminance becomes surface relief that pumps with the bass; beats flash the picture, touch makes pixels flare
- Particles join the picture one by one in a sparkle dissolve when it loads
- Tap Photo to toggle the skin on/off; double-tap to pick a different image


## Demo track

- **▶ Demo** — plays the bundled track "stay in the loop" (EP-133 K.O., original music by the app author) so the sphere comes alive instantly, no file needed. Cached by the service worker: works offline too. Tap Demo to pause/resume; Track replaces it with your own file.
