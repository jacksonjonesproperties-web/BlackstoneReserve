# Blackstone Reserve Reels

Static site built to `design_handoff_brr_portfolio/README.md`. One page, no build
step, no dependencies: `index.html`, `css/styles.css`, `js/main.js`.

## Run

```bash
python3 -m http.server 8731
```

## Before it goes live

- **Activate the form — one click, needed once.** Enquiries POST to FormSubmit,
  which relays them to `blackstonereservereel@gmail.com` (`INBOX` in `js/main.js`).
  The first submission makes FormSubmit email that address an activation link;
  until someone clicks it nothing is delivered. So before launch: open the site,
  send yourself a test enquiry, click the link in the Gmail, then send a second one
  to confirm it arrives. FormSubmit also gives you a hashed endpoint at that point —
  swapping it into `ENDPOINT` keeps the address out of the page source.
  A hidden `_honey` field in the form is FormSubmit's spam trap.
- **Hero image.** Served as a PNG srcset at 1280 / 1920 / 2560 / 3840. The handoff
  also asks for WebP/AVIF — no encoder on this machine, so generate those at deploy
  time and add them as `<source>` entries.
- **Poster frames.** The handoff recommends a poster per video; there's no `ffmpeg`
  here to pull them. Until then the tiles use `preload="metadata"` and only play
  while on screen (IntersectionObserver), pausing when they scroll out.
- Tile links are `href="#"` placeholders, per the handoff.

## One judgment call to confirm

The enquiry section uses the handoff's exact grid rule
(`repeat(auto-fit, minmax(min(100%,320px),1fr))`) at full width, as instructed. On a
wide screen that yields three tracks — copy, form, and an empty third — because the
reserved footer row spans all columns and so nothing auto-collapses. The prototype
only showed two columns because it was pinned to 995px, which the handoff says not to
reproduce. Say the word and I'll cap it at two columns.
