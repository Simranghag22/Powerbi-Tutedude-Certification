# Task 9 — Time Intelligence with DAX

This task got me comfortable with Power BI's date/time functions — the building blocks for anything that compares performance across periods.

## What I Did

**Basic date measures:** Today's Date, Current Year, and Current Month Name — simple, but useful groundwork for anything that needs to reference "now" dynamically.

**Breaking sales down by date components:** Using `YEAR()`, `MONTH()`, and `FORMAT()`, I built Sales Quantity by Year, Sales Quantity by Month, and Returns Quantity by Year.

**Period comparisons:** Sales This Year and Sales Last Year measures, so I could start comparing performance across time rather than just looking at flat totals.

**Month-level analysis:** Added a Month-to-Date Sales measure and used the Calendar Hierarchy to identify which month had the highest sales.

**Bringing it together in visuals:** Year-wise Sales Trend, Month-wise Sales vs Returns, and Current Year vs Last Year Sales.

**What I found:**
- **2021 was the best-performing year**, with total sales amount around 9.32M — actually higher than 2022 (9.19M), even though 2022 had more total order *quantity*. That distinction between quantity and revenue value was an interesting nuance to notice.
- **Returns are trending down over time** — the Month-wise chart showed return quantity declining from around 190 in the higher-return months to about 50 in the lowest, with only minor fluctuations along the way.

## 📁 Files
| File | Description |
|------|-------------|
| `Task-09.pbix` | The Power BI file with the time intelligence measures |
| `Task-09-Submission.pdf` | Screenshots of each part plus written answers |
