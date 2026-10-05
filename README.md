<br>
<br>
<br>
<br>
<p align="center">
  <img src="./assets/icon.png" alt="YiMatches Logo" width="96" height="96" onerror="this.style.display='none'"/>
</p>
<h1 align="center">YiMatches</h1>
<h3 align="center">Simple and clever link-up game.</h3>

<p align="center">A clean, lightweight, and privacy-first 连连看 (link-up) game, crafted with Material You and modern web engineering.</p>
<p align="center">Made with ❤️ by <a href="https://github.com/lingyicute">lingyicute</a>.</p>
<br>
<br>
<p align="center">
  [🇺🇸 English] •
  <a href="https://github.com/lingyicute/YiMatches">🌐 Source Code</a> •
  <a href="https://github.com/lingyicute/YiMatches/issues">🐛 Report Bug</a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-AGPL--3.0-orange.svg" alt="License: AGPL-3.0"></a>
  <a href="index.html"><img src="https://img.shields.io/badge/Single%20File-367%20KB-blue" alt="Single File 367 KB"></a>
  <a href="https://github.com/lingyicute/YiMatches"><img src="https://img.shields.io/badge/Dependencies-Zero-brightgreen" alt="Zero Dependencies"></a>
  <a href="https://github.com/lingyicute/YiMatches"><img src="https://img.shields.io/badge/Ads%20%26%20Trackers-Zero-brightgreen" alt="No Ads No Tracking"></a>
  <a href="https://github.com/lingyicute/YiMatches"><img src="https://img.shields.io/github/stars/lingyicute/YiMatches?style=flat&color=yellow" alt="GitHub Stars"></a>
</p>
<br>

## 📖 Overview

连连看 (link-up) is a genre full of look-alikes that cheat on the one rule that matters: two tiles should disappear only when a path of **at most three straight segments** actually connects them. Many browser clones quietly fall back to "same row or column", or forget that routes are allowed to travel **around the outside of the board**.

**YiMatches** implements the real rule set — including border-wrapping paths — and *shows* you the route: the connection is drawn as an animated line over the board so you can see exactly why a pair matched. It ships as **one self-contained HTML file** with hints, limited shuffles, undo, and a stats list per difficulty.

<br>

## ✨ Features

- **🧠 A Correct Ruleset**
  - Real path-finding: the engine tests **straight, one-bend and two-bend** routes — plus their **border-wrapping** variants — so a pair clears if and only if a legal path exists.
  - The winning path is **drawn as an animated SVG line**, making every match self-explanatory.
  - **Dead-end rescue** — when no legal move remains, the board reshuffles itself automatically, free of charge.

- **🛟 Assists That Keep It Moving**
  - **Hint (提示)** highlights a valid pair; uses are limited per difficulty.
  - **Shuffle (重排)** redistributes the remaining tiles on demand, with the remaining count always visible.
  - **Undo** steps back through your moves; **restart** deals a fresh board in one tap.

- **🎯 Four Board Sizes**
  - **简单 Easy** 6×6 / 9 tile types · **中等 Medium** 8×8 / 16 · **困难 Hard** 8×10 / 20 · **专家 Expert** 10×12 / 24.
  - Hint budgets scale with the difficulty (5 hints on easy down to 4 on expert, 3 shuffles each).

- **📊 Records & Feedback**
  - **Best completion time per difficulty**, plus a count of how many times you have cleared each board.
  - Toasts and dialogs for new records, dead ends, and out-of-moves situations.

- **🎨 Material You & Polished Design**
  - **Dynamic theming**: eight accents built on `oklch` tonal ramps, applied to surfaces, chips, tiles and outlines.
  - Day / Night mode, initial choice from `prefers-color-scheme`, live `theme-color` updates, `prefers-reduced-motion` support.
  - Tiles scale with the board using container-relative sizing, so the icons stay proportional from 6×6 up to 10×12.

- **🔒 100% Privacy, Offline & Ad-Free**
  - **Zero network requests** — the game is self-contained and plays offline.
  - Difficulty and best times live in `localStorage` (`ym-diff`, `ym-best`); nothing is uploaded.
  - Licensed under **AGPL-3.0**.

- **⌨️ Keyboard and Touch Parity**
  - Move a cursor with `↑ ↓ ← →` / `W A S D`, select with `Space` or `Enter`, `H` for a hint, `Z` to undo, `X` to shuffle, `R` to restart.
  - ARIA labels, focus-visible outlines and dialogs for every action that needs confirming.

<br>

## 🛠️ Why YiMatches? (Under the Hood)

### 1. Pathfinding You Can Verify
The matcher is a real 连连看 pathfinder: it walks straight runs, one-turn candidates and two-turn candidates (both plane-internal and routed through the one-cell border around the board). The same routine powers the "any move left?" check, so hints, dead-end detection and matching can never disagree with each other.

### 2. Fair, Predictable Board Generation
Boards are laid out so that a solution exists by construction, and the auto-reshuffle on a dead end keeps a run alive instead of forcing a restart — you lose time, never the game, to a badly shuffled board.

### 3. Zero-Dependency, Zero-Network Architecture
`index.html` holds markup, styles, the pathfinder, the SVG line overlay and a base64-embedded subset of the "Nebulove" typeface. No framework, no bundler, no CDN, no analytics, **no external requests at all** — so the file runs from disk, from any static host, or on a plane.

<br>

## 🚀 Play It Now

There is nothing to install — the game *is* one HTML file.

### Option 1 — Just open it
Download `index.html` (or clone the repository) and double-click the file. It works straight from disk, offline.

### Option 2 — Serve it locally
```bash
git clone https://github.com/lingyicute/YiMatches.git
cd YiMatches
python3 -m http.server 8000     # then open http://localhost:8000
```

### Option 3 — Publish it anywhere
Drop `index.html` on GitHub Pages, Cloudflare Pages, Netlify or any static host — a single file is the entire deployment.

<br>

## 🔨 Building from Source

There is no build step: `index.html` is the source *and* the artifact.

1. **Clone the repository**:
   ```bash
   git clone https://github.com/lingyicute/YiMatches.git
   cd YiMatches
   ```

2. **Edit and reload** — the file is split by banner comments (tools, storage, theme, pathfinding, board generation, rendering, dialogs), so the engine and the presentation stay separable.

3. **Ship it** — commit and push; with GitHub Pages enabled, the update is live immediately.

<br>

## 🤗 Contributing

Contributions are always welcome!
- **Bug Reports & Feature Requests**: submit an issue on the [GitHub Issue Tracker](https://github.com/lingyicute/YiMatches/issues).
- **Pull Requests**: keep the single-file, zero-dependency philosophy intact and match the existing code style.
- **Translations**: the interface is currently Simplified Chinese — an i18n layer plus translated string tables would be very welcome.

<br>

## 📄 License

```text
Copyright (C) 2026 lingyicute <li@92li.uk>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program. If not, see <https://www.gnu.org/licenses/>.
```
