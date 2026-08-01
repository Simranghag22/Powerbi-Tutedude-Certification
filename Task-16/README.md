# Task 16 — Top-N Performance Dashboard

This task was all about ranking — quickly surfacing who or what is performing best (and worst) rather than showing every single data point at once.

## What I Did

**Page setup:** Created a new page named **Top-N Performance Dashboard**.

**Product performance table:** Built a Table visual with Product Name, Product Category, Total Sales, and Order Quantity, sorted by Total Sales descending, renamed `TABLE_ProductPerformance`.

**Top-N filtering:** Applied a Top 10 filter on Product Name based on Total Sales, so the table dynamically shows only the top 10 performers rather than the full product list — updating automatically as filters change elsewhere on the page.

**Conditional formatting:** Applied a color scale (low → high) to the Total Sales column, so the strongest performers are visually obvious without needing to read every number.

**Category summary matrix:** Built a Matrix with Product Category in rows, Year in columns, and Total Sales as the value — stepped layout off, subtotals on — renamed `MATRIX_CategoryYearSales`. This gave a compact year-over-year comparison across categories in one view.

**Dynamic Top-N text card:** Created a Text Card that reads "Top Product by Sales: <Product Name>", using Top-N logic via a visual filter so it always highlights whichever product is currently #1 — not a hardcoded value.

**Final check:** Confirmed slicers affected all the visuals consistently, and cleaned up alignment so the table, matrix, and card didn't overlap or feel crowded.

## 📁 Files
| File | Description |
|------|-------------|
| `Task-16.pbix` | The Power BI file with the Top-N Performance Dashboard page |
| `Task-16-Submission.pdf` | Screenshots of each part |
