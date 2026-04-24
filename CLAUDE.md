# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a GitHub Pages site (`veqtor.github.io`) hosting a minimal Ethereum voting DApp at `pixelplace/index.html`. It is a plain HTML/JS project with no build system, package manager, or test infrastructure.

## Stack

- **Bootstrap 3.3.7** — styling via CDN
- **jQuery 3.2.1 (slim)** — DOM manipulation via CDN
- **Web3.js** — Ethereum blockchain interaction via CDN (rawgit, develop branch)

## Development

No build step required. Open `pixelplace/index.html` directly in a browser or serve it locally:

```bash
python3 -m http.server 8080
# then open http://localhost:8080/pixelplace/
```

## Known Gap

`pixelplace/index.html` references `./index.js` (line 39), which is **not tracked** in the repository. This file should contain:
- Web3 provider setup (connecting to an Ethereum node or injected provider like MetaMask)
- Contract ABI and deployed address
- `voteForCandidate()` function — called by the Vote button
- Logic to populate `#candidate-1`, `#candidate-2`, `#candidate-3` with live vote counts

When adding `index.js`, match the existing inline style: plain ES5 JavaScript, no modules, no transpilation.

## Repository Structure

```
pixelplace/
  index.html   # Single-page voting DApp UI
```

The site is served directly by GitHub Pages from the repository root; no Jekyll or other static site generator is configured.
