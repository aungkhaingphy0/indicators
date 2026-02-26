# RTH Volume Profile: Technical Reference & Usage Guide

This document provides a deep dive into the logic, functions, and practical application of the **Previous Day and Today Volume profile** indicator.

## 1. Technical Functions & Logic

### A. Session Detection (RTH)
The indicator is specifically designed for **Regular Trading Hours (RTH)** based on the 09:30 – 15:59 (GMT-5) window.
- **Logic**: Uses `time("1", "0930-1559", "GMT-5")` to identify the session boundary at a 1-minute resolution.
- **Boundary**: The 16:00 bar marks the `sessEnd`, triggering the promotion of "Developing" data to "Previous Day" data.

### B. 1-Minute Data Integrity
Regardless of the chart timeframe (5m, 15m, 1h), the indicator calculates profiles using 1-minute granularity.
- **Function**: `request.security_lower_tf(syminfo.tickerid, "1", ...)` fetches intrabar OHLCV data.
- **Benefit**: Ensures precise POC/VA calculations that don't change based on the chart zoom level.

### C. Optimized Grid Computation
Instead of slow linear scans, the indicator uses a pre-allocated numerical grid.
- **Allocation**: A `MAX_BINS = 5000` array is pre-allocated on initialization (v2 optimization) to minimize garbage collection lag.
- **Distribution**: Every 1-minute bar's volume is distributed across the corresponding price bins using a weighted share calculation.
- **Efficiency**: Calculations for POC and Value Area only occur on confirmed bar closes (`barstate.isconfirmed`), preventing real-time "flicker" and high CPU usage.

### D. Session Promotion (Developing → PD)
At the close of the RTH session (16:00):
- The current day's profile (`dvPOC`, `dvVAH`, `dvVAL`) is copied to the `pd` variables.
- The `pType` (p-Shape, b-Shape, D-Shape) is calculated from the final session data.
- The developing data is cleared for the next day, while the PD levels remain fixed as horizontal rays.

---

## 2. General Usage

### Toggles
- **Show PD Volume Profile**: Displays the fixed levels (lines and labels) from the previous session.
- **Show Developing Volume Profile**: Displays the real-time building levels for the current live session.

### Configuration Settings
- **Value Area %**: Standard is 68% (one standard deviation). You can adjust this to 70% or 80% depending on your strategy.
- **Rows Layout**:
  - **Number of Rows**: Divides the session's high-low range into a fixed number of bins (e.g., 1000). Best for standard charts.
  - **Ticks Per Row**: Sets each bin to a fixed tick height (e.g., 4 ticks = 1 ES point). Best for precision and matching professional platforms like Sierra Chart.

### Style & Visuals
- **Infinite Rays**: POC/VAH/VAL lines extend infinitely to the right, ensuring you see the interaction with levels even if the session has long passed.
- **Price Scale Integration**: Values are plotted directly on the right-side price axis for a clean, professional look.
- **PD Table**: A color-coded summary table displays the previous session's profile type and key levels.

---

## 3. Example Analysis

### Profile Shapes
The indicator classifies the previous session into three primary shapes:

1.  **D-Shape (Balance)**
    - **Visual**: Volume is concentrated in the middle of the range.
    - **Analysis**: Indicates a balanced, non-trending market. Look for "mean reversion" trades where price bounces between VAH and VAL.
2.  **p-Shape (Bullish / Short Covering)**
    - **Visual**: Volume is concentrated at the top of the range; thin trading below.
    - **Analysis**: Often indicates a breakout or short-covering rally. The POC at the top acts as a strong support level for the next session.
3.  **b-Shape (Bearish / Long Liquidation)**
    - **Visual**: Volume is concentrated at the bottom of the range; thin trading above.
    - **Analysis**: Often indicates heavy selling or long liquidation. The POC at the bottom acts as a strong resistance level for the next session.

### Trading the Levels
- **Open Inside Value Area**: Indicates acceptance of yesterday's prices. Expect a range-bound day (choppy).
- **Open Outside Value Area**: Indicates an "unfair" price. If price sustains outside Value, expect a trend or "initiative" move in that direction.
- **POC Interaction**: The Point of Control is the most liquid price. It acts like a "magnet." If price is far from POC, it often wants to return to it. If it rejects POC sharply, it indicates strong trend sentiment.
