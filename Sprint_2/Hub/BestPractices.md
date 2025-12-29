# Complete Power BI Dashboard Development Guide

## Table of Contents
1. [Understanding BI Dashboards](#understanding-bi-dashboards)
2. [Dashboard Design Best Practices](#dashboard-design-best-practices)
3. [Drill-Through Functionality](#drill-through-functionality)
4. [Bookmarks for Different Views](#bookmarks-for-different-views)
5. [Navigation Buttons and Reset Filters](#navigation-buttons-and-reset-filters)
6. [Consistent Color Themes and Branding](#consistent-color-themes-and-branding)
7. [Custom Tooltips](#custom-tooltips)
8. [Power BI Best Practices Documentation](#power-bi-best-practices-documentation)
9. [Reducing Data Model Size](#reducing-data-model-size)
10. [Implementing Proper Data Types](#implementing-proper-data-types)
11. [Creating Aggregated Tables](#creating-aggregated-tables)
12. [Testing Dashboard Performance](#testing-dashboard-performance)
13. [Complete Project Examples](#complete-project-examples)

---

## Understanding BI Dashboards

### What is a BI Dashboard?

A **Business Intelligence (BI) Dashboard** is like the control panel of a car, but for your business data. Instead of showing speed and fuel, it shows sales, performance, customer behavior, and other important business metrics—all in one place with charts, graphs, and numbers that update automatically.

**Power BI** is Microsoft's tool for creating these dashboards. Think of it as a smart way to turn boring Excel spreadsheets into interactive, visual stories that help people make decisions.

### Key Components of a Power BI Dashboard

- **Visuals:** Charts, graphs, tables, maps
- **Filters & Slicers:** Controls to narrow down data
- **KPIs:** Big numbers showing key metrics
- **Navigation:** Buttons to move between pages
- **Interactivity:** Click, hover, drill-down capabilities

---

## Dashboard Design Best Practices

### Core UX Principles

**The 5-Second Rule:** Users should understand the main message within 5 seconds of viewing the dashboard.

**F-Pattern Layout:** People read top-to-bottom, left-to-right. Structure your dashboard accordingly:
```
┌─────────────────────────────────────┐
│ [Most Important Info - Top Left]    │ ← Users look here FIRST
├─────────────────────────────────────┤
│ [Supporting Charts - Middle]        │
├─────────────────────────────────────┤
│ [Detailed Data - Bottom]            │
└─────────────────────────────────────┘
```

**Key Principles:**

1. **Less is More:** Don't cram everything on one page
   - Limit to 7-10 visuals per page
   - Use multiple pages instead of overcrowding

2. **Hierarchy of Information:**
   - Top: KPIs (What matters most?)
   - Middle: Trends and comparisons (Why does it matter?)
   - Bottom: Details (What are the specifics?)

3. **Consistency:**
   - Same colors mean the same things throughout
   - Same layout pattern across pages
   - Consistent placement of navigation elements

4. **White Space:**
   - Don't fill every pixel
   - Give visuals room to breathe
   - Improves readability

5. **Mobile-Friendly:**
   - Test on **View → Mobile layout**
   - Stack visuals vertically for mobile
   - Ensure touch targets are large enough

### Visual Selection Guide

| **Data Type** | **Best Visual** | **When to Use** |
|---------------|-----------------|-----------------|
| Single KPI | Card or KPI visual | Highlight one important number |
| Trend over time | Line chart | Show changes across time periods |
| Comparison | Bar or column chart | Compare categories or groups |
| Proportion | Pie or donut chart | Show parts of a whole (max 5-7 slices) |
| Geographic | Map | Display location-based data |
| Relationship | Scatter chart | Show correlation between two metrics |
| Ranking | Bar chart (sorted) | Show top/bottom performers |
| Distribution | Histogram | Show frequency distribution |

---

## Drill-Through Functionality

### What is Drill-Through?

Drill-through is like clicking a link that takes you to more details. Click on "January Sales" on Page 1, and it automatically opens Page 2 showing only January's details.

### Step-by-Step Implementation

**Step 1: Plan Your Drill-Through Path**

Decide the journey:
```
Summary Page → Detail Page
(e.g., Regional Sales Overview → Specific Region Details)
```

**Step 2: Create Your Pages**
- Page 1: "Sales Overview" (Summary)
- Page 2: "Sales Details" (Destination)

**Step 3: Set Up Drill-Through on Destination Page**

1. Navigate to Page 2 (your detail page)
2. In the **Visualizations pane** (right side), find the **Drill through** section
3. Drag a field into the **Drill through** box (e.g., "Region", "Product", "Month")
4. Power BI automatically adds a **back arrow button**

**Step 4: Customize Drill-Through Settings**

1. Select the drill-through field in the well
2. In the dropdown, choose:
   - **Keep all filters:** Maintains all active filters when drilling through
   - **Cross-report drill through:** Allow drilling to reports in other workspaces

**Step 5: Test the Drill-Through**

1. Go to Page 1 (source page)
2. Right-click any data point in a visual
3. You'll see **Drill through** option with your page name
4. Click it → automatically jumps to Page 2 with filtered data

### Live Example

**Scenario: Sales Dashboard**

**Page 1: Regional Performance**
```
Bar chart showing Total Sales by Region:
North: $500K
South: $350K
East: $420K
West: $380K
```

**Action:**
Right-click "North" bar → Select **Drill through → Regional Details**

**Page 2: Regional Details** (automatically shows only North region data)
```
[← Back Button]  ← Auto-generated

Region: NORTH

┌─────────────────────────────────┐
│ Sales by Product Category       │
│ Electronics: $200K              │
│ Furniture: $150K                │
│ Supplies: $150K                 │
└─────────────────────────────────┘

┌─────────────────────────────────┐
│ Monthly Trend for North Region  │
│ (Line chart)                    │
└─────────────────────────────────┘
```

### Advanced Drill-Through Techniques

**Multiple Drill-Through Fields:**
- Add multiple fields to drill-through well
- User can drill through on combination (e.g., Region + Product)

**Conditional Drill-Through:**
- Create multiple detail pages
- Different drill-through targets based on context
- Example: Product details page + Customer details page

**Cross-Report Drill-Through:**
1. Enable in drill-through settings
2. Users can drill from one report to another
3. Useful for connected dashboards

---

## Bookmarks for Different Views

### What are Bookmarks?

Bookmarks save the current state of a page—like taking a snapshot. You can save different filter combinations, visible visuals, and selections, then switch between them with a button click.

### When to Use Bookmarks

- **Scenario Comparison:** View 2024 vs 2023 data
- **Different Perspectives:** Manager view vs Executive view
- **Hide/Show Details:** Toggle between summary and detailed view
- **Story Telling:** Create a guided tour through your data

### Step-by-Step Creation

**Step 1: Prepare Your First View**

1. Open your report page
2. Apply filters (e.g., Year = 2024)
3. Select specific visuals to highlight
4. Set slicers to specific values
5. Hide any visuals you don't want visible (View → Selection pane → Hide)

**Step 2: Create the Bookmark**

1. Go to **View** tab → Click **Bookmarks Pane**
2. Click **Add** button (or right-click in pane → Add)
3. Name it descriptively: "2024 View" or "Executive Summary"

**Step 3: Configure Bookmark Properties**

Right-click the bookmark → **Data, Display, Current Page**

Options explained:
- **Data:** Captures filter states and slicers
- **Display:** Captures which visuals are visible/hidden
- **Current Page:** Remembers which page is shown
- **Selected visuals:** Only captures state of selected visuals (not entire page)

**Step 4: Create Additional Bookmarks**

1. Change your view (different filters, visible visuals)
2. Create another bookmark: "2023 View"
3. Repeat for as many views as needed

**Step 5: Update Existing Bookmarks**

If you need to modify a bookmark:
1. Set up the page the way you want
2. Right-click the bookmark → **Update**

### Linking Bookmarks to Buttons

**Create Interactive Bookmark Buttons:**

1. **Insert a button:**
   - **Insert** tab → **Buttons** → **Blank** (or choose a style)

2. **Style the button:**
   - Select button
   - In **Format** pane → **Style** section
   - Set Fill color, Border, Text
   - Add text: Click button, type in formula bar or add text box overlay

3. **Link to bookmark:**
   - With button selected
   - **Format** pane → **Action** → Toggle ON
   - **Type:** Bookmark
   - **Bookmark:** Select your bookmark from dropdown

4. **Repeat for other bookmarks**

**Example Button Setup:**

```
Top of dashboard:
┌──────────┬──────────┬──────────┬──────────┐
│ 2024 View│ 2023 View│ Top 10   │  Reset   │
└──────────┴──────────┴──────────┴──────────┘
     ↓          ↓          ↓          ↓
  Bookmark1  Bookmark2  Bookmark3  Bookmark4
```

### Advanced Bookmark Techniques

**Selection Pane for Show/Hide:**

1. **View → Selection**
2. Eye icons control visibility
3. Create multiple versions of same page with different visuals visible
4. Each bookmark captures different visibility states

**Example - Three Views on Same Page:**

**View 1: Charts Only**
- Charts: Visible ✓
- Tables: Hidden ✗

**View 2: Tables Only**
- Charts: Hidden ✗
- Tables: Visible ✓

**View 3: Everything**
- Charts: Visible ✓
- Tables: Visible ✓

**Bookmark Navigator:**

Create a "homepage" with large buttons:
```
┌─────────────────────────────────┐
│     SALES DASHBOARD HOME        │
├─────────────────────────────────┤
│  ┌───────────┐  ┌───────────┐  │
│  │  Current  │  │   Last    │  │
│  │   Year    │  │   Year    │  │
│  └───────────┘  └───────────┘  │
│  ┌───────────┐  ┌───────────┐  │
│  │    Top    │  │  Regional │  │
│  │ Performers│  │   View    │  │
│  └───────────┘  └───────────┘  │
└─────────────────────────────────┘
```

---

## Navigation Buttons and Reset Filters

### Types of Navigation Buttons

1. **Page Navigation:** Move between report pages
2. **Bookmark Navigation:** Switch views on same page
3. **Reset Filters:** Clear all applied filters
4. **Back Button:** Return to previous page/state
5. **Web URL:** Link to external resources

### Creating Page Navigation Buttons

**Step 1: Insert Button**

1. **Insert** tab → **Buttons** → Choose a style:
   - **Blank:** Fully customizable
   - **Arrow:** Navigation with arrow icon
   - **Info:** Information symbol
   - **Custom image:** Upload your own

**Step 2: Configure Navigation**

1. Select the button
2. **Format** pane → **Action** → Toggle **ON**
3. **Type:** Page navigation
4. **Destination:** Select target page

**Step 3: Style the Button**

In **Format** pane:
- **Shape:** Adjust size, fill color, border
- **Text:** Add label, font size, alignment
- **Icon:** Add icons (optional)
- **Shadow:** Add depth (optional)
- **Rotation:** For creative layouts

**Step 4: Add Button Text**

Two methods:
1. With button selected, type directly in formula bar
2. Add text box overlaying button (more flexible formatting)

### Creating "Reset All Filters" Button

This is a special bookmark-based button that clears all filters.

**Step 1: Create a Clean State**

1. Clear ALL filters from your report page
2. Clear ALL slicer selections
3. Ensure page is in default state

**Step 2: Create "Reset" Bookmark**

1. **View → Bookmarks pane**
2. Click **Add**
3. Name it "Reset All Filters"
4. Right-click bookmark → ensure **Data** is checked (Display unchecked)

**Step 3: Create Reset Button**

1. **Insert → Buttons → Blank**
2. Add text: "Reset Filters" or "Clear All"
3. **Format → Action → ON**
4. **Type:** Bookmark
5. **Bookmark:** Select "Reset All Filters"

**Alternative Method: Using Slicer Clear Button**

For individual slicers:
1. Select slicer
2. **Format → Slicer header → ON**
3. Enable **Clear button**
4. A small X appears on slicer to clear selections

### Navigation Bar Best Practices

**Consistent Placement:**
- Top: Horizontal navigation bar (most common)
- Left: Vertical sidebar navigation
- Bottom: Footer navigation (less common)

**Standard Navigation Layout:**

```
┌─────────────────────────────────────────┐
│ [Home] [Sales] [Products] [Customers]   │ ← Pages
│                              [Reset]     │ ← Utility
└─────────────────────────────────────────┘
```

**Visual Hierarchy:**
- Primary navigation: Larger, more prominent
- Secondary actions: Smaller, subtle
- Reset/Clear: Distinct color (e.g., red or gray)

**Button States:**

Use button formatting for different states:
1. **Default:** Normal appearance
2. **On hover:** Slightly darker or outlined (Format → Visual → On hover)
3. **On press:** Even darker (Format → Visual → On press)
4. **Selected:** Bold or different color to show current page

---

## Consistent Color Themes and Branding

### Why Color Consistency Matters

- **Professional appearance:** Looks polished and trustworthy
- **Faster comprehension:** Users recognize meaning instantly
- **Brand alignment:** Reinforces company identity
- **Accessibility:** Ensures readability for all users

### Color Psychology in Dashboards

| **Color** | **Meaning** | **Best Used For** |
|-----------|-------------|-------------------|
| Green | Positive, growth, success | Profits, achievements, targets met |
| Red | Negative, alert, urgent | Losses, problems, targets missed |
| Blue | Neutral, trustworthy, calm | Revenue, information, default |
| Yellow/Orange | Warning, caution | Approaching limits, moderate alerts |
| Gray | Neutral, inactive | Disabled items, secondary info |
| Purple | Premium, creative | Special segments, VIP customers |

### Creating a Custom Theme

**Step 1: Plan Your Color Palette**

Decide on:
- **Primary colors:** 2-3 main brand colors
- **Data colors:** 6-10 colors for charts
- **Sentiment colors:** Green (good), Red (bad), Yellow (caution)
- **Text colors:** Dark for body, medium for secondary
- **Background colors:** Light neutrals

**Example Palette:**
```
Primary: #0066CC (Brand Blue)
Secondary: #00A651 (Brand Green)
Accent: #FF6600 (Orange)

Data Colors: #0066CC, #00A651, #FFB600, #8B4789, #D32F2F, #00897B
Good: #00A651 (Green)
Bad: #D32F2F (Red)
Warning: #FFB600 (Yellow)

Text: #333333 (Dark Gray)
Background: #FFFFFF (White)
Secondary BG: #F5F5F5 (Light Gray)
```

**Step 2: Create Theme JSON File**

Method 1: Start from Built-in Theme
1. **View → Themes → Customize current theme**
2. Modify colors in the interface
3. **Save current theme** → Exports as JSON

Method 2: Create JSON Manually

Create a text file named `MyCompanyTheme.json`:

```json
{
  "name": "My Company Theme",
  "dataColors": [
    "#0066CC",
    "#00A651",
    "#FFB600",
    "#8B4789",
    "#D32F2F",
    "#00897B",
    "#FF6600",
    "#5E35B1"
  ],
  "good": "#00A651",
  "neutral": "#FFB600",
  "bad": "#D32F2F",
  "maximum": "#D32F2F",
  "center": "#FFB600",
  "minimum": "#00A651",
  "foreground": "#333333",
  "background": "#FFFFFF",
  "tableAccent": "#0066CC"
}
```

**Step 3: Apply Theme to Report**

1. **View → Themes → Browse for themes**
2. Select your JSON file
3. Click **Open**
4. Theme applies to entire report

**Step 4: Apply to All Future Reports**

Save as default:
1. Apply your theme
2. Save the .pbix file as a template
3. Use this template for new projects

### Applying Branding Elements

**Logo Placement:**

1. **Insert → Image**
2. Place logo in consistent location (top-left or top-right)
3. **Format → Image → Size:** Keep reasonable (not too large)
4. On **Format pane → General → Properties:** 
   - Lock aspect ratio
   - Set **Alt text** for accessibility

**Repeat on All Pages:**
- Insert image on first page
- Copy (Ctrl+C)
- Paste on other pages (Ctrl+V) in exact same position

**Custom Fonts:**

1. **Format → Text**
2. Choose fonts that match brand guidelines
3. Recommended approach:
   - **Titles:** Bold, larger size (18-24pt)
   - **Body:** Regular, readable size (11-14pt)
   - **Labels:** Smaller, 9-11pt

**Consistent Visual Formatting:**

Create a "master visual" with perfect formatting:
1. Format one visual completely (colors, fonts, borders)
2. **Format → Copy formatting** (paint brush icon)
3. Click other visuals to apply same formatting

Or use **Format Painter:**
1. Select formatted visual
2. **Home → Format painter**
3. Click target visual

### Color Coding Rules

**Apply Consistently Across All Dashboards:**

1. **Same Metric = Same Color Always**
   - Revenue always Blue
   - Profit always Green
   - Cost always Orange
   - Customer Count always Purple

2. **Conditional Formatting:**

For KPI cards showing performance:
```
> Target: Green (#00A651)
90-100% of Target: Yellow (#FFB600)
< 90% of Target: Red (#D32F2F)
```

3. **Category Colors:**

Assign colors to categories and stick to them:
```
Product Category A: Blue
Product Category B: Green
Product Category C: Orange
```

### Accessibility Considerations

**Color Contrast:**

- Text on background: Minimum 4.5:1 ratio
- Large text: Minimum 3:1 ratio
- Use tools like WebAIM Contrast Checker

**Don't Rely on Color Alone:**

Use multiple indicators:
- Color + Icon (✓ for good, ✗ for bad)
- Color + Label text
- Color + Pattern/texture

**Test for Color Blindness:**

- Avoid red-green combinations alone
- Use blue-orange for strong contrast
- Test with color blindness simulators

---

## Custom Tooltips

### What are Tooltips?

Tooltips are the small pop-ups that appear when you hover over data points. Custom tooltips let you show a mini-dashboard instead of just basic info.

**Default Tooltip:**
```
[Hover over bar]
Category: Electronics
Sales: $45,000
```

**Custom Tooltip:**
```
[Hover over bar]
┌─────────────────────────────┐
│ Electronics                 │
│ Sales: $45,000 (↑ 15%)     │
│ Target: $40,000 ✓          │
│ [Mini trend chart]          │
│ Top Product: Laptop X       │
└─────────────────────────────┘
```

### When to Use Custom Tooltips

✅ **Good use cases:**
- Show additional context without cluttering main view
- Display trend for a single data point
- Show related metrics (e.g., hover sales → see profit margin)
- Compare to target or previous period
- Display detailed breakdown

❌ **Avoid:**
- Don't make tooltips too complex (keep simple)
- Don't include interactive elements (buttons won't work)
- Don't exceed ~4-5 small visuals

### Creating Custom Tooltips

**Step 1: Create a Tooltip Page**

1. Add a new page to your report
2. Name it descriptively: "Sales Tooltip" or "Product Details Tooltip"

**Step 2: Configure as Tooltip Page**

1. With the new page selected
2. **Format → Page information** (paint roller icon in Visualizations pane)
3. Toggle **Allow use as tooltip** → **ON**
4. **Type:** Tooltip
5. Canvas size automatically becomes "Tooltip" size (320 x 240 pixels)

**Step 3: Design the Tooltip**

Keep it minimal and glanceable:

Example layout:
```
┌─────────────────────────────┐
│ [Product Name - auto-filter]│
├─────────────────────────────┤
│ ┌───────┐  ┌───────┐       │
│ │ Sales │  │Profit │       │
│ │ $45K  │  │  22%  │       │
│ └───────┘  └───────┘       │
├─────────────────────────────┤
│ [7-day trend - mini line]   │
├─────────────────────────────┤
│ vs Last Year: ↑ 15.2%      │
└─────────────────────────────┘
```

**Visual recommendations:**
- **Card visuals:** For KPIs (2-4 cards max)
- **Small line/bar chart:** Show quick trend
- **Text:** Brief labels, metrics
- **No slicers:** They won't work in tooltips
- **No buttons:** Navigation doesn't work

**Step 4: Apply Tooltip to Visual**

1. Go back to your main report page
2. Select the visual you want to add the tooltip to
3. **Format → Tooltip** section
4. **Type:** Report page
5. **Page:** Select your tooltip page
6. Optional: **Keep visual filters** if tooltip should respect main visual's filters

**Step 5: Test**

- Hover over data points on your main visual
- Tooltip should appear
- Should show data filtered to that specific point

### Advanced Tooltip Techniques

**Dynamic Tooltip Content:**

The tooltip automatically filters based on:
- The data point you hover over
- Fields used in the main visual's axis/legend

Example:
```
Main visual: Sales by Region (bar chart)
Tooltip page: Includes Region field

Hover "North" → Tooltip shows only North data
Hover "South" → Tooltip shows only South data
```

**Multiple Tooltips for Different Visuals:**

Create specialized tooltips:
- "Product Tooltip" → Details about products
- "Customer Tooltip" → Customer information
- "Time Tooltip" → Trend over time

Assign different tooltips to different visuals.

---

## Power BI Best Practices Documentation

### Why Document Best Practices?

- **Knowledge Transfer:** New team members understand standards
- **Consistency:** Everyone follows same approach
- **Quality Assurance:** Standards ensure quality output
- **Maintenance:** Easier to update and troubleshoot
- **Scalability:** Best practices enable growth

### What to Document

Create a **Power BI Style Guide** document covering:

#### 1. Naming Conventions

**Files:**
```
Format: [Department]_[ReportName]_[Version]_[Date].pbix
Example: Sales_MonthlyPerformance_v2_20240315.pbix
```

**Pages:**
```
Use descriptive, concise names
Good: "Sales Overview", "Regional Details", "Trend Analysis"
Bad: "Page1", "Stuff", "Report"
```

**Measures:**
```
Format: [Metric Name] - [Calculation Type]
Examples:
- Total Revenue
- Revenue YTD
- Revenue vs Target %
- Avg Order Value
```

**Columns:**
```
Use spaces, proper capitalization
Good: "Customer Name", "Order Date", "Product Category"
Bad: "customer_name", "ORDERDATE", "prodcat"
```

**Tables:**
```
Singular nouns for dimension tables: Customer, Product, Date
Plural for fact tables: Sales, Orders, Transactions
```

#### 2. Data Model Standards

**Star Schema Preferred:**
```
      ┌─────────┐
      │  Date   │
      └────┬────┘
           │
      ┌────┴────┐
      │  Sales  │ ← Fact Table (center)
      └────┬────┘
      ┌────┴────┬──────────┐
      │         │          │
 ┌────┴───┐ ┌──┴──────┐ ┌─┴────────┐
 │Customer│ │ Product │ │ Location │ ← Dimension Tables
 └────────┘ └─────────┘ └──────────┘
```

**Relationships:**
- Use single direction filtering where possible
- Many-to-one relationships preferred
- Avoid many-to-many when possible
- Always use proper date table

**Date Table Requirements:**
```
Must include:
- Complete date range (no gaps)
- Year, Quarter, Month, Week columns
- Fiscal period columns if applicable
- Holiday flags
- Marked as date table: Table tools → Mark as date table
```

#### 3. DAX Standards

**Formatting:**
```dax
// Good - Readable, formatted
Total Revenue = 
SUMX(
    Sales,
    Sales[Quantity] * Sales[Price]
)

// Bad - Hard to read
Total Revenue=SUMX(Sales,Sales[Quantity]*Sales[Price])
```

**Comments:**
```dax
// Use comments to explain complex logic
// Author: John Doe
// Date: 2024-03-15
// Purpose: Calculate revenue excluding returns

Revenue Excl Returns = 
CALCULATE(
    [Total Revenue],
    Sales[IsReturn] = FALSE
)
```

**Variables:**
```dax
// Use variables for:
// 1. Repeated calculations
// 2. Improved readability
// 3. Performance

Sales vs Target % = 
VAR CurrentSales = [Total Revenue]
VAR TargetSales = [Revenue Target]
VAR Variance = CurrentSales - TargetSales
RETURN
    DIVIDE(Variance, TargetSales, 0)
```

**Common Measures:**

Document standard measures everyone should use:
```dax
// Time Intelligence
YTD Sales = 
TOTALYTD([Total Revenue], 'Date'[Date])

Prior Year Sales = 
CALCULATE(
    [Total Revenue],
    SAMEPERIODLASTYEAR('Date'[Date])
)

YoY Growth % = 
VAR CurrentYear = [Total Revenue]
VAR PriorYear = [Prior Year Sales]
RETURN
    DIVIDE(CurrentYear - PriorYear, PriorYear, 0)
```

#### 4. Visual Standards

**Chart Selection Matrix:**

| **Use Case** | **Visual Type** | **Max Categories** |
|--------------|-----------------|-------------------|
| Single KPI | Card / KPI | 1 |
| Trend | Line chart | 1-5 lines |
| Comparison | Bar chart | 5-15 bars |
| Part-to-whole | Donut chart | 3-7 slices |
| Geographic | Map | Any |
| Correlation | Scatter | Any |
| Distribution | Histogram | Any |

**Formatting Standards:**

```
Titles:
- Font: Segoe UI
- Size: 12-14pt
- Color: #333333
- Position: Top-left of visual

Axis Labels:
- Font size: 10pt
- Always show units ($, %, K, M)
- Rotate if needed for readability

Data Labels:
- Use sparingly
- Only on key data points
- Format consistently ($1.2M not $1,234,567)

Gridlines:
- Minimal or none for clean look
- Light gray if needed (#E0E0E0)
```

#### 5. Performance Standards

**Target Metrics:**
```
Page load time: < 5 seconds
Visual rendering: < 2 seconds per visual
Report refresh: < 30 minutes (depending on data size)
Report size: < 1 GB (ideally < 500 MB)
```

**Optimization Checklist:**
- [ ] Remove unused columns and tables
- [ ] Use proper data types
- [ ] Create aggregated tables for large datasets
- [ ] Disable auto date/time
- [ ] Use calculated columns only when necessary (prefer measures)
- [ ] Reduce visual count per page (max 15)
- [ ] Optimize DAX measures

#### 6. Security & Sharing

**Row-Level Security (RLS):**
```
Document RLS roles:
- Sales Team: See only their region
- Managers: See their team's regions
- Executives: See all data

Example RLS expression:
[Region] = USERPRINCIPALNAME()
```

**Workspace Organization:**
```
Development Workspace: Work in progress
Test Workspace: User acceptance testing
Production Workspace: Published reports

Naming: [Department] - [Environment]
Example: Sales - Production
```

**Refresh Schedule:**
```
Document for each report:
- Frequency: Daily at 6 AM, Weekly on Monday, etc.
- Data sources: SQL Server, SharePoint, Excel files
- Dependencies: Report A must refresh before Report B
```

#### 7. Testing Checklist

Before publishing, verify:

**Functionality:**
- [ ] All filters work correctly
- [ ] Drill-through works
- [ ] Bookmarks switch views properly
- [ ] Navigation buttons go to correct pages
- [ ] Tooltips display properly
- [ ] Slicers sync across pages correctly

**Data Accuracy:**
- [ ] Totals match source systems
- [ ] Calculations are correct
- [ ] No blank/null values where unexpected
- [ ] Filters apply correctly
- [ ] Time intelligence measures are accurate

**Design:**
- [ ] Theme applied consistently
- [ ] Logo on all pages
- [ ] Proper alignment of visuals
- [ ] Consistent spacing
- [ ] No overlapping elements
- [ ] Mobile layout configured
- [ ] Accessible color contrast

**Performance:**
- [ ] Pages load in < 5 seconds
- [ ] No timeout errors
- [ ] Smooth interactions
- [ ] Report size reasonable

---

## Reducing Data Model Size

### Why Data Model Size Matters

**Performance Impact:**
- Larger models = Slower loading
- More data = Longer refresh times
- Too much data = Report timeout errors
- Impacts user experience significantly

**Power BI Limits:**
```
Power BI Pro: 1 GB per dataset
Power BI Premium: 10 GB+ (depending on capacity)
