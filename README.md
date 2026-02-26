# RTH Volume Profile Indicator for TradingView

A professional-grade Pine Script v6 indicator that displays both the **Previous Day (PD)** and **Developing** RTH Volume Profiles on any chart timeframe.

## Main Indicator

### [`RTH Volume profile.pine`](RTH%20VP/RTH%20Volume%20profile.pine)

The flagship indicator combining both PD and Developing profiles in a single overlay.

**Key Features:**
- **Dual Profiles** — Toggle PD and Developing profiles independently
- **1-Minute Precision** — Always uses 1-min data via `request.security_lower_tf`, accurate on any chart timeframe
- **RTH Session** — 09:30–15:59 (GMT-5); developing profile auto-promotes to PD at session end
- **Infinite Rays** — POC, VAH, VAL extend infinitely to the right
- **Price Scale Labels** — Levels plotted directly on the y-axis
- **Profile Classification** — Identifies p-Shape, b-Shape, or D-Shape distributions
- **Pre-allocated Grid** — Optimized computation, no GC overhead

## Documentation

See [`RTH volume profile usage.md`](RTH%20VP/RTH%20volume%20profile%20usage.md) for:
- Technical functions & logic breakdown
- Configuration settings guide
- Example analysis & trading strategies

## Quick Start

1. Open TradingView → Pine Editor → New blank indicator
2. Paste the contents of `RTH VP/RTH Volume profile.pine`
3. Save and Add to Chart
