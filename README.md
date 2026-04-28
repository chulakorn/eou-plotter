# 🛢️ Ellipse of Uncertainty (EOU) Plotter

A lightweight, zero-dependency web app for visualizing and comparing **Wellbore Position Uncertainty** ellipses across multiple survey tools — built for drilling engineers in the oil & gas industry.

[Demo](chulakorn.github.io/eou-plotter)

---

## Screenshot

> Dark mode | Three survey tools compared

![EOU Plotter Screenshot](https://github.com/chulakorn/eou-plotter/blob/main/eou-plotter%20example.png)

---

## Features

| Feature | Details |
|---|---|
| **Multi-tool comparison** | Plot up to 3 survey tools simultaneously |
| **Unit system toggle** | Metric (m) / English (ft) |
| **Confidence level** | 1σ (1D/68%), 2σ (2D/95%), 3σ (3D/99.7%) |
| **Dark / Light mode** | One-click theme switch |
| **Clean axis scaling** | Ticks always snap to 0 / 5 multiples |
| **No install needed** | Pure HTML + CSS + JS, single file |

---

## Inputs

| Field | Description |
|---|---|
| **Unit System** | Metric (metres) or English (feet) |
| **Total Depth** | Well TD displayed at the center of the ellipse plot |
| **Tool Name** | Label for each survey tool (e.g. MWD+IFR2, GYD-OmegaX) |
| **Semi-Major (X-axis)** | EOU lateral half-axis for that tool |
| **Semi-Minor (Y-axis)** | EOU highside half-axis for that tool |
| **Confidence Level** | Display label only — 1D / 2D / 3D sigma |

> ⚠️ Confidence level is for **display reference only**. Enter semi-axes already scaled to your chosen sigma level from your survey tool's error model output.

---

## File Structure

```
eou-plotter/
├── index.html      ← Entire application (self-contained)
└── README.md       ← This file
```

No build tools. No npm. No server. One file runs everything.

---

## Background — What is EOU?

The **Ellipse of Uncertainty** is a standard representation in directional drilling to show the positional uncertainty of a wellbore at a given measured depth. It is derived from the **ISCWSA error model** applied to the survey tool's individual error terms.

- **Semi-Major axis** (Lateral / X) — uncertainty in the azimuthal direction
- **Semi-Minor axis** (Highside / Y) — uncertainty in the inclination direction
- **Confidence level** — 1σ ≈ 68% probability the true position falls within the ellipse; 3σ ≈ 99.7%

This tool is for **visual comparison** of different survey tools or configurations at a specific total depth.

---

## Typical Workflow

```
1. Run your survey tool error model (e.g. in SLB DOX or DrillPlan, Landmark COMPASS, Halliburton WellPlan, or NOV INTEQ)
2. Export the EOU value at your target depth for each tool
3. Enter values into this app
4. Compare ellipses visually side-by-side
```

---

## Customization

All styling is done with CSS variables at the top of `index.html`. To change colors, fonts, or layout — edit the `:root[data-theme="dark"]` and `:root[data-theme="light"]` blocks.

To add a 4th survey tool, duplicate one of the `field-group` blocks in the HTML and extend the `tools` loop in the JavaScript (`for (let i = 1; i <= 4; i++)`), adding a 4th entry to the `COLORS` and `COLORS_DIM` arrays.

---

## License

MIT — free to use, modify, and distribute.

---

*Built for drilling engineers. No cloud. No login. No tracking.*
