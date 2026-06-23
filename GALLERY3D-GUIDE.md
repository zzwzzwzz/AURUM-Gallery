# Immersive Gallery (v2) — how it works & how to copy the references

This explains the `gallery3d.html` spike and gives you a path to the look of the two reference sites. Written for someone new to three.js.

## What was decided (council pass #3, 2026-06-23)
- **Technique: scroll-on-rails.** The camera glides forward along a *fixed path* down a corridor of paintings. You don't free-walk — you scroll, and the world moves past you like a film. This was the lowest-friction, mobile-friendly, beginner-safe choice.
- **NOT free-roam WASD.** The whole council flagged "walk exactly like real life" as a multi-week build (collision, mobile touch controls, motion sickness) that breaks on phones and excludes keyboard users. It's the v3 upgrade, not v1.
- **NOT photoreal.** Stylized beats realistic. A clean room with good lighting reads as "gallery" instantly; chasing realism is uncanny-valley + infinite asset work.
- **Additive + accessible.** The 3D page is linked as "immersive (beta)"; the 2D pages remain the front door and the accessible equivalent.

## The five three.js concepts in this file
Everything in `gallery3d.html` is built from these. If you learn these five, you understand the whole thing:

1. **Scene / Camera / Renderer** — the trinity. `Scene` is the world, `PerspectiveCamera` is your eye, `WebGLRenderer` draws it to the `<canvas>` every frame.
2. **Geometry + Material = Mesh.** The room is `PlaneGeometry` walls/floor/ceiling with `MeshStandardMaterial` (reacts to light). Each painting is a `PlaneGeometry` with a `MeshBasicMaterial` (ignores light, so the art stays crisp).
3. **Texture.** `TextureLoader` downloads each Met image and wraps it onto a painting plane. The image's width/height sets the plane's aspect ratio so nothing is stretched.
4. **Lights.** `HemisphereLight` + `AmbientLight` for base fill, and one `SpotLight` per painting washing the wall around it — that pool of light is what sells "gallery."
5. **Raycaster.** When you click, a ray is shot from the camera through the cursor; if it hits a painting, we show the wall label. This is how all 3D "click on a thing" works.

Plus two non-three.js pieces:
- **Scroll-on-rails:** one number, `progress` (0→1), driven by `wheel` / `touchmove` / arrow keys. Each frame the camera's `z` is interpolated between `START_Z` and `END_Z` from that number. That's the entire "movement" system — no physics.
- **LoadingManager:** the Met images are heavy (~1–2 MB each), so a loading bar runs until they're all decoded, then fades.

## Why no build step
three.js is pulled from a CDN via an **importmap** (`<script type="importmap">`). That keeps the zero-build, open-the-file-in-a-browser nature of the whole AURUM site. No npm, no webpack, no Vite.

## How to copy each reference

### To get the VRSEAT look (constrained, reflective, click-to-preview)
VRSEAT keeps the camera on a leash and leans on **reflections + spatial audio**.
1. Add `OrbitControls` (from `three/addons/controls/OrbitControls.js`) at each stop so the visitor can look around from a fixed point, with limits set so they can't spin wildly.
2. Glossy floor: raise the floor material's `metalness` and lower `roughness`, or add a `Reflector` (three.js addon) for a true mirror floor. (VRSEAT uses screen-space reflections — that's the expensive version; skip it.)
3. Spatial audio: `THREE.PositionalAudio` attached to objects, gated behind a "tap to enter / use headphones" prompt (never autoplay).

### To get the Penderecki's Garden look (cinematic, narrated, scene-to-scene)
That site is an agency production — don't copy it literally. The *achievable* lessons:
1. **Scene choreography:** instead of one corridor, define several "stops" (a `CatmullRomCurve3` path) and snap the camera to named scenes as `progress` crosses thresholds. Fade in a caption/quote at each.
2. **Audio per scene** with the "use headphones" prompt, fading between tracks as you scroll.
3. **Art direction over realism:** they win on color grading and sound, not polygon count. Add one subtle post-processing **bloom** pass (`UnrealBloomPass` from addons) so the gold glows — that single effect does most of the "premium" work.

## The upgrade path (each step is independently shippable)
1. **Bloom** post-processing (gold glow) — biggest visual payoff per line of code.
2. **Ambient audio** + "use headphones" prompt.
3. **Look-around (OrbitControls)** at each painting.
4. **Multi-room** — duplicate the corridor, glide through a doorway.
5. **Glossy floor reflection.**
6. *Only if truly wanted:* a **free-roam toggle** (`PointerLockControls` + bounding-box collision) — this is v3 and needs senior review for the a11y/mobile story.

## Gotchas already handled in the spike
- `renderer.setPixelRatio(min(dpr, 2))` so retina phones don't melt.
- `prefers-reduced-motion` → the camera snaps instead of easing (and there's a commented one-liner to send those visitors straight to 2D).
- No-WebGL → an accessible fallback screen links to the 2D gallery.
- Wheel/touch drive the camera (body doesn't scroll), so clicks always reach the canvas.
- Art uses `MeshBasicMaterial` so paintings never go dark, regardless of room lighting.

## Known limits (it's a spike)
- Met images are hotlinked; if one 404s you'll see an empty frame (add a fallback texture later).
- Eight works, one room — deliberately small so it's *finished*.
- No audio, no bloom yet (top of the upgrade path).
