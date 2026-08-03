# Task 5 — Relationship Behavior & Model Stress Testing

Deliberately poking at the model to see how it behaves under stress — no new tables, just testing what happens when things break

![Star Schema model view](./Screenshots/star-schema-model-view.png)

**Skills:** Relationship troubleshooting · Cardinality validation · Multi-fact-table design · Filter context & filter flow · Bidirectional filtering · Model cleanup

## What I Did

This task was all about deliberately poking at the model to see how it behaves under stress — inactive relationships, bidirectional filtering, multiple fact tables — rather than building anything new.

**Inactive relationships:** I made the `Fact_Sales` → `Dim_Calendar` relationship inactive and built a Year vs OrderQuantity visual to watch what happened. The visual stopped filtering through the Calendar dimension properly — it kept showing numbers, but they weren't being filtered correctly anymore, which is a subtle failure mode that could easily slip past someone not checking closely. I restored the relationship afterward.

**Cardinality review:** I went through every relationship in the model and confirmed they were all correctly set as Many → One from fact to dimension. This makes sense structurally — fact tables have many rows sharing the same key (like ProductKey), while dimension tables have one unique row per key, so the relationship direction has to reflect that.

**Multiple fact tables:** I confirmed `Fact_Sales` and `Fact_Returns` are never directly connected to each other — they only relate indirectly through the shared dimensions (`Dim_Product`, `Dim_Calendar`, `Dim_Territory`). Direct fact-to-fact relationships would risk ambiguity, duplicate counting, and circular filter paths, so keeping them separate and routed through dimensions is the safer design.

**Filter flow validation:** Using Year, Product Category, and Territory slicers, I confirmed filters correctly flow from Dimension → Fact (selecting a slicer updates the fact table numbers), and validated that it doesn't work the other way — selecting fact data doesn't change what's available in the dimension tables. That's the expected behavior in a proper Star Schema.

**Bidirectional filtering experiment:** I turned on bidirectional filtering for one relationship just to see what would happen. No ambiguity warning came up (the model's simple enough that it didn't cause an issue here), but I understood the risk — bidirectional filtering can create ambiguous paths in more complex models, so it's something to use carefully rather than by default.

**Cleanup:** Hid technical columns (keys, IDs) in Report View, since they clutter the Fields pane and don't add business value for anyone actually building visuals off this model.

## Why It Matters

The task came with six analytical questions, and answering them out loud is really the point of the exercise:

- **Inactive relationships silently break filtering** rather than throwing an error — the visual still renders, it just stops being accurate, which is more dangerous than an obvious failure
- **Fact → Dimension must be Many → One** because fact tables hold repeated transactional keys while dimension tables hold one unique row per key
- **Fact tables should never connect directly to each other** — different granularities and shared dimensions mean a direct link risks ambiguity, duplicate counting, and circular filter paths
- **Filter flow in a Star Schema is single-directional (Dimension → Fact)** by design, which is what keeps aggregations predictable
- **Bidirectional filtering is a tool to use deliberately, not by default** — it didn't break anything here because the model is simple, but it's a real risk in larger schemas
- **Hiding technical columns is about the next person using the model**, not just tidiness — a cluttered Fields pane makes it easier to pick the wrong field

## 📁 Files
| File | Description |
|------|-------------|
| `Task-05.pbix` | The Power BI file with the stress-tested model |
| `Task-05-Submission.pdf` | Screenshots of each part plus written answers |
| `Screenshots/star-schema-model-view.png` | Full model view showing both fact tables connected only through the shared dimensions |
