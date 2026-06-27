
# Part 4: Tableau Executive Dashboard & Data Storytelling

**Student:** Rohit Kadam
**Student ID:** 2511727
**Repository:** rohitkadam_2511727_part4_tableau_dashboard
**Tool Used:** Tableau Public / Tableau Desktop

---
## Business Problem Summary

The retail leadership team wants an executive dashboard to monitor sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns. The dashboard must help leadership identify business opportunities and risks and support data-driven decision-making.

---

## Dataset Description

| Property | Details |
|---|---|
| File | dashboard_sales_data.xlsx |
| Total Records | 4,200 rows |
| Date Range | January 2024 – December 2025 |
| Total Columns | 20 |
| Missing Values | customer_rating (32 nulls), campaign_channel (24 nulls) |

---

## Task 1: Data Inspection

### Date Fields

| Field | Type in Tableau | Notes |
|---|---|---|
| `order_date` | Date | Order placement date. Range: 01 Jan 2024 – 31 Dec 2025 |
| `ship_date` | Date | Shipment dispatch date. Range: 03 Jan 2024 – 06 Jan 2026 |

Both fields must be confirmed as **Date** data type in Tableau. If Tableau imports them as string, right-click the field → Change Data Type → Date.

### Geographic Fields

| Field | Type in Tableau | Notes |
|---|---|---|
| `region` | Dimension (String) | 4 values: North, South, East, West |
| `state` | Dimension (String) | Indian states — assign Geographic Role → State/Province |
| `city` | Dimension (String) | Indian cities — assign Geographic Role → City |

In Tableau, right-click `state` → Geographic Role → State/Province and `city` → Geographic Role → City to enable map views.

### Categorical Fields

| Field | Type in Tableau | Notes |
|---|---|---|
| `customer_segment` | Dimension (String) | 3 values: Consumer, Corporate, Home Office |
| `category` | Dimension (String) | 3 values: Furniture, Office Supplies, Technology |
| `sub_category` | Dimension (String) | 13 values including Tables, Chairs, Phones, Copiers etc. |
| `ship_mode` | Dimension (String) | 4 values: First Class, Second Class, Same Day, Standard Class |
| `campaign_channel` | Dimension (String) | 5 values: Email, Organic, Paid, Referral, Social — 24 nulls present |
| `product_name` | Dimension (String) | Individual product names — not used as primary dimension |
| `customer_id` | Dimension (String) | Customer identifier |
| `order_id` | Dimension (String) | Order identifier |

### Numerical Measures

| Field | Type in Tableau | Range | Notes |
|---|---|---|---|
| `sales` | Measure (Decimal) | 72.91 – 427,418.19 | Revenue per order |
| `profit` | Measure (Decimal) | -17,757.55 – 133,628.04 | Can be negative (loss-making orders) |
| `discount` | Measure (Decimal) | 0.00 – 0.35 | Expressed as decimal (0.35 = 35%) |
| `quantity` | Measure (Integer) | 1 – 10 | Units ordered |
| `delivery_days` | Measure (Integer) | 0 – 9 | Days between order and ship date |
| `customer_rating` | Measure (Decimal) | 2.10 – 5.00 | 32 null values — exclude nulls from average |

### Binary / Flag Fields

| Field | Type in Tableau | Notes |
|---|---|---|
| `return_flag` | Measure (Integer) | 0 = Not returned, 1 = Returned. Change to Dimension in Tableau for filtering. Return rate = 4.55% across all orders |

In Tableau, right-click `return_flag` → Convert to Dimension to use it as a filter and category label.

---

## Assumptions

1. `order_date` is used as the primary date field for all time-based analysis. `ship_date` is used only for delivery day calculations.
2. `delivery_days` is treated as the difference between ship date and order date — values of 0 indicate same-day dispatch.
3. `discount` values are decimal fractions (0.25 = 25% discount) — formatted as percentage in Tableau.
4. `return_flag = 1` indicates a returned order. All return rate calculations use this field divided by total order count.
5. 32 null values in `customer_rating` are excluded from average rating calculations.
6. 24 null values in `campaign_channel` are labelled as "Unknown" in dashboard filters.
7. Geographic fields (`state`, `city`) refer to Indian locations — Tableau geographic roles are assigned accordingly.
8. Negative profit values indicate orders where discounts or costs exceeded revenue — these are retained in the dataset and visible in the dashboard.

