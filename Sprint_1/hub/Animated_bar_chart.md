# 📊 Power BI Animated Bar Chart -- Sales by Sub-Category Over Time

https://github.com/user-attachments/assets/1382ae7e-0319-42c6-bdde-ec758b6d6c6a

## Overview

This report explains the implementation of an **Animated Bar Chart** in
Power BI to visualize the **Sum of Sales** by **Sub-Category** across
**Year, Quarter, Month, and Day**. This animated visualization helps
track how sales performance changes dynamically over time.

------------------------------------------------------------------------
<img width="958" height="515" alt="5" src="https://github.com/user-attachments/assets/f63ccf4d-9673-4df6-9870-c657b281d529" />

## Visual Description

The visual used is an **Animated Bar Chart** with the following
configuration:

-   **Name (Category):** Sub-Category\
-   **Value (Measure):** Sum of Sales\
-   **Period (Animation Field):**
    -   Order Date → Year → Quarter → Month → Day

------------------------------------------------------------------------

## What is an Animated Bar Chart?

An Animated Bar Chart is a dynamic visual that: - Displays data changes
over time - Transitions automatically between time periods - Makes trend
analysis more visual and engaging - Helps users understand performance
evolution

------------------------------------------------------------------------

## Fields Used in This Visual

  Section   Field Used
  --------- ----------------------------------------
  Name      Sub-Category
  Value     Sum of Sales
  Period    Order Date (Year, Quarter, Month, Day)

------------------------------------------------------------------------

## Filters Applied

The following filters are available but currently set to **All**:

-   Order Date -- Year\
-   Order Date -- Quarter\
-   Order Date -- Month\
-   Order Date -- Day\
-   Sub-Category\
-   Sum of Sales

------------------------------------------------------------------------

## Key Observations from the Chart (Sample Frame)

-   **Copiers** show the highest sales (\~3000)
-   **Chairs** appear multiple times due to time-based changes
-   **Accessories** and **Bookcases** show steady growth patterns
-   **Phones** show comparatively lower sales in this frame

------------------------------------------------------------------------

## How the Animation Works

1.  The chart plays automatically through:
    -   Year → Quarter → Month → Day
2.  Bars rearrange based on sales values
3.  Rankings change dynamically based on performance
4.  Users can pause, replay, or manually scrub through time

------------------------------------------------------------------------

## Steps to Create Animated Bar Chart in Power BI

1.  Import dataset into Power BI.
2.  Get the **Animated Bar Chart** visual from AppSource.
3.  Drag **Sub-Category** into the *Name* field.
4.  Drag **Sum of Sales** into the *Value* field.
5.  Drag **Order Date hierarchy** into the *Period* field.
6.  Apply filters if required.
7.  Play the animation to visualize time-based changes.

------------------------------------------------------------------------

## Business Benefits

-   Helps detect **seasonal sales trends**
-   Identifies **fast-growing product categories**
-   Supports **forecasting and demand planning**
-   Enhances **dashboard storytelling**
-   Makes reports more **interactive and professional**

------------------------------------------------------------------------

## Conclusion

The Animated Bar Chart in Power BI is a powerful storytelling tool for
tracking sales movement across time. It transforms static data into an
engaging visual journey that supports strategic business decisions.

------------------------------------------------------------------------


