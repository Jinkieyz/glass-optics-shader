# Glass optics, a real time GLSL study

A self contained WebGL demo: a cast glass form rendered in real time in the browser,
with the optics written by hand in the fragment shader.

Open it through any static server (it loads Three.js from a CDN):

    python3 -m http.server 8000
    # then open http://localhost:8000

## What the shader does

Three.js only sets up the canvas, a full screen quad and the uniforms. Everything
optical is GLSL:

- A raymarched SDF, a bevelled box melted into a sphere, that rotates slowly.
- Fresnel (Schlick) to weigh reflection against transmission by viewing angle.
- Refraction through the solid: the ray bends in, marches to the far surface, and
  bends out, sampling a procedural studio environment on each side.
- Chromatic dispersion: red, green and blue use slightly different indices of
  refraction, so the edges break into spectral fringes.
- Beer-Lambert absorption, which tints the glass and gives it the satin look of a
  real casting.

## Controls

Drag to orbit, scroll to zoom. Sliders for index of refraction, dispersion, colour
density and glass colour, plus a quality (resolution) scale so the cost fits the
hardware.

## Author

Nadeschda Barenje.
