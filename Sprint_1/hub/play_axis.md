# ▶️ Power BI Play Axis -- Time-Based Interactive Analysis

https://github.com/user-attachments/assets/410af968-d82d-4a5d-9b79-ebc3b1110fff

## Overview

This document explains how the **Play Axis** visual is imported and
applied in Power BI to create a **time-based interactive animation**
using the **Ship Date (Month & Day)** hierarchy. The Play Axis allows
users to control how visuals change dynamically over time using play,
pause, forward, and backward controls.

------------------------------------------------------------------------
<img width="956" height="515" alt="7" src="https://github.com/user-attachments/assets/a53e0970-0512-4b15-82b7-9da164c5b031" />

## Visual Description

The Play Axis is configured with the following setup:

-   **Axis Field:** Ship Date
    -   Hierarchy: Month → Day
-   **Control Buttons:**
    -   ▶️ Play
    -   ⏸ Pause
    -   ⏹ Stop
    -   ⏮ Previous
    -   ⏭ Next

This Play Axis is used to control the animation of the other visuals on
the report page.

------------------------------------------------------------------------

## What is the Play Axis in Power BI?

The Play Axis is a custom visual that: - Animates data over time -
Allows step-by-step playback of time-based data - Enables interactive
storytelling - Works like a timeline controller for reports

It is widely used for: - Sales trend animation - Monthly or daily data
playback - Performance change visualization

------------------------------------------------------------------------

## Dashboards Controlled by Play Axis

### 1. **Sum of Sales by Category (Pie Chart)**

Displays sales distribution across: - Technology - Furniture - Office
Supplies

### 2. **Sum of Profit & Sum of Quantity by Region (Clustered Column Chart)**

Displays performance comparison across: - West - East - South - Central

As the Play Axis runs, both visuals update dynamically based on the
selected time period.

------------------------------------------------------------------------

## Fields Used in This Setup

  Visual Component   Field Used
  ------------------ ----------------------------------------
  Play Axis          Ship Date (Month, Day)
  Pie Chart          Category, Sum of Sales
  Column Chart       Region, Sum of Profit, Sum of Quantity

------------------------------------------------------------------------

## Filters Applied

All filters are currently set to **(All)**:

-   Ship Date -- Month
-   Ship Date -- Day

This allows full animated playback across all time periods.

------------------------------------------------------------------------

## How the Animation Works

1.  User clicks the ▶️ **Play** button.
2.  The report automatically moves through:
    -   Month → Day
3.  Both charts update in real-time.
4.  Users can pause, move forward, or go backward manually.
5.  This creates a smooth **time-trend visualization experience**.

------------------------------------------------------------------------

## Steps to Add Play Axis in Power BI

1.  Open **Power BI Desktop**.
2.  Go to **AppSource (Get More Visuals)**.
3.  Search for **Play Axis**.
4.  Import the visual.
5.  Drag **Ship Date hierarchy** into the Play Axis field.
6.  Connect it with charts on the same page.
7.  Click ▶️ Play to animate the report.

------------------------------------------------------------------------

## Business Benefits

-   Makes reports **interactive and engaging**
-   Helps visualize **sales trends over time**
-   Supports **seasonal analysis**
-   Improves **executive storytelling**
-   Enhances **dashboard professionalism**

------------------------------------------------------------------------

## Conclusion

The Play Axis in Power BI transforms static dashboards into dynamic,
animated reports. It allows users to explore how sales, profit, and
quantity evolve over time with full playback control.

------------------------------------------------------------------------

