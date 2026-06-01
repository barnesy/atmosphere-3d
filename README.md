# Atmosphere — "Shoot for the Moon"

A scroll-driven, single-file WebGL journey built with [Three.js](https://threejs.org/). One continuous shot takes you from a bright morning launch pad to a moonlit landing: a toy rocket lifts off and arcs into orbit around a realistic moon, animals climb the hills, a UFO abducts a rabbit with a tractor beam and then barrel-rolls down to touch down beside the rocket — all while the sky ramps from day to dusk to night and the moon rises solid from behind the ridgeline.

Everything is rendered live in the browser. No build step, no framework, no assets beyond a couple of OBJ models, some textures, and one small generated video texture.

**[▶ Live demo](https://barnesy.me/atmosphere-3d/)**

## Highlights

- **Scroll *is* the timeline.** The whole sequence is a deterministic function of scroll progress, `updateScene(s, t, dt)` — so it scrubs forward and backward smoothly and renders identically at any point.
- **Real 3D type.** The "Shoot for the Moon" headline is extruded `TextGeometry` with soft, rounded "space-pillow" bevels, lit on its own render layer, with a glitter texture (a seamless-looping MP4) driving its emissive channel so it twinkles. It zooms past the camera to dismiss as you start scrolling.
- **Custom GLSL** for the sky gradient, the gibbous moon, the fresnel tractor beam, and a reflective sea.
- **Hand-tuned choreography** — cubic-bézier launch, great-circle (slerp) descent so the rocket never clips through the moon, a draped "laser" ring where the beam meets the hill, and a final-approach barrel roll.
- **Responsive** — the 3D title re-fits and re-centers against the real camera projection so it never clips on narrow screens.

## Run locally

It's a static site — serve the folder with anything:

```bash
python3 -m http.server 4321
# then open http://localhost:4321/
```

## Project structure

```
index.html      # the entire experience (Three.js scene, shaders, scroll choreography)
moontex.mp4     # seamless-looping glitter texture for the title (generated with ffmpeg/numpy)
models/         # toy_rocket.obj, ufo.obj
textures/       # moon, rocket, and UFO maps
```

## Tech

Three.js (r0.160) · OBJLoader · FontLoader + TextGeometry · custom ShaderMaterials · VideoTexture · WebGL.

Pair-coded with Claude.

---

© 2026 Chris Barnes
