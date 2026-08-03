# Task 7 — DAX Measures & Analytical Insights

This is where DAX properly started — moving business logic out of Power Query and into measures that recalculate dynamically as someone filters a report

![Category-wise return rate](./Screenshots/category-return-rate.png)

**Skills:** DAX calculated columns · Explicit measures · Quick Measures · COUNT/DISTINCTCOUNT · Filter context validation · Statistical measures (AVERAGE, MAX, MIN)

## What I Did

**Getting oriented:** Before writing anything, I made sure I understood the split between Calculated Columns (computed row-by-row, stored in the table) and Measures (computed on the fly, based on whatever's currently filtered). I created a dedicated `Measures` table to keep everything organized in one place rather than scattered across the model.

- **Why DAX runs differently from Power Query**: Power Query transforms and stores data at refresh time, so its results are fixed until the next refresh. DAX measures instead recalculate live, responding to whatever filters, slicers, or visuals are currently in context — which is exactly why they're the right tool for anything that needs to react to user interaction. Power Query stays the right tool for static transformations like cleaning, merging, and formatting before the data even loads.

**Calculated columns:** Added `Sales Amount = OrderQuantity * ProductPrice` in Fact_Sales, and a `Return Flag` in Fact_Returns using `IF(ReturnQuantity > 0, "Returned", "Not Returned")`.

**Core aggregation measures:** Built Total Sales Quantity, Total Sales Amount, Total Return Quantity, and Total Products Sold as explicit measures.

- **Implicit vs. explicit measures**: implicit ones are auto-generated the moment you drag a field into a visual and aggregate it (e.g. dragging Order Quantity and letting Power BI SUM it) — quick, but the logic stays hidden and isn't reusable. Explicit measures are written by hand in DAX, fully visible and reusable across the model. I favored explicit measures throughout so the logic was transparent and consistent.

**Quick Measures & counting:** Used a Quick Measure for Total Sales by Category, then wrote COUNT and DISTINCTCOUNT measures for Total Orders and Distinct Products Sold (and Distinct Customers). Quick Measures are genuinely useful when you need a common pattern (running totals, percentages, YoY comparisons) without hand-writing the DAX — Power BI generates it for you. COUNT and DISTINCTCOUNT sound similar but answer different questions: COUNT includes duplicates and is right for "how many total records," while DISTINCTCOUNT ignores duplicates and is right for "how many unique entities."

**Filter context checks:** Added Year, Category, and Territory slicers and watched Total Sales Amount move accordingly — unfiltered it read **24.91M**, but selecting Year 2021 + Clothing + Germany dropped it to **10.94K**, a concrete demonstration that the measure was correctly picking up the active filter context rather than ignoring it. I also built Sales by Year, Sales by Category, and Returns by Continent as measures to further prove filter propagation was working as expected.

**Statistical measures:** Average Sales Quantity, Max/Min Sales Quantity, and a Return Rate measure (Total Return Quantity ÷ Total Sales Quantity).

**The headline finding:** Building Category-wise Sales vs Returns, Year-wise Sales Trend, and Territory-wise Return Rate visuals, then a Category-wise Return Rate pie chart, **Bikes came out with by far the highest return rate at 42.79%** — well ahead of Clothing (30.05%) and Accessories (27.16%), a clear outlier worth flagging for further investigation.

## 📁 Files
| File | Description |
|------|-------------|
| `Task-07.pbix` | The Power BI file with the Measures table built out |
| `Task-07-Submission.pdf` | Screenshots of each part plus written answers |
| `Screenshots/category-return-rate.png` | Pie chart showing Bikes as the clear outlier on return rate |
