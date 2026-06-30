# Sales-Performance-

# Project Overview
This project delivers an end-to-end sales performance analysis for a Nigerian B2B technology and services company, tracking 12 sales representatives across 6 regions, 8 products, and 4 categories over a full 2024 calendar year. The project introduces a proper star schema data model, the first in this portfolio series to move beyond a flat table structure separating transactional sales data and monthly targets into fact tables linked to dimension tables for reps, products, customer segments, and dates.
The analysis tracks revenue against monthly targets, identifies top and bottom performing reps, breaks down performance by product category and region, and surfaces consistency patterns across the sales team.

# Tools & Technologies
Power BI Desktop — data modelling, DAX measures, dashboard design
Microsoft Excel — star schema construction, dimension and fact table builds, lookup formulas
Power Query (M) — data load and type enforcement
DAX — KPI measures, time intelligence, target attainment calculations
Star Schema Data Modelling — fact and dimension table design with verified referential integrity

# Dataset
AttributeDetailSales transactions784 dealsMonthly target records144 (12 reps x 12 months)Sales representatives12Regions6 (Lagos, Abuja, Port Harcourt, Enugu, Kano, Ibadan)Products8 across 4 categories (Software, Cloud, Hardware, Services)Observation windowJanuary 2024 - December 2024

Data Model — Star Schema
This project moves from a single flat table approach (used in the prior two portfolio projects) to a proper star schema, designed and built manually in Excel before loading into Power BI.
Fact tables:

fact_sales — 784 rows, one per closed deal, containing quantity, unit price, discount, and deal value
fact_targets — 144 rows, one per rep per month, containing target, actual revenue, variance, and attainment

Dimension tables:

dim_rep — 12 reps with region and team assignment
dim_product — 8 products with category and unit price
dim_segment — 4 customer segment types
dim_month — 12-row month lookup table, built specifically to resolve a many-to-many relationship between fact_targets and the daily-grain dim_date table
dim_date — 366-row full date dimension enabling time intelligence

Relationship chain: fact_targets → dim_month → dim_date, with dim_month as the one side and dim_date as the many side — a key modelling decision made to support both monthly target filtering and full date-level time intelligence from a single date hierarchy.
All foreign keys in fact_sales were verified against their dimension tables for referential integrity before being loaded into Power BI, with zero orphaned records.


# Key Findings
Overall Attainment

Total attainment across the 12-rep team for 2024 sits below 100%, with significant variation in consistency across reps and months rather than a uniform shortfall.
Top and Bottom Performers

Fatima Aliyu closed the year at the highest annual attainment rate among all reps, while Tunde Fashola recorded the lowest. The performance gap between top and bottom reps is substantial enough to warrant a closer look at territory assignment and target-setting methodology.
Consistency Over Capability

10 of 12 reps hit their monthly target at least once during the year, but very few hit it consistently across multiple consecutive months. This reframes the underperformance narrative: the team has demonstrated the capability to hit target, but something — pipeline timing, seasonality, or target calibration — is preventing consistent delivery month over month.
Category Performance

Services is the strongest revenue-generating category, followed by Software, with Cloud trailing as the smallest contributor — informing where sales enablement and incentive focus might be most impactful.
Seasonal Pattern

Q4 shows the strongest revenue quarter of the year, consistent with end-of-year budget cycles common in B2B technology sales, while Q2 is comparatively the weakest.

# Recommendations

Investigate target-setting methodology — given that most reps can hit target intermittently but not consistently, review whether monthly targets are evenly calibrated against realistic pipeline timing rather than a flat annual divide
Study top performer patterns — formally document what Fatima Aliyu and other consistent performers are doing differently in deal cadence, channel mix, or account management
Review underperforming rep support — reps with consistently low attainment may need pipeline coaching, territory rebalancing, or product training rather than punitive target pressure
Plan for Q2 seasonality — if Q2 is structurally the weakest quarter, consider adjusted targets or specific Q2 campaigns to smooth performance across the year
