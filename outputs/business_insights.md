# Business Insights — Part 4: Tableau Executive Dashboard

**Student:** Rohit Kadam
**Student ID:** 2511727
**Based on:** Executive Sales Performance Dashboard — dashboard_sales_data.xlsx (4,200 orders, Jan 2024 – Dec 2025)

---

## Insight 1 — Sales Trend: Sales Growth Is Steady but Uneven Across Months

**Observation from dashboard:**
The Sales Trend line chart shows total monthly sales fluctuating between ₹6.3M and ₹15M across 2024–2025, with Technology consistently dominating while Furniture and Office Supplies remain flat.

**Data evidence:**
- 2024 total sales: ₹106.2M | 2025 total sales: ₹110.8M — year-on-year growth of +4.3%
- Lowest month: August 2024 at ₹6.3M
- Highest month: July 2025 at ₹10.7M
- Technology drives the majority of the monthly variance — its line has the steepest swings

**Business interpretation:**
Overall business is growing but slowly (+4.3% YoY). The high monthly variance suggests sales are event-driven or promotion-dependent rather than driven by consistent demand. August 2024's sharp dip is a concern — it indicates a potential seasonal low that the business has not addressed with promotions or campaigns.

**Recommended action:**
Investigate what caused the August 2024 dip and whether it repeated in August 2025. If seasonal, develop a targeted August promotion — particularly for Technology — to smooth the revenue curve and reduce dependence on high-variance months.

---

## Insight 2 — Regional Performance: South Region Leads but All Regions Have Similar Margins

**Observation from dashboard:**
The Regional Performance bar chart shows South as the clear leader in both sales and profit, followed by North, while East and West are nearly equal.

**Data evidence:**
- South: ₹64.7M sales, ₹10.0M profit (15.4% margin)
- North: ₹54.6M sales, ₹8.3M profit (15.2% margin)
- East: ₹48.9M sales, ₹7.6M profit (15.6% margin)
- West: ₹48.9M sales, ₹7.4M profit (15.1% margin)
- South generates 30% of total sales but only 29.5% of total profit

**Business interpretation:**
South is the strongest revenue region but not meaningfully more profitable than other regions. All four regions operate at margins between 15.1% and 15.6% — a very tight range. This tells leadership that the business model is consistent across regions and that regional sales differences are driven by volume, not better pricing or lower costs in any one region.

**Recommended action:**
Investigate why South generates more volume — is it more stores, a larger customer base, or stronger campaign performance? Apply those learnings to East and West, which lag by ₹15M+ in sales despite similar margin profiles. The opportunity is in volume growth, not margin improvement.

---

## Insight 3 — Category Profitability: Technology Drives 84% of Profit on 71% of Sales

**Observation from dashboard:**
The Category Profitability chart shows Technology sub-categories (Copiers, Accessories, Phones, Machines) dominating the top of the profit chart, while Furniture sub-categories (Chairs, Furnishings, Tables, Bookcases) have dramatically lower profit despite comparable sales volumes.

**Data evidence:**
- Technology: ₹153.9M sales → ₹28.0M profit (18.2% margin)
- Furniture: ₹51.6M sales → ₹3.6M profit (6.9% margin)
- Office Supplies: ₹11.5M sales → ₹1.7M profit (14.8% margin)
- Copiers alone: ₹40.6M sales → ₹7.3M profit (18.0% margin)
- Tables profit margin: only 5.7% — lowest of all sub-categories

**Business interpretation:**
Technology is the profit engine of the business. Furniture generates 24% of sales but only 11% of profit. The Furniture category — particularly Tables and Bookcases — is generating revenue without generating meaningful returns. This represents an opportunity cost: resources (marketing, inventory, logistics) invested in Furniture would generate higher returns if shifted to Technology.

**Recommended action:**
Review the Furniture pricing and cost structure immediately. Consider reducing Furniture inventory investment and reallocating marketing budget toward Technology — specifically Copiers and Accessories, which combine high profit with high volume. If Furniture must be retained, target margin improvement through reduced discounting.

---

## Insight 4 — Customer Segment Behavior: Home Office Leads in Sales but Has Highest Return Rate

**Observation from dashboard:**
The Customer Segment chart shows Home Office with the highest sales, followed closely by Consumer and Corporate. All three segments show similar profit margins, but return data reveals Home Office as the riskiest segment.

**Data evidence:**
- Home Office: ₹74.5M sales, ₹11.6M profit (15.5% margin), return rate 5.67%
- Consumer: ₹71.9M sales, ₹11.0M profit (15.3% margin), return rate 3.91%
- Corporate: ₹70.6M sales, ₹10.7M profit (15.2% margin), return rate 4.00%
- Home Office return rate is 45% higher than Consumer return rate

**Business interpretation:**
All three segments contribute nearly equally to revenue and profit — this is a well-balanced customer portfolio. However, Home Office's return rate of 5.67% is significantly elevated. If this trend continues at scale, it will erode margin through return processing costs, restocking, and potential product write-offs. Home Office buyers may be making less informed purchase decisions or may have different product fit expectations.

**Recommended action:**
Add post-purchase follow-up touchpoints specifically for Home Office customers — product guides, setup support, or satisfaction checks within the first 7 days of delivery. Investigate which product categories Home Office customers are returning most frequently and address the root cause (sizing, expectations, quality).

---

## Insight 5 — Discount Impact: Discounts Above 20% Destroy Profit

