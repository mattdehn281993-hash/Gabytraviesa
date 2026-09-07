# Sanctuary — Gaby Traviesa

Two interactive demos built for **Gabriela Traviesa Soria** (Gaby Traviesa),
thanatologist and bioethicist, Aalsmeer, Netherlands.

| | |
|---|---|
| **Sanctuary for Readers.dc.html** | The public site — books, meditations, reflections, podcast, about, circle |
| **Sanctuary Studio.dc.html** | Her side — upload audio, add videos and episodes, write or dictate, manage the circle |

Both are single self-contained files on the Claude Design (`x-dc`) runtime.
No build step, no bundler, no framework install. Bilingual ES/EN throughout,
architected so Dutch can be added as a third language without touching the
templates.

---

## Run it

Serve the folder over HTTP and open either file:

```bash
python -m http.server 8080 --bind 127.0.0.1
```

- Site → <http://127.0.0.1:8080/Sanctuary%20for%20Readers.dc.html>
- Studio → <http://127.0.0.1:8080/Sanctuary%20Studio.dc.html> (any email/password signs in)

**Serve it — don't double-click the file.** Over `file://` the page gets a null
origin, which breaks the YouTube and Spotify embeds. It is the same condition
that stops them working inside a sandboxed canvas.

React is vendored in `vendor/`, and on `localhost` the pages prefer that copy,
so the demo boots with no network at all. Served from any real host the shim is
inert and the runtime fetches React normally.

---

## How the two halves connect

Both pages are served from one origin, so they share `localStorage`. The Studio
owns the key `gt-studio-v1` and writes it; the site only ever reads it.

- Only items marked **public** reach the site. Drafts and circle-only writing never do.
- The Studio supplies titles and bodies; the site keeps the rich copy the Studio
  doesn't capture (a reflection's closing line, its cross-links, its place).
- With no store — or a corrupt one — the site falls back to its own built-in
  content and still stands on its own.
- A publish in one tab updates an open site tab live, via the `storage` event.

Phase 3 replaces that storage layer with a real backend; nothing above it needs
to change.

---

## What's real and what's demo

Real, and verified against the live services:

- Her seven Amazon editions across four works, with real buy links
- Three YouTube talks and two Spotify episodes — titles recovered from the
  oEmbed endpoints, not invented
- One real meditation recording, **"El verdadero viaje" / "The True Journey"**,
  in both languages, which genuinely plays
- Her ABBC congress talk on the About page
- Her portrait

Demo, and labelled as such in the interface:

- The other ten meditations advance a progress bar without audio
- Book sample passages are placeholder prose, marked pending
- Sign-in accepts anything; there is no account
- Circle access checks an email against the Studio's invite list in the browser.
  It is not authentication.

---

## Assets

`assets/README.md` documents what goes where and under which filename.

Her portrait and the recorded meditation **are committed**, with her
permission, so the demo works straight from a clone. The recording is already
published on her YouTube channel; the files here are the audio-only versions.
`uploads/` (internal briefs) is not committed.

Still outstanding from her: the seven high-resolution book covers (the site
currently falls back to Amazon's CDN, which caps at 500px and goes soft), a
description for the recorded meditation, and confirmation of its Spanish title.

---

## Tests

Four suites run the real component code in Node, no browser and no network:

```bash
node verify.js       # content integrity, ES/EN symmetry, cross-link validity
node sim.js          # site behaviour, 70 render states
node studio-sim.js   # Studio behaviour, 120 render states
node phase2-sim.js   # both halves against one shared store
```

They live outside this repo in the working scratchpad; move them into `test/`
if this becomes a real project.
