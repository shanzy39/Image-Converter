# <img src="icon.svg" width="28" height="28" align="center" alt=""> Image Converter

A free, client-side web tool to **convert, resize, and compress images** — right in your browser. Drop in a PNG, JPG, WebP (and more), pick an output format, tweak the size and quality, and download. **Nothing is ever uploaded** — every pixel stays on your machine.

> Live demo: https://shanzy39.github.io/Image-Converter/

## Features

- **Convert between formats** — PNG, JPG, and WebP
- **Drag & drop or browse** — also accepts GIF, BMP, and SVG as input
- **Resize** — set a target width/height, with optional **lock aspect ratio**
- **Quality / compression slider** — dial in file size for JPG &amp; WebP, with a live size estimate
- **Live preview** — see the result (on a transparency checkerboard) before you download
- **Size readout** — shows the estimated output size and how much smaller/larger it is than the source
- **Privacy by default** — re-encoding strips **EXIF/GPS metadata** from the exported image
- **100% client-side** — no upload, no server, no tracking, works offline

## How it works

1. The chosen image is loaded into an in-memory `Image`
2. It's drawn onto a `<canvas>` at your target dimensions (high-quality smoothing; JPG gets a white matte so transparent areas don't turn black)
3. `canvas.toBlob()` re-encodes it to your selected format and quality
4. The resulting blob is previewed and offered as a download — and because it's a fresh re-encode, embedded metadata (camera info, GPS, timestamps) is dropped

## Notes

- **PNG is lossless**, so the quality slider only affects **JPG** and **WebP**.
- **WebP export** depends on browser support; if your browser can't encode WebP, that option is disabled automatically.
- Converting a transparent PNG to **JPG** fills the background with white (JPEG has no transparency).

## Run locally

No build step, no dependencies. Open `index.html` in a browser:

```bash
# open directly — it works straight from the filesystem
open index.html
```

(Or serve the folder with any static server if you prefer.)

## Deploy to GitHub Pages

1. Push this repo to GitHub
2. **Settings → Pages**
3. Source: **Deploy from a branch**, branch `main`, folder `/ (root)`
4. Save — your site goes live at `https://<your-username>.github.io/Image-Converter/`

## Built with

- Plain HTML, CSS, and vanilla JavaScript — the native `<canvas>` 2D API and `FileReader`
- No frameworks, no build tools, no CDNs — a single self-contained HTML file

## Companion projects

- [SVG-2-STL-Converter](https://github.com/shanzy39/SVG-2-STL-Converter) — turn SVG vectors or text into 3D-printable STL files
- [Lightning-Decoder](https://github.com/shanzy39/Lightning-Decoder) — inspect LNURL, Lightning Address, and BOLT11 strings

## License

MIT
