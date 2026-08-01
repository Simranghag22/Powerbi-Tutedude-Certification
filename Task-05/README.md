# Task 5 — Relationship Behavior & Model Stress Testing

This task was all about deliberately poking at the model to see how it behaves under stress — inactive relationships, bidirectional filtering, multiple fact tables — rather than building anything new.

## What I Did

**Inactive relationships:** I made the `Fact_Sales` → `Dim_Calendar` relationship inactive and built a Year vs OrderQuantity visual to watch what happened. The visual stopped filtering through the Calendar dimension properly — it kept showing numbers, but they weren't being filtered correctly anymore, which is a subtle failure mode that could easily slip past someone not checking closely. I restored the relationship afterward.

**Cardinality review:** I went through every relationship in the model and confirmed they were all correctly set as Many → One from fact to dimension. This makes sense structurally — fact tables have many rows sharing the same key (like ProductKey), while dimension tables have one unique row per key, so the relationship direction has to reflect that.

**Multiple fact tables:** I confirmed `Fact_Sales` and `Fact_Returns` are never directly connected to each other — they only relate indirectly through the shared dimensions (`Dim_Product`, `Dim_Calendar`, `Dim_Territory`). Direct fact-to-fact relationships would risk ambiguity, duplicate counting, and circular filter paths, so keeping them separate and routed through dimensions is the safer design.

**Filter flow validation:** Using Year, Product Category, and Territory slicers, I confirmed filters correctly flow from Dimension → Fact (selecting a slicer updates the fact table numbers), and validated that it doesn't work the other way — selecting fact data doesn't change what's available in the dimension tables. That's the expected behavior in a proper Star Schema.

**Bidirectional filtering experiment:** I turned on bidirectional filtering for one relationship just to see what would happen. No ambiguity warning came up (the model's simple enough that it didn't cause an issue here), but I understood the risk — bidirectional filtering can create ambiguous paths in more complex models, so it's something to use carefully rather than by default.

**Cleanup:** Hid technical columns (keys, IDs) in Report View, since they clutter the Fields pane and don't add business value for anyone actually building visuals off this model.

## 📁 Files
| File | Description |
|------|-------------|
| `Task-05.pbix` | The Power BI file with the stress-tested model |
| `Task-05-Submission.pdf` | Screenshots of each part plus written answers |
