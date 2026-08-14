# Cliniway e-business card

Static one-page digital business card for William Wang, Founder & CEO of Cliniway.
No build step, no dependencies — plain HTML and CSS.

## Files

| Path | Notes |
|---|---|
| `index.html` | The whole card. Inline CSS and JS. |
| `assets/cliniway-logo.png` | Transparent PNG, 1200px wide. |
| `assets/william-wang.jpg` | 400×400 portrait, shown as a circular crop. |
| `assets/cliniway-demo.mp4` | 720p30 H.264, faststart. 8.4 MB. |
| `assets/demo-poster.jpg` | Poster frame shown before playback. |
| `.nojekyll` | Stops GitHub Pages running the files through Jekyll. |

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

Open `index.html` directly via `file://` and everything works except the video,
which some browsers block on the file protocol. Use the server for a true preview.

## Deploy to GitHub Pages

```bash
git init -b main
git add .
git commit -m "Cliniway e-business card"
git remote add origin https://github.com/<user>/<repo>.git
git push -u origin main
```

Then: **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)` → Save.**
Live at `https://<user>.github.io/<repo>/` in about a minute.

### Custom domain

Add a `CNAME` file containing one line, e.g. `card.cliniway.io`, then at your DNS
provider create a CNAME record pointing `card` → `<user>.github.io`. Enable
**Enforce HTTPS** in Settings → Pages once the certificate is issued.

## Editing

- **Contact details and copy** — in the markup of `index.html`.
- **Colours** — the `:root` block at the top. Values are sampled from the logo.
- **vCard** ("Save to contacts") — the `vcf` array in the `<script>` at the bottom.
  Keep it in sync with the visible contact details.
- **QR code** — replace the `.qr-slot` div with an `<img>` once the URL is final.

## Swapping the video for a hosted embed

To cut the repo to ~150 KB, upload the demo to YouTube or Vimeo and replace the
`<section class="video">` block with an iframe. The click-to-load script and the
`.frame` styles can then be deleted.
