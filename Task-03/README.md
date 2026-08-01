# Task 3 — Returns Analysis & Territory Integration

This task shifted focus to the other side of the business — returns — and brought territory/geography data into the model for the first time.

## What I Did

**Returns data prep:** Loaded the returns CSV, converted ReturnDate to a proper Date type, validated ReturnQuantity as numeric, and renamed the query `Fact_Returns`.

**Territory dimension:** Cleaned up Region, Country, and Continent columns (removing extra spaces and formatting inconsistencies), and renamed the query `Dim_Territory`.

**Reusing Product & Calendar:** Rather than rebuilding from scratch, I reused the same `Dim_Product` and `Dim_Calendar` hierarchy logic from Task 2, just extended for this dataset.

**Merging everything together:** Joined `Fact_Returns` with `Dim_Product` (on ProductKey), `Dim_Territory` (on TerritoryKey), and `Dim_Calendar` (on ReturnDate). Then I added a conditional column classifying each return as **High Returns** (ReturnQuantity ≥ 2) or **Low Returns** otherwise.

**Some of what I found:**
- Return dates aren't evenly spread — there's a real pattern to when returns spike, rather than a flat distribution
- **2022 had missing dates** — only 181 days recorded instead of a full 365, suggesting the data was likely only collected through June/July of that year, which also explains why 2022 showed fewer weeks (max week numbers: 2020 had 53, 2021 had 52, 2022 had fewer due to the incomplete data)
- After merging, I built summary queries for Total Returns by Category, by Continent, and by Year to check the dataset was actually reporting-ready

## 📁 Files
| File | Description |
|------|-------------|
| `Task-03.pbix` | The Power BI file with Fact_Returns and Dim_Territory added to the model |
| `Task-03-Submission.pdf` | Screenshots of each part plus written answers |
