# 🍩 Overview of Donut Chart in Power BI

🖥️ A Donut Chart is like a pie chart with a hole — it shows parts of a whole while leaving a center area for labels or summary metrics. 

🟣 How to create a Donut Chart in Power BI (step-by-step)

Open Power BI Desktop 📁

Get Data → CSV (or Excel) → select sample.csv → Load. 🔽

On the Report canvas, open the Visualizations pane and click the Donut chart icon (a pie with a hole). 🥯

In the Fields pane:

Drag Category to Legend. 🏷️

Drag Sales to Values. 🔢

Format the Donut (click the paintbrush icon 🎨):

Title → turn on and set a meaningful name (e.g., “Sales by Product”). 🏷️

Data labels → turn on; choose Percentage and/or Value. 🔍

Detail labels / Category labels → show category names on or beside slices.

Donut center → use the "Donut label" (if available) to show total sales or a summary measure (e.g., Total Sales). 🧾

Data colors → select consistent brand colors. 🎨

Legend → choose position (right, bottom) or disable if not needed. 📑

Add tooltip (optional): add another field to show extra info on hover (e.g., Year, Region). 🐭

Interaction & filters:

Add a Slicer (e.g., Year) to let users filter the donut interactively. 🔁

Make sure drill-throughs or cross-filtering behave the way you want. ↕️

Test interactivity: click slices to see cross-filtering on other visuals. ✅

# 🎨 Design tips & accessibility

Keep the number of categories small (5–8) to stay readable. 👓

Use contrasting colors for slices so differences are clear. 🌈

Show percentages—donut charts communicate part/whole best with % values. %✔️

If many small slices exist, consider grouping them into “Other”. ➕➡️📦

💾 Exporting (what to add to git)

Power BI .pbix files can be large—consider exporting visuals instead:

Recommended files to push to GitHub

README.md (this file) ✅

sample.csv (small dataset) ✅

exports/donut-chart.png (exported image) ✅

exports/donut-chart.pdf (optional) ✅

notes.md or how-to-open-pbix.md (usage notes) ✅

⚠️ If your .pbix is small and you want it in the repo, it's okay — but many teams prefer not to commit large binaries. Instead, store .pbix in a release or cloud storage (OneDrive/SharePoint).
