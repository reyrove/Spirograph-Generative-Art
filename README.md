# Spirograph — Generative Art

> A seed-based generative system for linked-arm curve compositions.  
> A reproducible catalogue of computational curve studies.

---

## What is this?

**Spirograph** is a generative design system built on a linked-arm chain. Two arms are joined at a moving pivot — the first rotates around the centre, the second rotates around the joint. The tip traces a single continuous curve that is neither random nor drawn: it is **the unavoidable product** of two sine waves with different speeds.

Every artwork in this catalogue is defined by a single numeric seed. The same seed always produces the identical composition — making each piece **traceable, reproducible, and licensable** across textile, print, and apparel applications.

Named for the mechanical toy that draws hypotrochoid curves, **Spirograph** rebuilds that logic in code and reframes it as a textile.

---

## Live

🌐 **[View the catalogue →](https://reyrove.github.io/Spirograph/)**

---

## The System

The generator combines two layers:

| Layer | Description |
|-------|-------------|
| **Linked arms** | Two arms joined at a pivot; each rotates at its own speed. |
| **Gradient stroke** | The curve is drawn as a gradient from background tone to foreground tone along its own length. |

Both layers are driven by the same seed, ensuring deterministic output.

### Parameters

- **Number of arms** — 2
- **Arm lengths** — derived from a seeded random sum vector
- **Rotation speeds** — a pair of values, each in `0.1` – `1.0`
- **Initial phases** — 0 to 2π per arm
- **Background gradient** — a diagonal blend of two seeded tones
- **Foreground** — a seeded highlight colour for the trace and tip

---

## Structure

```
Spirograph/
├── index.html              ← Full catalogue (single-file)
├── images/
│   ├── fav.svg
│   ├── spirograph-tote.png
│   ├── spirograph-cushion.png
│   └── ...
├── Spirograph.jpg          ← Apparel mockup
└── README.md
```

The entire project is contained in a single `index.html` — no build step, no framework. The only external dependency is **p5.js** (loaded from CDN), which drives the exact curve-rendering pipeline.

---

## Features

- **Seed-based generation** — every composition is deterministic and reproducible
- **Live animation** — the plate runs continuously; the cover and framed plate auto-stop after 30 seconds
- **Live catalogue** — cover, statement, plate, surfaces, process, archive, commission sections
- **Multiple surfaces** — print, scarf, textile, wallpaper — all rendered from the same seed
- **Archive of 8 seeds** — click any plate to load it into the main view
- **PNG export** — download the current frame of the plate directly from the browser
- **Keyboard shortcuts** — `R` for new seed, `S` to save
- **Legal modal** — licensing, terms, and credits built in
- **Responsive** — works on desktop, tablet, and mobile
- **Mobile-first navbar** — horizontally scrollable with fade hint

---

## Usage

### Generate a new composition

Click **New Seed** or press `R`.

### Download the current frame

Click **Download** or press `S`.

### Load a seed from the archive

Click any plate in the **Archive** section.

---

## Color System

Every composition is seeded with two values:

- **Background gradient** — a two-tone diagonal gradient drawn from the dark palette used by the other catalogues. Each seed picks two of them.
- **Foreground** — a single accent colour drawn from a bright palette of over 100 tones, used for the trace and the moving tip.

The trace itself is a **gradient** that runs from the first background tone through to the foreground colour, sampled along the length of the curve. Early segments sit near the background tone; the tip sits at the foreground colour. The result is a single continuous line whose colour evolves as it draws.

Because the seed picks both the palette and the arm geometry, no two seeds produce the same rhythm of colour and motion.

---

## Technical Notes

- **p5.js** drives the curve rendering, but only for the moving arms and pivots. The trace itself is drawn via raw Canvas 2D for performance.
- **Seeded randomness** for structural parameters (arm lengths, speeds, phases, colours) uses a Lehmer LCG.
- **Live plate** — 45fps, continuously animating.
- **Cover and framed plate** — 24fps, freeze after 30 seconds of animation.
- **Frozen stills** — the four surface swatches and eight archive thumbnails run for a small number of frames (800 and 400–600 respectively), then freeze.
- **Gradient pre-computed** — each instance builds a 128-colour gradient table at setup, so no colour allocation happens per frame.
- **Banded strokes** — the trace is drawn in colour bands (~128 stroke calls per frame), not per-segment (~1500), while preserving the exact visual gradient.
- **Off-screen pause** — an `IntersectionObserver` calls `noLoop()` on live instances that scroll out of view.
- **Shadow disabled below 320px** — the archive thumbnails skip the shadow render, which is invisible at that size.
- **DPR capped at 1.5** — a meaningful pixel-count saving on retina displays with no perceptible difference on a line drawing.
- `prefers-reduced-motion` respected.

---

## About

**Spirograph** is a project by [Reyhaneh Daneshdoost](https://reyrove.github.io/) — an Iranian-born artist working at the intersection of classical textile logic and generative systems.

The work begins with a simple observation: the woven surface — repetitive, mathematically structured, infinitely variable — has always been a form of computation, long before computers.

**Spirograph** is an attempt to render that logic visible.

> *A curve drawn by a joint in motion cannot repeat — it can only return, shifted.*

---

## Licensing

All compositions are seed-documented and available for licensing across textile, surface, and apparel applications.

For commercial use, custom editions, or exclusive rights:

📧 **reyhanehdaneshdoost@gmail.com**

See the **Licensing** section in the live catalogue for details.

---

## Links

- 🌐 [Website](https://reyrove.github.io/)
- 📷 [Instagram](https://www.instagram.com/rey._.rove/)
- 💼 [LinkedIn](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- 🐦 [X](https://x.com/reyrove)

---

## Credits

**Design & Generative System**  
Reyhaneh Daneshdoost

**Typefaces**  
Cormorant Garamond · DM Mono

**Edition**  
Spirograph — Autumn 2026

---

<p align="center">
  <em>Generative Linked-Arm Curve</em><br />
  <sub>© Reyrove Studio · All compositions reproducible by seed</sub>
</p>