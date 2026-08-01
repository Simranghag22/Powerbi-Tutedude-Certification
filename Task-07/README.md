# Task 7 — DAX Measures & Analytical Insights

This is where DAX properly started — moving business logic out of Power Query and into measures that recalculate dynamically as someone filters a report.

## What I Did

**Getting oriented:** Before writing anything, I made sure I understood the split between Calculated Columns (computed row-by-row, stored in the table) and Measures (computed on the fly, based on whatever's currently filtered). I created a dedicated `Measures` table to keep everything organized in one place rather than scattered across the model.

- **Why DAX runs differently from Power Query**: Power Query transforms and stores data at refresh time, so its results are fixed until the next refresh. DAX measures instead recalculate live, responding to whatever filters, slicers, or visuals are currently in context — which is exactly why they're the right tool for anything that needs to react to user interaction.

**Calculated columns:** Added `Sales Amount = OrderQuantity * ProductPrice` in Fact_Sales, and a `Return Flag` in Fact_Returns using `IF(ReturnQuantity > 0, "Returned", "Not Returned")`.

**Core aggregation measures:** Built Total Sales Quantity, Total Sales Amount, Total Return Quantity, and Total Products Sold as explicit measures.

**Quick Measures & counting:** Used a Quick Measure for Total Sales by Category, then wrote COUNT and DISTINCTCOUNT measures for Total Orders and Distinct Products Sold. Quick Measures are genuinely useful when you need a common pattern (running totals, percentages, YoY comparisons) without hand-writing the DAX — Power BI generates it for you.

**Filter context checks:** Added Year, Category, and Territory slicers and watched how Sales by Year, Sales by Category, and Returns by Continent measures responded — confirming the measures were correctly picking up the active filter context rather than ignoring it.

**Statistical measures:** Average Sales Quantity, Max/Min Sales Quantity, and a Return Rate measure (Total Return Quantity ÷ Total Sales Quantity).

**The headline finding:** Building Category-wise Sales vs Returns, Year-wise Sales Trend, and Territory-wise Return Rate visuals, **Bikes came out with by far the highest return rate at 42.79%** — a clear outlier compared to Clothing and Accessories.

## 📁 Files
| File | Description |
|------|-------------|
| `Task-07.pbix` | The Power BI file with the Measures table built out |
| `Task-07-Submission.pdf` | Screenshots of each part plus written answers |
