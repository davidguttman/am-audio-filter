# AM-IFY · Web Audio Radio Simulator

A single-page static web app that runs an audio file through a Web Audio
processing chain (highpass/lowpass, mid peak, saturation, bitcrusher, noise,
tremolo) to simulate vintage AM radio, weak signals, shortwave, telephone, etc.

Drop an MP3 (or click the display) to load a file, then play it through the
filter. Includes ten draggable knobs, six presets, an A/B FX bypass, loop, and
a live oscilloscope.

## Running locally

It's a single `index.html` with no build step. Open it directly in a browser,
or serve the directory with any static server:

```
python -m http.server 8000
# then open http://localhost:8000/
```

## Deployment

Deploy `index.html` (and this directory) to any static host:

- **GitHub Pages** — push to a repo and enable Pages on the default branch.
- **Netlify / Vercel / Cloudflare Pages** — point at the repo, no build
  command, publish directory `.`.
- **S3 / any CDN** — upload `index.html` to the bucket root.

There are no dependencies and no build artifacts. Fonts are loaded from Google
Fonts at runtime.