**Observation from dashboard:**
The Discount vs Profit view shows a clear negative relationship between discount level and profit per order. As discount percentage increases, average profit drops sharply and turns negative.

**Data evidence:**
- No Discount: avg profit ₹13,203 per order
- 1–10% discount: avg profit ₹10,010 per order (-24%)
- 11–20% discount: avg profit ₹6,336 per order (-52%)
- 21–30% discount: avg profit ₹3,181 per order (-76%)
- 31%+ discount: avg profit **-₹1,601 per order** (loss-making)
- 288 total orders with negative profit
- 204 of those 288 loss-making orders had discounts of 21–30%

**Business interpretation:**
Discounting above 20% consistently produces loss-making orders. The business is currently writing off margin on 288 orders — nearly 7% of all orders — through excessive discounting. Most of these are in the 21–30% bucket, suggesting a systematic over-discounting policy rather than isolated exceptions.

**Recommended action:**
Implement a discount cap of 20% across all categories without CFO-level approval. Review the 204 orders with 21–30% discounts — identify which sales team, region, or campaign channel approved them. Replace deep discounting with value-add incentives (free shipping, extended warranty, bundling) that do not directly erode margin.

---

## Insight 6 — Shipping Performance: Standard Class Dominates but Same Day Generates Highest Profit

**Observation from dashboard:**
The Shipping Performance chart shows Standard Class as the most-used shipping mode by far, but Same Day shipping generates the highest average profit per order despite being used least.

**Data evidence:**
- Standard Class: 2,435 orders (58% of total), avg delivery 4.71 days, avg profit ₹7,839
- Second Class: 894 orders (21%), avg delivery 2.68 days, avg profit ₹8,261
- First Class: 630 orders (15%), avg delivery 1.77 days, avg profit ₹7,364
- Same Day: 241 orders (6%), avg delivery 0.40 days, avg profit ₹9,102
- Same Day profit is 16% higher than Standard Class profit

**Business interpretation:**
Same Day shipping customers generate the highest profit per order. This likely reflects higher-value orders (premium customers or urgent corporate purchases) that are less price-sensitive and less likely to be discounted. Standard Class is the workhorse but has the lowest average profit. The long average delivery time of Standard Class (4.71 days) may be affecting customer satisfaction and contributing to returns.

**Recommended action:**
Promote Same Day and First Class shipping options to Corporate and Home Office segments where order values are higher. Investigate whether Standard Class delivery times can be improved — reducing from 4.71 days to 3 days could improve satisfaction and reduce return rates without changing the shipping mode.

---

## Insight 7 — Return Pattern: Furniture Has Double the Return Rate of Technology

**Observation from dashboard:**
The Return Analysis chart shows Furniture with significantly more returns than Technology and Office Supplies. Within Furniture, Bookcases, Furnishings, and Chairs have the highest individual return rates.

**Data evidence:**
- Furniture return rate: 7.67%
- Office Supplies return rate: 3.65%
- Technology return rate: 3.03%
- Bookcases: 8.42% return rate (highest sub-category)
- Furnishings: 8.16% return rate
- Chairs: 7.99% return rate
- Copiers: 2.72% return rate (lowest sub-category)
- East region has the highest return rate at 4.91%

**Business interpretation:**
Furniture's return rate is more than double that of Technology. This compounds the already-low Furniture profit margin (6.9%) — returns add reverse logistics costs, reduce net revenue, and tie up inventory. The East region's elevated return rate across all categories suggests either a quality or expectation mismatch specific to that geography.

**Recommended action:**
Add detailed product photography, dimensions, and assembly guides for Furniture — particularly Bookcases, Furnishings, and Chairs — to set accurate expectations pre-purchase. Implement a returns-reduction pilot in the East region with proactive post-purchase customer outreach. Track whether return rate falls after these interventions.

---

## Insight 8 — Business Risk and Opportunity: Technology Is Both the Greatest Asset and Greatest Concentration Risk

**Observation from dashboard:**
Technology generates 71% of total revenue and 84% of total profit. No other category comes close. This creates an extreme business concentration risk.

**Data evidence:**
- Technology: ₹153.9M sales (71% of total), ₹28.0M profit (84% of total profit)
- If Technology sales dropped 20%, total business profit would fall from ₹33.3M to approximately ₹27.7M — a 17% total profit decline
- Furniture and Office Supplies combined contribute only 16% of total profit
- Copiers, Accessories, Phones, and Machines together = ₹154M sales = more than Furniture + Office Supplies combined

**Business interpretation:**
The business is heavily dependent on Technology performance. Any disruption — supply chain issues, competitor pricing, market saturation, or category demand slowdown — would have an outsized impact on profitability. Meanwhile, Furniture and Office Supplies are underperforming and not generating enough profit to act as a meaningful safety buffer.

**Recommended action:**
Pursue a dual strategy: (1) Protect and grow Technology through exclusive supplier partnerships, inventory priority, and targeted marketing to Corporate and Home Office segments. (2) Improve the profitability of Furniture and Office Supplies through cost restructuring and reduced discounting so that if Technology slows, these categories can partially absorb the impact. Set a strategic target to reduce Technology's profit concentration from 84% to 70% within 18 months.

---

*All insights derived from: outputs/executive_dashboard.twbx and dashboard_sales_data.xlsx (4,200 orders, Jan 2024 – Dec 2025)*