---

## Task 2: Calculated Fields

The following calculated fields were created in Tableau:

| Field Name | Formula | Purpose |
|---|---|---|
| `Profit Margin` | `SUM([Profit]) / SUM([Sales])` | Shows what percentage of sales becomes profit |
| `Cost` | `[Sales] - [Profit]` | Derives the cost of goods from sales and profit |
| `Average Order Value` | `SUM([Sales]) / COUNTD([Order Id])` | Average revenue generated per unique order |
| `Return Rate` | `SUM([Return Flag]) / COUNT([Order Id])` | Proportion of orders that were returned |
| `Shipping Delay Bucket` | IF/ELSEIF logic on Delivery Days | Groups delivery speed into: Same Day, 1-2 Days, 3-5 Days, 6+ Days |

### Explanation of Each Field

**Profit Margin:** Divides total profit by total sales to show profitability as a percentage. Used in KPI cards and category profitability views. Helps leadership quickly assess which categories, regions, or segments are most profitable relative to their revenue.

**Cost:** Subtracts profit from sales to derive the cost value. Useful for understanding the cost structure of the business without a dedicated cost column in the dataset.

**Average Order Value:** Total sales divided by the count of distinct orders. Gives a per-order revenue benchmark. Helps leadership understand whether sales growth is driven by more orders or higher value per order.

**Return Rate:** Sum of returned orders (return_flag = 1) divided by total order count. Expressed as a percentage in the dashboard. Helps identify high-return categories, regions, or segments that represent revenue risk.

**Shipping Delay Bucket:** Categorizes delivery_days into four business-friendly groups — Same Day (0 days), 1-2 Days, 3-5 Days, and 6+ Days. Makes shipping performance easy to compare across ship modes without reading raw numbers.

---

## Tableau Workbook Description

| Property | Details |
|---|---|
| File | executive_dashboard.twbx |
| Location | tableau/executive_dashboard.twbx |
| Type | Tableau Packaged Workbook (.twbx) — includes embedded data |
| Total Sheets | 10 (7 chart sheets + 3 KPI sheets) |
| Dashboard | 1 executive dashboard (Dashboard 1) |
| Tableau Version | Tableau Public / Tableau Desktop |

The workbook contains all supporting sheets and the executive dashboard in a single packaged file. Opening the .twbx file in Tableau will display all sheets and the dashboard with live filter interactions.

---

## Dashboard Components

The executive dashboard includes the following components:

### Chart Views (7)

| Sheet Name | Chart Type | Purpose |
|---|---|---|
| Sales Trend | Line Chart | Sales over time by category (Jan 2024 – Dec 2025) |
| Regional Performance | Bar Chart | Sales and profit by region |
| Category Profitability | Bar Chart | Profit by sub-category colored by category |
| Customer Segment | Bar Chart | Sales and profit by customer segment |
| Shipping Performance | Stacked Bar Chart | Delivery days by ship mode colored by delay bucket |
| Discount vs Profit | Scatter Plot | Relationship between discount level and profit |
| Return Analysis | Stacked Bar Chart | Return count by category colored by region |

### KPI Cards (3)

| KPI Card | Metric | Field Used |
|---|---|---|
| Total Sales | ₹217M | SUM(Sales) |
| Total Profit | ₹33M | SUM(Profit) |
| Average Order Value | ₹51,671 | AGG(Average Order Value) |

---

## Filters and Interactions Used

### Dashboard Filters (3)

| Filter | Field | Type |
|---|---|---|
| Region | Region | Multi-select checkbox |
| Category | Category | Multi-select checkbox |
| Customer Segment | Customer Segment | Multi-select checkbox |

