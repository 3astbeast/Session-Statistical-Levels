<p align="center">
  <img src="https://avatars.githubusercontent.com/u/209633456?v=4" width="160" alt="RedTail Indicators Logo"/>
</p>

<h1 align="center">Session Statistical Levels</h1>

<p align="center">
  <b>A percentile-based session range level indicator for NinjaTrader 8.</b><br>
  Tracks Asia, London, and NY sessions independently, calculates historical range distributions, and projects statistical levels from the current session's open.
</p>

<p align="center">
  <a href="https://buymeacoffee.com/dmwyzlxstj">
    <img src="https://img.shields.io/badge/☕_Buy_Me_a_Coffee-FFDD00?style=flat-square&logo=buy-me-a-coffee&logoColor=black" alt="Buy Me a Coffee"/>
  </a>
</p>

---

## Credit

Original TradingView Pine Script by **[@notprofessorgreen](https://twitter.com/notprofgreen)**. 

---

## Overview

Session Statistical Levels answers a simple question: "Based on the last N sessions, how far is price likely to move from here?" It tracks three global trading sessions (Asia, London, NY) plus an optional custom session, records their ranges over a configurable lookback period, then projects percentile-based levels symmetrically above and below the current session's opening price. The result is a data-driven framework of expected range boundaries that updates automatically at the start of each session.

---

## Sessions

Each session is tracked independently with its own range history, level calculations, and display.

- **Asia** — 7:00 PM – 2:00 AM ET (crosses midnight)
- **London** — 2:00 AM – 8:00 AM ET
- **NY** — 8:00 AM – 4:00 PM ET
- **Custom** — Configurable HHMM start/end in ET with a custom label

Each session can be toggled on or off independently. All times are in Eastern Time.

---

## Statistical Levels

At the start of each session, the indicator computes percentiles from the historical range distribution and projects them as horizontal levels from the session open price. All levels are drawn symmetrically above and below.

**Median (P50)** — The 50th percentile of historical session ranges. The "typical" session move.

**IQR Band (P25/P75)** — Interquartile range. 50% of sessions have stayed within this band.

**P10/P90** — The 10th and 90th percentile extremes. Only 10% of sessions move beyond the P90 level.

**P95** — 95th percentile for identifying historically extreme sessions. Disabled by default.

**Mean** — Average historical range, with an optional ±1 standard deviation band for distribution width context.

Each level type can be independently toggled on or off.

---

## Directional MAE/MFE Levels

Beyond raw range percentiles, the indicator separates historical sessions by direction (bullish vs bearish) and tracks how far price moved in favor of and against the opening direction.

**Bullish Sessions:**
- **Bull MFE50** — Median upside from open on bullish days
- **Bull MFE75** — 75th percentile upside on bullish days
- **Bull MAE50** — Median downside from open on bullish days (how far it dipped before going up)

**Bearish Sessions:**
- **Bear MFE50** — Median downside from open on bearish days
- **Bear MFE75** — 75th percentile downside on bearish days
- **Bear MAE50** — Median upside from open on bearish days (how far it bounced before going down)

These levels give you directional context that symmetric range levels can't — particularly useful when you have a directional bias and want to know where the typical pullback and target zones are.

---

## Fill Shading

Optional semi-transparent fills between the upper and lower bands for quick visual range assessment. IQR and P90 fills are independently configurable.

---

## Stats Table

An on-chart statistics table rendered via SharpDX showing per-session data at a glance:

- Session name with bull/bear count
- Total number of sessions in the lookback
- P25, P50 (Median), P75, P90 values
- Mean and standard deviation

The table is positionable at any corner of the chart (Top Left, Top Right, Bottom Left, Bottom Right).

---

## Configuration

**Lookback Sessions** — Number of historical sessions used for percentile calculations. Default: 100. 50+ recommended for stable percentiles.

**Label Size** — Tiny, Small, or Normal for all level labels.

**Style** — Independent color settings for every level type: Median, IQR, P10/P90, P95, Mean, StDev, MAE, MFE, plus IQR and P90 fill colors.

---

## Installation

1. Download the `.cs` file from this repository
2. Open NinjaTrader 8
3. Go to **Tools → Import → NinjaScript Add-On**
4. Select the downloaded file and click **OK**
5. The indicator will appear in your **Indicators** list — add it to any chart

---

## Part of the RedTail Indicators Suite

This indicator is part of the [RedTail Indicators](https://github.com/3astbeast/RedTailIndicators) collection — free NinjaTrader 8 tools built for futures traders who demand precision.

---

<p align="center">
  <a href="https://buymeacoffee.com/dmwyzlxstj">
    <img src="https://img.shields.io/badge/☕_Buy_Me_a_Coffee-Support_My_Work-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black" alt="Buy Me a Coffee"/>
  </a>
</p>
