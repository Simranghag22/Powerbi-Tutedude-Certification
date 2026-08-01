# Task 12 — Time Intelligence Patterns in DAX

Building on the basics from Task 9, this task moved into the actual standard time intelligence patterns that show up in nearly every real BI report — YTD, YoY growth, rolling averages.

## What I Did

**Setting up properly for time intelligence:** Before writing any of the growth measures, I made sure `Dim_Calendar` had continuous, unbroken dates and marked it explicitly as a **Date Table** in Power BI — a required step for time intelligence functions to behave correctly. I also double-checked the relationships from `Dim_Calendar` to both `Fact_Sales` (via OrderDate) and `Fact_Returns` (via ReturnDate) were solid.

**Core time intelligence measures:**
- **Year-to-Date (YTD) Sales**
- **Previous Year Sales**
- **Year-on-Year (YoY) Growth %**

**Moving and comparative measures:**
- **Rolling 3-Month Sales**
- **Month-over-Month Growth**

**Validating with visuals:** Built out Sales YTD vs Previous Year, YoY Growth % by Year, and a Rolling 3-Month Sales Trend to see these patterns actually play out visually rather than just as numbers in a card.

This was a good one for really cementing why the Date Table setup matters — these functions quietly fail or give wrong numbers if the calendar table isn't marked correctly, so getting that step right first paid off for everything after it.

## 📁 Files
| File | Description |
|------|-------------|
| `Task-12.pbix` | The Power BI file with the time intelligence measures |
| `Task-12-Submission.pdf` | Screenshots of each part |
