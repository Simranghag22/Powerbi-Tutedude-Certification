# Task 2 — Sales Data Integration & Modeling

This is where things got real — pulling together multiple years of raw sales CSVs into something usable, playing the role of a BI analyst at a retail company.

## What I Did

**Consolidating sales data:** I loaded three years of sales CSVs (2020, 2021, 2022) into Power Query and appended them into a single table, which I renamed `Fact_Sales`. I checked the data types carefully — OrderDate and StockDate as Date, OrderQuantity as Whole Number — then added Year and Month Name columns extracted from OrderDate, plus an Index column starting from 1.

- **Highest order quantity** came in 2022, at 45,314 units
- **Top 3 months** by order quantity were June, May, and December

**Building the product hierarchy:** I merged Product Lookup with Product Subcategories, then merged that result with Product Categories, validated that ProductKey was unique, and added a Profit Margin column (Price − Cost). Renamed the final query `Dim_Product`. The category with the most products turned out to be **Components**.

**Calendar prep:** Converted the date column properly and added Year, Month Number, Month Name, and Week Number columns, renamed to `Dim_Calendar`.

**Integration check:** Merged `Fact_Sales` with both `Dim_Product` and `Dim_Calendar`, and validated there were no duplicates and data types stayed correct after merging. As a final sanity check, I confirmed the Year-wise order quantity from this merged view matched what I'd calculated back in Part 1 — which it did, confirming the integration held together correctly.

## 📁 Files
| File | Description |
|------|-------------|
| `Task-02.pbix` | The Power BI file with Fact_Sales, Dim_Product, and Dim_Calendar built out |
| `Task-02-Submission.pdf` | Screenshots of each part plus written answers |
