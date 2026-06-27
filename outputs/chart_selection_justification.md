# Chart Selection Justification — Part 4: Tableau Executive Dashboard

**Student:** Rohit Kadam
**Student ID:** 2511727

---

## 1. Sales Trend View — Line Chart

**Question answered:** How are sales changing over time across categories?

**Why this chart type is appropriate:**
A line chart is the correct choice for time-series data. It shows direction, magnitude, and rate of change across months clearly. The continuous line makes it easy to spot peaks, troughs, and seasonal patterns that a bar chart would make harder to read across 24 months.

**Fields used:**
- Columns: MONTH(Order Date)
- Rows: SUM(Sales)
- Color: Category (Furniture, Office Supplies, Technology)

**Design principle applied:**
Color is used only to distinguish categories — not for decoration. Three distinct colors allow leadership to track each category independently on the same axis without confusion.

**Mistake avoided:**
Avoided using a bar chart for time series, which would have made trend direction harder to read. Avoided stacking categories into a single line which would have hidden individual category performance.

---

## 2. Regional Performance View — Bar Chart

**Question answered:** Which region generates the most sales and profit?

**Why this chart type is appropriate:**
A horizontal bar chart is ideal for comparing a single measure across a small number of categories (4 regions). Bars make it immediately clear which region leads. Color encodes profit, adding a second dimension without adding a second chart.

**Fields used:**
- Rows: Region
- Columns: SUM(Sales)
- Color: SUM(Profit)

**Design principle applied:**
Sorted by Sales descending so the highest-performing region appears at the top. Color gradient on Profit allows leadership to see both sales volume and profitability in one view. Clear hierarchy — sales is the primary measure, profit is secondary context.

**Mistake avoided:**
Avoided using a pie chart, which would have made regional comparison difficult and would not have allowed a second measure (profit) to be shown clearly.

---

## 3. Category Profitability View — Bar Chart

**Question answered:** Which sub-categories drive the most profit or loss?

**Why this chart type is appropriate:**
A horizontal bar chart with 13 sub-categories is appropriate because it allows easy comparison of all sub-categories at once. Color distinguishes the three parent categories, helping leadership understand which category each sub-category belongs to without a separate lookup.

**Fields used:**
- Rows: Sub Category
- Columns: SUM(Profit)
- Color: Category

**Design principle applied:**
Sorted by Profit descending so the highest-profit sub-categories appear at the top. Negative profit bars (if present) would extend left of zero, making losses immediately visible. Labels are clear and sub-category names are fully readable.

**Mistake avoided:**
Avoided using a treemap, which would have made it difficult to compare profit values precisely. Avoided combining sub-category and category on the same axis, which would have created a cluttered view.

---

## 4. Customer Segment View — Bar Chart

**Question answered:** Which customer segment generates the most sales and profit?

**Why this chart type is appropriate:**
A horizontal bar chart with three segments allows direct comparison. Color encodes profit to add context beyond just sales volume. With only three segments, the chart is clean and immediately readable without any cognitive load.

**Fields used:**
- Rows: Customer Segment
- Columns: SUM(Sales)
- Color: SUM(Profit)

**Design principle applied:**
Consistent use of the same color scheme as the Regional Performance chart (blue gradient for profit) maintains visual consistency across the dashboard. Minimal clutter — no gridlines, no unnecessary labels.

**Mistake avoided:**
Avoided using a donut or pie chart for segment comparison, which would have made it difficult to compare segment sizes accurately.

---

## 5. Shipping Performance View — Bar Chart

**Question answered:** Which shipping mode has the most delivery days and what is the delay distribution?

**Why this chart type is appropriate:**
A stacked horizontal bar chart works well here because it shows both the total delivery days per ship mode and the breakdown by Shipping Delay Bucket. Leadership can see at a glance which ship mode accumulates the most delay and what type of delay (Same Day, 1-2 Days, 3-5 Days, 6+ Days) drives it.

**Fields used:**
- Rows: Ship Mode
- Columns: SUM(Delivery Days)
- Color: Shipping Delay Bucket (calculated field)

**Design principle applied:**
The Shipping Delay Bucket calculated field converts raw numbers into business-friendly categories, making the chart interpretable without statistical knowledge. Consistent color across delay buckets makes the legend easy to read.

**Mistake avoided:**
Avoided showing raw delivery day numbers without context. Avoided using a line chart, which would have implied a time trend that does not exist in this dimension.

---

## 6. Return Analysis View — Stacked Bar Chart

**Question answered:** Which category has the most returns and which region drives returns?

**Why this chart type is appropriate:**
A stacked bar chart shows both the total return volume per category and the regional breakdown within each category. This allows leadership to identify not just which category is highest risk but also which region within that category is driving returns.

**Fields used:**
- Rows: Category
- Columns: SUM(Return Flag)
- Color: Region

**Design principle applied:**
Color used for Region matches the consistent color palette used across the dashboard. Three categories keep the chart clean. The stacked design adds regional insight without requiring a separate chart.

**Mistake avoided:**
Avoided using a heat map or highlight table, which would have been harder to read with only three categories. Avoided showing return rate as a percentage only, which could have been misleading if category sizes differed significantly.

---

## 7. KPI Cards — Text Sheets (3 cards)

**Question answered:** What are the overall headline business metrics?

**Why this chart type is appropriate:**
KPI cards (large-format text with a single number) are the correct format for executive headline metrics. They allow leadership to absorb the most important numbers — Total Sales, Total Profit, Average Order Value — at a glance without reading a chart.

**Fields used:**
- KPI Total Sales: SUM(Sales)
- KPI Total Profit: SUM(Profit)
- KPI Average Order Value: AGG(Average Order Value)

**Design principle applied:**
Placed at the top of the dashboard following the visual hierarchy principle — most important information first. Formatted in millions for readability (₹217M, ₹33M). Large font for the number, smaller font for the label. Connected to region filter via action so KPIs update when a region is selected.

**Mistake avoided:**
Avoided showing raw unformatted numbers (e.g., 217,917,653) which would be difficult to read at a glance. Avoided using a gauge or speedometer chart, which is decorative and not appropriate for executive dashboards.

---

## Dashboard-Level Design Principles Applied

| Principle | How Applied |
|---|---|
| Correct chart selection | Each chart type matches the business question it answers |
| Clear hierarchy | KPI cards at top, trend in upper left, regional and segment charts in center, operational charts at bottom |
| Minimal clutter | No unnecessary gridlines, borders, or decorative elements |
| Consistent color usage | Category always uses the same 3 colors; Profit always uses the same blue gradient |
| Proper labels | All axes labeled, all chart titles match the view name |
| Readable titles | Plain business language — "Sales Trend", "Category Profitability", not statistical jargon |
| Appropriate sorting | Bar charts sorted descending by primary measure |
| Useful filters | Region, Category, Customer Segment filters — the three most actionable dimensions for leadership |
| Avoidance of misleading scales | All axes start at zero; no dual axes with different scales |
| Focus on business interpretation | Every chart answers a business question leadership would actually ask |
