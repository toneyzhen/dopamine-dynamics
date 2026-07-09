# happy-hormones-dynamics

**▶ [View the live chart](https://htmlpreview.github.io/?https://github.com/toneyzhen/happy-hormones-dynamics/blob/main/index.html)** — runs right in your browser, no download needed.

An interactive explorer for the four "happy hormones" — **DOSE: Dopamine, Oxytocin, Serotonin, and Endorphins.** Pick a hormone tab, then click activities to plot how they tend to affect its level over time. Each hormone has two groups: **positive ways to boost it** (green — a gentle rise and sustained plateau) and **shortcuts that backfire** (red — a hard spike, then a crash below baseline). Hover the chart to read values at any point in time.

> **Heads up:** The "happy hormones" (DOSE) are a popular framework, not precise science, and the curves are **illustrative, not measured data.** See [About the data](#about-the-data) below.

## Demo

Live version: **[htmlpreview.github.io](https://htmlpreview.github.io/?https://github.com/toneyzhen/happy-hormones-dynamics/blob/main/index.html)**

## Features

- **Four hormone tabs** — Dopamine, Oxytocin, Serotonin, Endorphins — each re-themes the page in its own color
- Two toggle groups per hormone: **positive boosts** and **shortcuts to avoid**
- 62 activity curves in total (up to 16 per hormone)
- Checkbox-style toggles that show both the selection state and each line's color
- A dashed **baseline** line so you can see rises above and crashes below it
- **Hover tooltip** with a crosshair showing each active curve's value at that time
- **Reset** button to clear the chart
- Light and dark mode (follows your system setting)
- Responsive layout down to mobile
- Respects `prefers-reduced-motion`
- **Zero dependencies** — a single self-contained HTML file, no build step, no network access required

## Customizing

Everything lives in one `HORMONES` array near the top of the `<script>` block in `index.html`. Each hormone has a `pos` list (healthy boosts) and a `neg` list (shortcuts to avoid). Line colors are assigned automatically from built-in palettes, so you only supply a label and a curve shape.

**Boost** entry (`pos`) — gentle rise, sustained plateau, easing return:

```js
{ label:'Exercise',
  amp:40,   // plateau height above baseline
  t1:1.4,   // when the rise levels off (hours)
  t2:6.5,   // when it starts easing back down (hours)
  k:0.8 }   // smoothness of the rise/fall
```

**Shortcut** entry (`neg`) — sharp spike, then a crash below baseline:

```js
{ label:'Social media',
  peak:95,  // spike height above baseline
  tau:0.6,  // how quickly it peaks (smaller = faster)
  dip:28,   // depth of the crash below baseline
  tc:2.6,   // when the crash bottoms out (hours)
  w:1.6 }   // how wide/drawn-out the crash is
```

To add a whole new hormone, copy one of the four objects in `HORMONES` and give it a `name`, an `accent` color, a short `role` and `desc`, and its own `pos`/`neg` lists.

Global knobs, also near the top of the script:

- `BASE` — the baseline level (default `50`)
- `TMAX` — length of the time axis in hours (default `12`)
- `YMIN` / `YMAX` — vertical scale of the chart (default `0`–`155`)

## About the data

These curves are a **teaching metaphor, not a measurement.** Every value — the baseline, the axis scales, and each activity's peak, dip, and timing — was hand-picked to produce a recognizable *shape*, then rendered with two simple formulas (a spike-plus-dip for shortcuts, a smooth rise-and-fall plateau for healthy boosts).

The qualitative idea is loosely grounded in popular neuroscience writing (e.g. Anna Lembke's *Dopamine Nation*) and concepts like reward prediction error and receptor downregulation after overstimulation: fast, potent chemical shortcuts tend to produce large, brief surges followed by a dip below baseline, while slower, effortful activities produce smaller but more sustained changes.

Real neurochemistry is far messier than clean lines — the four hormones overlap and interact, they operate on very different timescales in specific brain regions, "level" isn't a single quantity you'd plot in hours, and actual magnitudes vary enormously by activity, dose, person, and context. **Don't treat these curves as empirical findings.**

The items in the red "shortcuts" group (junk food, gambling, drugs, alcohol, chasing validation, and so on) are flagged as things to **avoid** — they are not recommendations, there are no instructions for any of them, and **nothing here is medical advice.**