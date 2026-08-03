# Task 16 — Top-N Performance Dashboard

All about ranking — quickly surfacing who or what is performing best (and worst) rather than showing every single data point at once

![Top 10 products with conditional formatting](./Screenshots/top10-conditional-formatting.png)

**Skills:** Top-N filtering · Conditional formatting (color scales) · Matrix visuals · Working around missing visual types

## What I Did

This task was all about ranking — quickly surfacing who or what is performing best (and worst) rather than showing every single data point at once.

**Page setup:** Created a new page named **Top-N Performance Dashboard**.

**Product performance table:** Built a Table visual with Product Name, Product Category, Total Sales, and Order Quantity, sorted by Total Sales descending, renamed `TABLE_ProductPerformance`.

**Top-N filtering:** Applied a Top 10 filter on Product Name based on Total Sales, so the table dynamically shows only the top 10 performers rather than the full product list — updating automatically as filters change elsewhere on the page.

**Conditional formatting:** Applied a color scale (low → high) to the Total Sales column, so the strongest performers are visually obvious without needing to read every number.

**Category summary matrix:** Built a Matrix with Product Category in rows, Year in columns, and Total Sales as the value — stepped layout off, subtotals on — renamed `MATRIX_CategoryYearSales`. This gave a compact year-over-year comparison across categories in one view.

**Working around another missing feature:** The task called for a dynamic Top-N Text Card ("Top Product by Sales: <Product Name>"), but the basic Card visual wasn't available in my version of Power BI Desktop either. I used a different visual that still supports Top-N filtering to surface the same information, so the #1 product is still highlighted dynamically — just not via the exact visual type the task named.

**Final check:** Confirmed slicers affected all the visuals consistently, and cleaned up alignment so the table, matrix, and card didn't overlap or feel crowded.

## 📁 Files
| File | Description |
|------|-------------|
| `Task-16.pbix` | The Power BI file with the Top-N Performance Dashboard page |
| `Task-16-Submission.pdf` | Screenshots of each part |
| `Screenshots/top10-conditional-formatting.png` | Top 10 products table with the low-to-high color scale applied |
