# dopamine-dynamics

**▶ [View the live chart](https://htmlpreview.github.io/?https://github.com/toneyzhen/dopamine-dynamics/blob/main/index.html)** — runs right in your browser, no download needed.

An interactive chart that illustrates how different activities affect dopamine levels over time. Click any **high-dopamine trigger** or **healthy reset activity** to plot its curve. Triggers spike hard and crash below baseline; healthy activities rise more gently but stay elevated longer. Hover the chart to read values at any point in time.

> **Heads up:** The numbers in this chart are **illustrative, not measured data.** See [About the data](#about-the-data) below.

## Demo

Live version: **[htmlpreview.github.io](https://htmlpreview.github.io/?https://github.com/toneyzhen/dopamine-dynamics/blob/main/index.html)**

## Features

- Toggle up to 24 activity curves on and off
- A dashed **baseline** line so you can see rises above and crashes below it
- **Hover tooltip** with a crosshair showing each active curve's value at that time
- **Reset** button to clear the chart
- Light and dark mode (follows your system setting)
- Responsive layout down to mobile
- Respects `prefers-reduced-motion`
- **Zero dependencies** — a single self-contained HTML file, no build step, no network access required

## Customizing

All the activities are defined as two arrays near the top of the `<script>` block in `index.html`. Edit, add, or remove entries there — no other changes needed.

**Triggers** (sharp spike, then a crash below baseline):

```js
{ id:'social', label:'Social media', color:'#D4537E',
  peak:95,   // spike height above baseline
  tau:0.6,   // how quickly it peaks (smaller = faster)
  dip:28,    // depth of the crash below baseline
  tc:2.6,    // when the crash bottoms out (hours)
  w:1.6 }    // how wide/drawn-out the crash is
```

**Healthy activities** (gentle rise, sustained plateau, easing return):

```js
{ id:'exercise', label:'Exercise', color:'#1D9E75',
  amp:40,    // plateau height above baseline
  t1:1.4,    // when the rise begins to level off (hours)
  t2:6.5,    // when it starts easing back down (hours)
  k:0.8 }    // smoothness of the rise/fall
```

Other knobs, also near the top of the script:

- `BASE` — the baseline dopamine value (default `50`)
- `TMAX` — length of the time axis in hours (default `12`)
- `YMIN` / `YMAX` — vertical scale of the chart (default `0`–`150`)

## About the data

These curves are a **teaching metaphor, not a measurement.** Every value — the baseline, the axis scales, and each activity's peak, dip, and timing — was hand-picked to produce a recognizable *shape*, then rendered with two simple formulas (a spike-plus-dip for triggers, a smooth rise-and-fall plateau for healthy activities).

The qualitative idea is loosely grounded in popular neuroscience writing (e.g. Anna Lembke's *Dopamine Nation*) and concepts like reward prediction error and receptor downregulation after overstimulation: fast, potent rewards tend to produce large, brief surges followed by a dip below baseline, while slower, effortful activities produce smaller but more sustained changes.

Real dopamine dynamics are far messier than clean lines — they operate on sub-second timescales in specific brain regions, "level" isn't a single quantity you'd plot in hours, and actual magnitudes vary enormously by activity, dose, person, and context. **Don't treat these curves as empirical findings.**
