# Volume Profile Indicators for TradingView

This repository contains custom Pine Script indicators (v6) for TradingView that calculate and visualize the Regular Trading Hours (RTH) Volume Profile.

## Featured Indicator

*   **`volume_profile_combined.pine` (Recommended)**: The most advanced version. It combines both the **Previous Day (PD)** and **Developing** Volume Profiles into a single script.
    *   **Independent Toggles**: Turn PD or Developing profiles on/off separately.
    *   **Infinite Rays**: Levels extend infinitely to the right for clear level identification.
    *   **Price Scale Integration**: POC/VAH/VAL values are plotted directly on the price scale (y-axis).
    *   **RTH Session Logic**: Automatically handles the 09:30–16:00 (GMT-5) session, promoting the developing profile to the PD profile at the close of each session.
    *   **Row-Based Layout**: Supports "Number of Rows" and "Ticks Per Row" layout settings.

## Standalone Indicators

*   **`volume_profile_rows.pine`**: Dedicated to the Previous Day (PD) Volume Profile with advanced row layout settings (Number of Rows or Ticks Per Row).
*   **`developing_volume_profile_rows.pine`**: Focused solely on the Developing Volume Profile for the current session.
*   **`volume_profile.pine` (Legacy)**: A simpler PD Volume Profile using a fixed bin size approach.

## Getting Started

Please see the [GUIDE.md](GUIDE.md) for instructions on how to add these scripts to your TradingView account, and [USAGE.md](USAGE.md) for details on how to configure and interpret the indicators.

