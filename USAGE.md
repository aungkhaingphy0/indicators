# Usage & Configuration

Both indicators provide similar core functionality but differ in how the volume bins are constructed.

## Overview

The indicators calculate the Volume Profile for the Regular Trading Hours (RTH) of the **previous session**. They present:
*   **POC (Point of Control):** The price level with the highest traded volume.
*   **VAH (Value Area High):** The upper boundary of the Value Area.
*   **VAL (Value Area Low):** The lower boundary of the Value Area.
*   **Profile Shape:** Classifies the previous day's trading behavior as a `p-Shape`, `b-Shape`, or `D-Shape`.
*   A statistical table on the middle-right of the screen summarizing the data.

## Configuration Inputs

When you add the indicator to your chart or double-click it, you can customize the following settings:

### Session
*   **Start/End Hour & Minute:** Defines your RTH session (default is 09:30 to 16:00).
*   **Timezone:** Must match the exchange or your preferred timezone (e.g., `America/New_York` or `GMT-5`).

### Volume Profile Calculations
*   **Value Area %:** The percentage of total volume to include in the Value Area (default: is typically `68%` or `70%`).

**In `volume_profile.pine`:**
*   **Bin Size (pts):** The absolute size of each volume bin. Increase this for high-priced instruments (like NVDA or SPX) to avoid array limits.

**In `volume_profile_rows.pine`:**
*   **Rows Layout:** Choose between `Number of Rows` or `Ticks Per Row` (matching TradingView's native FRVP).
*   **Row Size:** 
    *   If using `Number of Rows`, this divides the session range into `N` equal rows.
    *   If using `Ticks Per Row`, this sets the height of each row to `N` ticks.

### Style
*   Customize lines (POC, VAH, VAL colors, widths, styles), right extension lengths, and the background color of the data table.

## Interpreting the Data
*   **D-Shape:** Indicates a balanced market where volume is distributed normally around the middle of the range.
*   **p-Shape:** Indicates short-covering or an up-trend, with the bulk of the volume near the top.
*   **b-Shape:** Indicates long-liquidation or a down-trend, with the bulk of the volume near the bottom.
