**🎯 Business Question**

What items are most frequently purchased together (e.g., Biryani + Raita), and how can we use that to improve cross-sell and average order value (AOV)?

**Why this matters:**

Surface smart add-ons (“Customers also add…”)

Design bundles/combo meals

Improve placement & offers on menu pages

**📦 What’s in this repo**

swiggy_combos_ready.xlsx — Excel workbook with:

RawData – the CSV loaded

OrderItemMatrix – orders × items (presence = 1)

ComboMatrix – co-occurrence heatmap (how many orders contain each pair)

top_swiggy_combos.csv — ranked Top Combos with counts + basic metrics

The dataset is fictitious but realistic (e.g., Biryani ↔ Raita, Pizza ↔ Garlic Bread, Burger ↔ Fries).

🧠 **Approach (business-first, tool-second)**

**Start simple:**
Pick a hero item (e.g., Biryani) and ask, “What shows up with it most often?”
→ quick wins and an easy story for stakeholders.

**Scale to all pairs:**
Build an Orders × Items grid (1 if the order contains the item).
Multiply that grid by its transpose to get a co-occurrence matrix:
each cell = # of orders with both items → full combo map.

**Make it readable:**
Hide the diagonal (popularity of single items) and apply a heatmap to spotlight strongest pairs.

**Rank & act:**
Produce a Top Combos table and turn winners into bundles, add-ons, or targeted offers.
Measure attach rate and AOV uplift, iterate weekly.

🛠️ How to use (Excel, 5 minutes)

Option A — Open the ready file

Open swiggy_combos_ready.xlsx.

Go to ComboMatrix → this is your heatmap of item pairs.

Open top_swiggy_combos.csv to see the ranked list (easiest to present).

Option B — Rebuild from scratch (quick)

Insert a PivotTable from RawData

Rows: order_id

Columns: item

Values: item → Count (convert to 0/1 if needed)

Copy the pivot values (0/1) to a new range.

Create a co-occurrence matrix (Aᵀ×A).

Add Conditional Formatting → Color Scale; optionally hide the diagonal.

(Optional) Unpivot to a Top 20 Combos table via Power Query (Unpivot Other Columns → sort desc → Keep Top Rows).

📊 **How to read the outputs**

Heatmap (ComboMatrix)

Rows/columns = items

Cell value = #orders with both items

Brighter cells = stronger combos

Diagonal = total orders with the item (we visually de-emphasize it)

Top Combos table

orders_together → frequency of the pair

(Optional metrics) confidence, support, lift:

Confidence A→B: “Given A, how often do we also see B?”

Support: how common the pair is overall

Lift (>1): pair occurs more often than chance

🚀 **Turn insights into action**

Bundles: Fixed combo pricing for the top pairs.

Add-on nudges: “Add Raita?” on the Biryani page.

Placement: Show best add-ons above the fold.

Offers: Targeted discounts for high-potential pairs.

Measure: Attach rate, CTR on add-ons, AOV change week-over-week.

🔎 **Example insights (from this sample)**

Biryani ↔ Raita emerges as a consistent hotspot.

Pizza ↔ Garlic Bread and Burger ↔ Fries show strong cross-sell potential.

Sweet add-ons (e.g., Gulab Jamun) behave like a universal upsell in many orders.

(Your real data will vary; this sample is for demonstration.)

⚠️ **Limitations**

Synthetic sample, limited size.

Counts aren’t seasonality-aware.

No price elasticity or delivery-time effects modeled.

For production use, add time windows, restaurant segments, A/B testing, and profitability checks.

🔮 **Next steps**

Segment by city/restaurant/time of day.

Track post-launch performance of bundles.

Graduate to association-rule mining (Apriori/FPGrowth) for larger catalogs.

Feed results into on-app recommendation placements.

📜 **License & attribution**

Code/analysis in this repo: MIT (adjust as you prefer).

Data: synthetic; free to use for demos, education, and content.

**Contact**

Maintained by Madhu Uday — Data Analytics Coach.