### Filter Actions (1)

| Action | Source | Target | Effect |
|---|---|---|---|
| Region Filter Action | KPI Sheets | All dashboard sheets | Selecting a region in the KPI filter updates all charts and KPI values simultaneously |

All three filters are visible on the right side of the dashboard. Selecting or deselecting any value updates all charts and KPI cards dynamically.

---

## Key Business Insights

1. **Technology drives 84% of profit** on 71% of sales — Copiers, Accessories, Phones, and Machines are the top sub-categories at 18% margin.
2. **South region leads** with ₹64.7M in sales — ₹15.8M more than East or West despite similar profit margins.
3. **Furniture margin is only 6.9%** with a 7.67% return rate — double the return rate of Technology (3.03%).
4. **Discounts above 20% produce loss-making orders** — 288 negative-profit orders identified, 204 of them in the 21–30% discount band.
5. **Home Office has the highest return rate (5.67%)** despite being the highest-revenue segment (₹74.5M).
6. **Same Day shipping generates the highest profit per order (₹9,102)** — 16% higher than Standard Class.
7. **Standard Class handles 58% of orders** but has the longest delivery time (4.71 days) and lowest average profit.
8. **Bookcase and Furnishings sub-categories** have return rates above 8% — the highest in the entire product range.

---

## Dashboard Story Summary

The dashboard tells a connected story across six business dimensions:

**The core:** Technology is the profit engine — generating ₹28M of ₹33.3M total profit. The South region leads in volume. Same Day shipping attracts the highest-value orders.

**The problem:** Furniture generates 24% of sales but only 11% of profit, with the highest return rate. Deep discounting (21–30%) is creating 288 loss-making orders annually. Home Office customers return products at a 45% higher rate than Consumer customers.

**The risk:** 84% profit concentration in Technology creates fragility. Any Technology demand slowdown would have an outsized business impact.

**The opportunity:** East and West regions have the same margin profile as South but ₹15.8M less in sales each — a volume gap that better marketing could close. Eliminating 21–30% discounts and redirecting Furniture investment to Technology would improve profitability without requiring new customers.

Full narrative: `outputs/dashboard_story.md`

---

## Assumptions and Limitations

### Assumptions
1. `order_date` is the primary date field for all time-based analysis
2. `delivery_days` represents the difference between ship date and order date
3. `discount` values are decimal fractions (0.25 = 25%)
4. `return_flag = 1` indicates a returned order
5. 32 null values in `customer_rating` excluded from average calculations
6. 24 null values in `campaign_channel` treated as Unknown
7. Geographic fields refer to Indian locations
8. Negative profit orders are retained and visible in the dashboard

### Limitations
1. No cost breakdown by category — cannot determine whether Furniture's low margin is from product cost, logistics, or returns
2. Campaign channel has 24 nulls — attribution analysis is incomplete
3. Return reasons not available — cannot determine why returns occur
4. No customer lifetime value data — dashboard aggregates to order level only
5. Two-year window only — insufficient to confirm long-term seasonality or trend direction

---

## Screenshots Included

| File | Shows |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard with all charts, KPIs, and filters |
| `screenshots/sales_trend_view.png` | Sales trend line chart by category over time |
| `screenshots/regional_performance_view.png` | Regional sales and profit bar chart |
| `screenshots/category_profitability_view.png` | Sub-category profit bar chart colored by category |
| `screenshots/filter_interaction_view.png` | Dashboard with active filter interaction applied |

---

## Repository Structure

```
part4_tableau_dashboard/
├── data/
│   └── dashboard_sales_data.xlsx
├── tableau/
│   └── executive_dashboard.twbx
├── outputs/
│   ├── dashboard_story.md
│   ├── business_insights.md
│   └── chart_selection_justification.md
├── screenshots/
│   ├── full_dashboard.png
│   ├── sales_trend_view.png
│   ├── regional_performance_view.png
│   ├── category_profitability_view.png
│   └── filter_interaction_view.png
└── README.md
```
