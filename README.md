# AM-IFY · Web Audio Radio Simulator

A single-page static web app that runs an audio file through a Web Audio
processing chain (highpass/lowpass, mid peak, saturation, bitcrusher, noise,
tremolo) to simulate vintage AM radio, weak signals, shortwave, telephone, etc.

Drop an MP3 (or click the display) to load a file, then play it through the
filter. Includes ten draggable knobs, six presets, an A/B FX bypass, loop, and
a live oscilloscope.

## Built-in music picker

The transport bar has a **TUNE** dropdown for picking a song from the
bundled `music/` directory — no upload needed. Selecting a song fetches
`music/<filename>`, decodes it via Web Audio, and arms the Play button.
Drag-and-drop and click-to-upload still work for your own files.

Because static hosts can't enumerate directories, the song list is a
hardcoded manifest in `index.html`. If you add or rename files in `music/`,
update the `builtinSongs` array to match.

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

The host must serve the `music/` folder alongside `index.html` so the
built-in song picker can fetch `music/<filename>` over HTTP. Opening
`index.html` directly via `file://` will block those fetches — use a
local static server (see above) during development.

There are no dependencies and no build artifacts. Fonts are loaded from Google
Fonts at runtime.
