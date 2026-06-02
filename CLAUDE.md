# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the personal portfolio / CV site for **Göran Sandström (veqtor)** — ML/full-stack engineer and electronic musician from Stockholm — served via GitHub Pages at `veqtor.github.io`. Plain HTML/CSS/JS, no build system, package manager, or test infrastructure.

## Structure

- `index.html` — the site. A single self-contained file (inline CSS + JS) presenting a **reverse-chronological timeline** (newest at top, oldest at bottom) interleaving two threads: **engineering/code** (teal) and **music/sound** (violet), with **milestones** (amber).
- `pixelplace/index.html` — an older, unrelated Ethereum voting DApp experiment kept as historical content. Not linked from the homepage except as a portfolio repo reference.

## Conventions

- **Single-file, no dependencies.** Everything (styles, scroll-reveal `IntersectionObserver` logic) lives inline in `index.html`. Fonts come from Google Fonts; media via third-party embed iframes. Keep it dependency-free and plain ES5-ish JS.
- **Timeline entries** are `.node` blocks classed `code` / `music` / `mile`, each containing a `.card`. Order is strictly newest→oldest; era dividers (`.era`) separate decades.
- **Color system** via CSS custom properties in `:root`: `--accent` (teal=code), `--accent2` (violet=music), `--accent3` (amber=milestone).
- **Only public sources.** All linked content is from public profiles (GitHub, Bandcamp, SoundCloud, Spotify, Discogs, Wikipedia, Internet Archive).

## Pending / data to refine

- **Bandcamp embeds:** Bandcamp blocks automated ID lookup. Albums currently link out rather than embed. To embed a player, get the album ID in-browser via
  `JSON.parse(document.querySelector('meta[name="bc-page-properties"]').content).item_id`
  then use `https://bandcamp.com/EmbeddedPlayer/album=<ID>/`.
- **Tekniska museet / Yellofier / Synchroid** entry has approximate dates/details (flagged with a `.note` in the page) — refine with first-party info.
- **YouTube** channel: `https://www.youtube.com/channel/UCw8fHBq-XE0fXQSjfGirxFQ`. Add specific video embeds if desired.

## Development

No build step. Serve locally:

```bash
python3 -m http.server 8080
# then open http://localhost:8080/
```

GitHub Pages serves directly from the repository root (no Jekyll configured).
