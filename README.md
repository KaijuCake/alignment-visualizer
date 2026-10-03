# Alignment Visualizer

An interactive **Needleman–Wunsch pairwise sequence alignment visualizer** for DNA sequences, implemented from scratch in vanilla JavaScript — no alignment libraries.

## Features

- **From-scratch implementation** — pure, commented functions: `buildScoringMatrix`, `traceback`, `formatAlignment`
- **Interactive DP scoring matrix** — hover (or tap) any filled cell to see exactly how its score was derived (diagonal / up / left)
- **Step-through animation** — play, pause, step, and reset the matrix fill cell-by-cell, with speed control; the current cell and its three predecessors are highlighted
- **Traceback path overlay** — toggle highlighting of the optimal alignment path through the matrix
- **Alignment results panel** — the two aligned sequences with color-coded matches, mismatches, and gaps, plus alignment score, percent identity, and gap count
- **Configurable scoring** — match, mismatch, and gap penalties (defaults +2 / −1 / −2)
- **Input validation** — ACGT-only sequences (case-insensitive, whitespace stripped), capped at 200 bases each to keep the O(n×m) matrix snappy
- **Preset examples** — one SNP difference, a pair requiring a gap, and a longer pair
- **"How it works" section** — a concise explainer of dynamic programming and traceback, written for undergraduates

## Run it

No build step, no dependencies. Open `index.html` in any modern browser — or enable GitHub Pages on this repo (Settings → Pages → Deploy from branch) for a live link.

## Background

This started as a teaching tool for [BASE (Biological Archive for Science & Education)](https://basebiologicalarchive.vercel.app/), a biology education platform. The long-term plan is to integrate it as an interactive `/tools/align` route there; this repo holds the standalone working prototype.

## The algorithm in 30 seconds

Needleman–Wunsch finds the optimal **global** alignment of two sequences with dynamic programming. It fills a scoring matrix where each cell `(i, j)` takes the best of three moves — align the two bases (diagonal), or insert a gap in either sequence (up / left) — then traces back from the bottom-right corner to recover the alignment. Try the presets and watch the matrix fill to see it happen.
