# Usage & Configuration

The indicators in this repository are designed to visualize Regular Trading Hours (RTH) Volume Profiles. The **Combined** version is the most feature-rich, while standalone scripts provide modular options.

## Features (Combined Indicator)

The `volume_profile_combined.pine` script offers:
*   **Dual View**: View both Previous Day (PD) and Developing profiles simultaneously or independently.
*   **Infinite Rays**: POC, VAH, and VAL lines extend infinitely to the right (`extend.right`), making it easy to see how current price interacts with historical levels.
*   **Price Scale labels**: Levels are automatically labeled on the right-side price scale (y-axis), reducing chart clutter.
*   **Session Promoter**: At exactly 16:00 (RTH close), the developing profile is "promoted" to the PD profile. Before 09:30, only the PD profile is visible.
*   **Profile Shape**: Classifies the PD session as `p-Shape`, `b-Shape`, or `D-Shape` based on volume distribution, displayed in a summary table.

## Configuration Inputs

### Toggles (Combined Only)
*   **Show PD Volume Profile**: Toggle the previous day's fixed levels.
*   **Show Developing Volume Profile**: Toggle the current day's real-time building profile.

### Calculation Settings
*   **Value Area %**: The percentage of volume included in the Value Area (default: `68%`).
*   **Rows Layout**: 
    *   `Number of Rows`: Divides the session price range into a fixed number of bins.
    *   `Ticks Per Row`: Each bin is a fixed height in ticks (e.g., 4 ticks for 1 ES point).
*   **Row Size**: The numeric value for the chosen layout.

### Visuals
*   **Style Groups**: Independent color and line style settings for PD and Developing profiles to distinguish them easily.
*   **Label Offset**: Adjust how many bars to the right the label boxes are placed.
*   **Label Position**: Choose to show labels on the `Left`, `Right`, or `Both` sides of the profiles.

## Interpreting the Data
*   **D-Shape**: Balanced market; volume concentrated in the middle.
*   **p-Shape**: Bullish bias/short covering; volume concentrated at the top.
*   **b-Shape**: Bearish bias/long liquidation; volume concentrated at the bottom.

