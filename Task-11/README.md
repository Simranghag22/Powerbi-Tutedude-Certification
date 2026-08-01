# Task 11 — ALL, FILTER & Iterator Functions in DAX

This task covered some of the trickier but genuinely powerful DAX patterns — removing filter context on purpose, filtering at the row level, and iterating row-by-row for calculations that a simple aggregation can't do.

## What I Did

**ALL() to remove filter context:** Built an Overall Sales Quantity measure that deliberately ignores whatever filters are active, which is exactly what you need as the denominator for a percentage-of-total calculation. Used that to build **Category Contribution %** — each category's share of the whole, regardless of what's currently sliced.

- **Why ALL is mandatory here**: without it, the "total" in your percentage calculation would itself be filtered down to match whatever category is currently selected, making every category show up as ~100% of itself. `ALL()` breaks that filter so the denominator stays constant across every row.

**FILTER for row-level conditions:** Built High Volume Sales (quantity > 5) and High Price Returns measures using `FILTER` to evaluate each row individually against a condition, rather than just aggregating everything.

**Iterator functions:** Used `SUMX` for Total Sales Value (multiplying quantity × price row-by-row before summing) and `AVERAGEX` for Average Sales per Transaction — the kind of calculation that a plain `SUM` genuinely can't do correctly, since it needs the multiplication done per-row first.

**What I found:**
- Interestingly, **no transactions actually met the "High Volume" threshold** (quantity > 5) — every single one of the 84,174 recorded units fell under Normal Sales, meaning the business is driven by many small orders rather than a few bulk ones.
- **Accessories contributes the most to overall sales**, at roughly **68.68%** of total sales quantity — a dominant share compared to every other category combined.

## 📁 Files
| File | Description |
|------|-------------|
| `Task-11.pbix` | The Power BI file with ALL/FILTER/iterator measures |
| `Task-11-Submission.pdf` | Screenshots of each part plus written answers |
