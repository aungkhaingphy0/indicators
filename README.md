# Volume Profile Indicators for TradingView

This repository contains custom Pine Script indicators for TradingView that calculate and visualize the Regular Trading Hours (RTH) Volume Profile for the previous day.

## Files Included

*   `volume_profile.pine`: Computes the RTH Volume Profile for the previous day using a standard fixed bin size approach. It identifies the profile shape (p-Shape, b-Shape, D-Shape) and outlines the Point of Control (POC), Value Area High (VAH), and Value Area Low (VAL).
*   `volume_profile_rows.pine`: An advanced version that supports TradingView's Fixed Range Volume Profile (FRVP) "Rows Layout" and "Row Size" settings, using batch processing to construct the profile dynamically through a specified number of rows or ticks per row.

## Getting Started

Please see the [GUIDE.md](GUIDE.md) for instructions on how to add these scripts to your TradingView account, and [USAGE.md](USAGE.md) for details on how to configure and interpret the indicators.
