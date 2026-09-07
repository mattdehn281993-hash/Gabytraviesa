# Drop images here

Anything in this folder is served alongside the site. No account, no upload
step, no build — drop a file in and it's available.

If you use the filenames below, I can wire them in without asking you anything.
If a name doesn't match, that's fine too — just tell me what you dropped.

---

## `portrait/`

| Filename | Where it appears |
|---|---|
| `gaby.jpg` | About page — replaces the "GT" placeholder |

Portrait or square crop, at least 800px on the short edge. She'll be shown at
roughly 320×430, so 800px covers retina screens comfortably.

---

## `covers/`

Real book covers. These replace the Amazon CDN images, which cap at **500px
tall** and go soft on the book detail page.

| Filename | Work | Edition |
|---|---|---|
| `renacer-es.jpg` | Renacer sin ti | Spanish |
| `renacer-en.jpg` | Reborn Without You | English |
| `huellas-es.jpg` | Huellas en el Corazón | Spanish |
| `huellas-en.jpg` | Paw Prints on Our Hearts | English |
| `trascender-es.jpg` | Trascender | Spanish |
| `trascender-en.jpg` | Transcend | English |
| `ligero-es.jpg` | Viajar Ligero | Spanish |

Aim for ~1200px tall. The layout crops to a 3:4.6 frame, so avoid covers with
important text hard against the top or bottom edge.

An edition with no file here keeps using the Amazon image, so partial drops are
fine — add what you have.

---

## `misc/`

Anything else: congress photos, event shots, images for a reflection. Drop them
in and tell me where they should go.

---

## Notes

- **Formats:** `.jpg`, `.png`, `.webp`, `.svg` all work. JPEG for photos.
- **Size:** keep each file under ~1MB where you can. These load on mobile, often
  on a phone connection.
- **No audio here.** Audio is a separate decision — see the note in the chat.
  Short version: a handful of files can live in `assets/audio/` and be served
  like these; her uploading her own from the Studio is what needs a backend.
- **Filenames:** lowercase, no spaces, hyphens instead. `gaby-retrato.jpg`, not
  `Gaby Retrato (1).JPG` — spaces and parentheses need escaping in URLs.

---

## `audio/`

Her meditations, and any podcast episode she wants hosted here rather than on
Spotify. Drop the file in and tell me which meditation it is.

Once a real file is here I can make the meditation player on the site **actually
play**, instead of the visual simulation it runs now. That is the single biggest
upgrade available at the moment.

- MP3 preferred (widest support). WAV and M4A also work.
- Any filename is fine — just say which meditation it belongs to. If you want to
  pre-name it, use the meditation's key: `peso.mp3`, `habitacion.mp3`,
  `ruido.mp3`, `dormir.mp3`, `amiga.mp3`, `luz.mp3`, `casa.mp3`,
  `decision.mp3`, `perdonar.mp3`, `cuerpo.mp3`.
- Rough size: a 20-minute meditation at 128 kbps is about 19 MB. Fine locally.
  See the bandwidth note below before this goes to a real domain.

## `video/`

**Read this before dropping a video in.** Self-hosting video is the one asset
that genuinely costs money at scale — every viewer downloads the whole file at
one fixed quality, with no adaptive streaming.

**Preferred:** put it on her YouTube channel
(`@gabrielatraviesaescritora.64`), set it Unlisted if it should not be public,
and give me the URL. It then plays inline on the site through the click-to-load
player already built — no bandwidth cost, adaptive quality on phones, and it
never sends anyone off the site.

**Drop the file here instead if:** it must not touch YouTube at all, or it is
short (under ~30 seconds) and meant as background or texture rather than
something to watch.

- MP4 (H.264 + AAC) is the only format worth using for broad browser support.

---

## Bandwidth note (for later, not now)

Storage is cheap; **egress is what costs.** A 19 MB meditation streamed 300
times in a month is about 5.7 GB of transfer — enough to exhaust a typical free
tier on its own. This does not matter while we are previewing locally. It
matters the day the site goes to a real domain, and it is the reason video
belongs on YouTube even though audio can reasonably be self-hosted.
