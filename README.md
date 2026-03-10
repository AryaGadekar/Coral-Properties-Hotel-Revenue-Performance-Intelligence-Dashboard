## TL;DR

Built a **Power BI hotel revenue intelligence dashboard** using **134,591 daily room records** to analyse portfolio performance, booking platform efficiency, and demand patterns across a multi-city hotel group.

The goal was to move beyond simple reporting and to diagnose where revenue, capacity, and channel strategy should be prioritised.

**Key findings**

- **Business travel dominates revenue**, contributing roughly 77% of total portfolio revenue.  
- **Weekend demand outperforms weekdays**, both in occupancy and ADR.  
- **Coral Delhi leads the portfolio** on RevPAR and occupancy efficiency.  
- **Booking platforms differ widely** in ADR and realisation percentage, which creates a channel yield problem worth fixing.  
- **There is untapped capacity** across the portfolio, meaning revenue growth can be driven by demand capture rather than new rooms.
  

# Coral-Properties-Hotel-Revenue-Performance-Intelligence-Dashboard
Power BI hospitality analytics dashboard analyzing revenue performance, occupancy trends, RevPAR, ADR, and booking platform efficiency.

## Dashboard Preview

<p align="center">
  <img src="images/Coral Dashboard.png" width="900"/>
</p>

*Figure 1. Coral Properties Hotel Revenue & Performance Intelligence Dashboard built in Power BI. The dashboard consolidates portfolio revenue performance, booking platform efficiency, property benchmarking, and demand trends to support revenue management decisions.*

## Dashboard Overview

The **Hotel Revenue & Performance Intelligence Dashboard** provides a consolidated view of operational and financial performance across the Coral Properties hotel portfolio. Built in **Power BI**, the dashboard brings together booking transactions, property data, and operational metrics to help analyze revenue generation, demand patterns, and distribution channel performance.

The dashboard highlights key hospitality performance indicators such as **Total Revenue, RevPAR (Revenue per Available Room), ADR (Average Daily Rate), Occupancy %, and Realisation %**, allowing stakeholders to monitor both revenue efficiency and capacity utilization across properties.

To support operational analysis, the dashboard includes multiple analytical views:

- **Revenue Performance KPIs** summarizing portfolio-level performance, including total revenue, RevPAR, occupancy rate, and realized revenue.
- **Revenue Distribution by Category** showing the contribution of business and luxury segments to total revenue.
- **Trend Analysis of Key Metrics** tracking weekly changes in RevPAR, ADR, and occupancy to identify demand fluctuations and operational trends.
- **Booking Platform Performance** analyzing realization rates and ADR across different booking channels to evaluate distribution efficiency.
- **Property-Level Performance Table** enabling benchmarking of individual hotels based on revenue, occupancy, pricing strategy, cancellation rate, and customer ratings.

Interactive filters allow users to analyze performance by **city, room class, and time period**, enabling flexible exploration of demand patterns and operational performance across the portfolio.

Overall, the dashboard transforms raw booking data into a **decision-support tool for revenue management, channel optimization, and property performance benchmarking**, helping hospitality managers identify growth opportunities and operational inefficiencies across the hotel network.

## Table of Contents

1. [Introduction](#introduction)
2. [Project Background](#project-background)
3. [Key Metrics](#key-metrics)
4. [Data Overview & Validation](#data-overview--validation)
5. [Executive Summary](#executive-summary)
6. [Insights Deep Dive](#insights-deep-dive)
7. [Strategic Recommendations & Performance Metrics](#strategic-recommendations--performance-metrics)
8. [Tools & Methods](#tools--methods)
9. [Assumptions & Limitations](#assumptions--limitations)
10. [Next Steps](#next-steps)

## Project Background

Hotel chains operate in a highly competitive environment where **pricing strategy, room utilization, and distribution channels** directly impact revenue performance. Managing multiple properties across different cities introduces additional complexity, as each location may experience different demand patterns, customer segments, and booking channel behaviors.

For hospitality businesses such as **Coral Properties**, leadership must constantly monitor how effectively their properties convert **available room inventory into revenue**. However, traditional operational reports often focus on isolated metrics and lack the integrated view required to evaluate portfolio-level performance.

This analysis addresses several key business questions:

- Which properties generate the strongest revenue and operational performance?
- How efficiently are hotels utilizing available room inventory?
- Which booking platforms contribute the most to realized revenue?
- Are pricing strategies aligned with occupancy levels and demand trends?

Understanding these drivers is essential for **revenue management teams** responsible for optimizing pricing, improving occupancy rates, and maximizing revenue per available room.

To support these decisions, this project analyzes **134,592 booking-level records** across multiple properties and booking platforms. By integrating operational metrics such as **RevPAR, ADR, Occupancy %, and Realisation %**, the analysis provides a structured view of hotel performance across different operational dimensions.

The insights generated from this analysis support several strategic decisions:

- **Hotel portfolio performance evaluation** to identify high-performing and underperforming properties.
- **Revenue management optimization** by understanding how pricing and occupancy interact.
- **Booking channel analysis** to evaluate which distribution platforms drive realized revenue.
- **Occupancy and pricing strategy insights** to improve capacity utilization and revenue efficiency.

By consolidating these insights into an interactive **Power BI dashboard**, the project provides a centralized analytics framework that enables stakeholders to monitor performance trends, benchmark properties, and make data-driven revenue management decisions.

## Key Metrics

The dashboard evaluates hotel performance using a set of standard **hospitality revenue management KPIs**. These metrics help measure how efficiently properties convert available room inventory into revenue and how pricing strategies interact with occupancy levels.

Together, these indicators provide visibility into **demand patterns, pricing efficiency, and capacity utilization** across the hotel portfolio.

| Metric | Meaning |
|------|------|
| **RevPAR (Revenue per Available Room)** | Measures how effectively a hotel generates revenue from its available room inventory. Calculated as total revenue divided by total available room nights. |
| **ADR (Average Daily Rate)** | Represents the average revenue earned per occupied room. It reflects the effectiveness of the hotel's pricing strategy. |
| **Occupancy %** | The percentage of available rooms that are successfully booked. Calculated as booked rooms divided by total available rooms. |
| **Realisation %** | Indicates the proportion of generated revenue that is actually realized after booking confirmations and adjustments. |
| **DSRN (Daily Sellable Room Nights)** | Total number of rooms available for sale across the portfolio on a given day. |
| **DBRN (Daily Booked Room Nights)** | Total number of rooms successfully booked across all properties. |
| **DURN (Daily Utilized Room Nights)** | Total number of rooms that were actually occupied by guests during the stay period. |

These KPIs collectively help evaluate **portfolio performance, booking efficiency, and revenue generation potential**, allowing stakeholders to monitor operational trends and identify opportunities for improving occupancy and pricing strategy.

## Data Overview & Validation

The analysis is based on a **hospitality booking dataset containing 134,592 booking-level transactions** across multiple hotel properties. The dataset captures reservation details, property information, booking channels, and revenue metrics used to evaluate portfolio performance.

The data model follows a **star schema structure**, where booking and operational metrics are stored in fact tables and descriptive attributes are maintained in dimension tables. This structure enables efficient analysis across different dimensions such as property, room category, booking platform, and time.

### Dataset Size

- **134,592 booking-level records** in the primary transaction table (`fact_bookings`)
- Additional aggregated operational metrics available in `fact_aggregated_bookings`

### Data Tables

| Table | Description |
|------|------|
| **fact_bookings** | Transaction-level booking dataset containing booking status, revenue generated, revenue realized, booking platform, and property references. |
| **fact_aggregated_bookings** | Aggregated daily operational metrics, including room capacity and successful bookings for each property. |
| **dim_hotels** | Dimension table containing hotel property information such as property name, city, and category. |
| **dim_rooms** | Dimension table defining room categories and room classification details. |
| **dim_date** | Calendar dimension used for time-based analysis, including week numbers and day type (weekday/weekend). |

### Data Validation

Before building the dashboard and performing analysis, several validation checks were conducted to ensure data quality and consistency:

- **Missing Value Checks**  
  Verified that key fields such as revenue, booking status, and property identifiers did not contain critical missing values that could impact aggregation results.

- **Revenue Consistency Checks**  
  Confirmed that **revenue generated and revenue realized values align with booking status** and aggregated totals used for KPI calculations.

- **Capacity vs Bookings Validation**  
  Validated that **successful bookings (DBRN) do not exceed available capacity (DSRN)** and ensured logical consistency between available room inventory and booking counts.

These validation steps ensure that the dataset is reliable for analyzing **hotel revenue performance, booking behavior, and operational efficiency** across the Coral Properties portfolio.

## Power BI Data Model

The dashboard is built using a **star schema data model** in Power BI. This modeling approach separates **transactional fact tables** from **descriptive dimension tables**, allowing efficient aggregation, filtering, and calculation of hospitality KPIs across multiple analytical dimensions.

A star schema improves performance and simplifies analytical queries by keeping the central transactional tables connected to surrounding descriptive tables such as property, room category, and date.

<p align="center">
  <img src="images/Data Model.png" width="700">
</p>

This structure allows analysts and decision makers to explore performance metrics across **time, property, room type, and booking platform dimensions** while maintaining a scalable and maintainable BI architecture.

---

## Fact Tables

Fact tables contain the **core transactional and operational metrics** used for calculating performance indicators across the hotel portfolio.

| Table | Description |
|------|-------------|
| `fact_bookings` | This is the primary transactional dataset containing **booking-level records**. Each row represents a single booking and includes fields such as booking date, booking platform, booking status, check-in and check-out dates, number of guests, property ID, ratings given, and revenue metrics (`revenue_generated` and `revenue_realized`). This table forms the foundation for revenue-based calculations such as **ADR, RevPAR, Realisation %, cancellation rates, and booking platform analysis**. |
| `fact_aggregated_bookings` | This table contains **daily aggregated operational metrics at the property and room category level**. Key fields include `capacity` (total available room nights) and `successful_bookings`. It supports calculations related to **occupancy rates, room utilization, DSRN (Daily Sellable Room Nights), DBRN (Daily Booked Room Nights), and DURN (Daily Utilized Room Nights)**. |

Together, these fact tables provide both **granular booking-level insights** and **aggregated operational performance metrics** required for revenue management analysis.

---

## Dimension Tables

Dimension tables provide **contextual attributes** that allow fact table metrics to be segmented and analyzed across meaningful business dimensions.

| Table | Description |
|------|-------------|
| `dim_date` | Calendar dimension used for time-based analysis. Includes attributes such as date, week number, month-year, and day type (weekday vs weekend). This enables trend analysis for key metrics like **RevPAR, ADR, and occupancy across weekly and monthly periods**. |
| `dim_hotels` | Contains descriptive information about each hotel property including `property_id`, `property_name`, `city`, and `category`. This dimension enables **property-level benchmarking, city-wise performance comparisons, and portfolio analysis**. |
| `dim_rooms` | Provides room-level attributes including `room_id` and `room_class`. This table allows segmentation of performance metrics by **room category**, helping identify differences in demand, pricing, and utilization between business and luxury room segments. |

These dimension tables allow analysts to **slice and filter performance metrics across multiple operational and strategic perspectives**.

---

## Relationships

The data model links fact tables with dimension tables using **one-to-many relationships**, where dimension tables represent the "one" side and fact tables represent the "many" side.

This design ensures consistent filtering behavior across the model and allows Power BI to efficiently propagate filters from dimensions to transactional data.

| Relationship | Purpose |
|--------------|---------|
| `dim_date → fact_bookings` | Enables time-based analysis of booking transactions such as booking trends, revenue trends, and seasonality patterns. |
| `dim_date → fact_aggregated_bookings` | Supports analysis of operational metrics such as capacity and occupancy over time. |
| `dim_hotels → fact_bookings` | Links booking transactions to property-level attributes such as city and hotel category. |
| `dim_hotels → fact_aggregated_bookings` | Enables analysis of operational metrics at the property level. |
| `dim_rooms → fact_bookings` | Allows segmentation of booking transactions by room category. |
| `dim_rooms → fact_aggregated_bookings` | Supports analysis of occupancy and capacity utilization across different room classes. |

These relationships enable users to analyze metrics like **RevPAR, ADR, occupancy, and revenue trends across multiple dimensions simultaneously**.

---

## Measures Table

The model also includes a dedicated **Measures Table (`Key_Measure`)** that stores calculated DAX metrics used throughout the dashboard.

Separating measures into a dedicated table is a common Power BI best practice because it:

- Improves model organization
- Makes measures easier to maintain and update
- Keeps fact tables focused on raw data rather than calculations

Examples of key measures stored in this table include:

- ADR (Average Daily Rate)
- RevPAR (Revenue per Available Room)
- Occupancy %
- Realisation %
- DSRN, DBRN, and DURN

---

## Why This Model Matters

The star schema implemented in this project enables efficient analysis of hotel performance across multiple dimensions including:

- **Time-based analysis** of revenue and demand trends
- **Property-level benchmarking** across cities and hotel categories
- **Room category performance analysis**
- **Booking platform efficiency comparison**
- **Capacity utilization and operational performance monitoring**

This modeling approach ensures the dashboard remains **scalable, performant, and easy to extend**, supporting future analytical enhancements such as demand forecasting, customer segmentation, and revenue optimization strategies.

8. Executive Summary

This is the high-level story.

Example insights:

• Revenue is heavily concentrated in business travel
• Weekend demand significantly outperforms weekdays
• Coral Delhi is the portfolio leader in RevPAR
• Booking platforms show major realization differences

Keep this section short but strategic.

## Insights Deep Dive

This section presents the core analytical insights derived from the Coral Properties hotel dataset. Each insight is supported by a visual analysis and interpreted from a business perspective to highlight operational performance, revenue patterns, and opportunities for improvement.

---

### Insight 1 — Weekly Revenue Trends

<p align="center">
  <img src="images/weekly-trends.png" width="600">
</p>

Figure 1. Weekly trend of RevPAR, ADR, and Occupancy across the Coral Properties portfolio.  
ADR remains relatively stable while RevPAR fluctuates with occupancy, indicating that revenue performance is primarily driven by demand rather than pricing adjustments.

The visualization reveals that **ADR remains relatively stable across weeks**, indicating disciplined pricing strategies across the hotel portfolio. However, **RevPAR fluctuations closely follow occupancy trends**, suggesting that changes in revenue are primarily driven by **variations in booking demand rather than pricing adjustments**.

Periods of lower occupancy correspond directly with drops in RevPAR, highlighting the impact of demand volatility on revenue performance.

#### Business Interpretation

Several key operational insights emerge:

- Revenue performance is **primarily demand-driven rather than price-driven**.
- Pricing strategy appears consistent across time periods, reflecting stable rate management.
- Demand fluctuations significantly impact revenue outcomes.
- Improving weekday demand could stabilize RevPAR and reduce revenue volatility.

This suggests that future revenue optimization efforts should focus on **increasing occupancy through demand generation strategies rather than aggressive price adjustments.**

---

### Insight 2 — Booking Platform Efficiency

<p align="center">
  <img src="images/booking-platform-efficiency.png" width="600">
</p>

*Figure 2. ADR and Realisation % by booking platform. The chart highlights differences in pricing power and revenue capture efficiency across distribution channels.*

Different booking platforms demonstrate varying levels of pricing power and revenue efficiency. Some channels generate **higher ADR values but lower realization rates**, indicating higher commissions or promotional discounts. Others show **higher realization rates but lower ADR**, suggesting higher booking volume but lower pricing power.

#### Business Interpretation

This analysis highlights several important insights about distribution strategy:

- Direct booking channels typically produce **higher realization percentages**, since they avoid third-party commissions.
- Online travel agencies may drive booking volume but reduce realized revenue through platform fees.
- Platform efficiency varies significantly, meaning that **channel mix optimization is essential for maximizing revenue.**

Revenue managers should aim to balance **high-ADR channels with high-realization channels** rather than prioritizing booking volume alone.

---

### Insight 3 — Property Performance Benchmark

<p align="center">
  <img src="images/revpar-occupancy-matrix.png" width="600">
</p>

**Figure 3. RevPAR vs Occupancy Performance Matrix**

This chart benchmarks hotel properties using two key hospitality KPIs: RevPAR and Occupancy.  
Each point represents a property within the Coral Properties portfolio.

The vertical and horizontal reference lines represent portfolio averages, dividing the chart into four performance zones.

• **High RevPAR + High Occupancy** → top-performing properties  
• **High RevPAR + Low Occupancy** → premium pricing but underutilized capacity  
• **Low RevPAR + High Occupancy** → demand captured through lower pricing  
• **Low RevPAR + Low Occupancy** → underperforming properties requiring operational review  

This matrix highlights significant performance differences across the portfolio and helps identify properties that can serve as operational benchmarks.

#### Business Interpretation

This benchmarking analysis reveals:

- Significant performance variation across properties
- Certain properties consistently outperform others
- High-performing hotels can serve as **operational benchmarks for the portfolio**

Understanding what drives success in top-performing properties can help replicate effective pricing and demand strategies across other locations.

---

### Insight 4 — Revenue Concentration Analysis

![Revenue Pareto](images/revenue_pareto.png)

### Insight 4 — Revenue Concentration Analysis

<p align="center">
  <img src="images/revenue-contribution-by-property.png" width="600">
</p>

**Figure 4. Revenue contribution by property**

This Pareto analysis highlights how revenue is distributed across the Coral Properties portfolio. 
A limited number of properties contribute a significant share of total revenue, indicating a 
concentration of performance among top-performing locations.

Hotels such as Coral Exotica and Coral Palace generate the largest share of revenue, while 
other properties contribute smaller portions of the portfolio’s total income. This insight 
helps identify which properties drive financial performance and where operational strategies 
can be replicated to improve overall portfolio results.

This Pareto chart examines how revenue is distributed across the Coral Properties portfolio.

The analysis reveals that **a relatively small number of properties generate the majority of total revenue**, which is a common pattern in hospitality portfolios.

This concentration occurs due to differences in:

- Location demand
- property positioning
- pricing strategies
- customer segments

#### Business Interpretation

Revenue concentration introduces both opportunities and risks:

- Top-performing properties represent key revenue drivers
- Operational practices from these hotels can serve as **benchmarks for other properties**
- However, heavy dependence on a few properties increases **portfolio risk if demand shifts occur**

Diversifying revenue sources across the portfolio can improve overall resilience.

---

### Insight 5 — Capacity Utilization

![Capacity Utilization Funnel](images/capacity_funnel.png)

**Figure 5. Capacity utilization funnel**

This funnel chart illustrates how available room inventory converts into realized stays.

The stages represent:

- **DSRN (Daily Sellable Room Nights)** — total rooms available
- **DBRN (Daily Booked Room Nights)** — rooms successfully booked
- **DURN (Daily Utilized Room Nights)** — rooms actually occupied

The gaps between these stages highlight inefficiencies in capacity utilization.

#### Business Interpretation

Two operational gaps emerge:

1. **DSRN → DBRN gap**  
   Indicates untapped demand where available rooms are not being booked.

2. **DBRN → DURN gap**  
   Indicates cancellations or no-show behavior.

Improving booking conversion rates and reducing cancellations can significantly increase revenue without expanding room inventory.

This insight highlights that **capacity optimization may be more impactful than physical expansion**.

### Insight 6. Weekday vs Weekend Demand Pattern

![Weekday vs Weekend](images/weekday-weekend.png)

*Figure 6. Comparison of RevPAR, ADR, and Occupancy across weekdays and weekends.*

This chart compares key revenue metrics across weekday and weekend periods.

The analysis shows that **weekend performance consistently exceeds weekday performance**, with higher ADR and stronger occupancy levels.

This pattern reflects stronger leisure demand during weekends.

### Business Interpretation

Key insights include:

- Weekend demand drives higher revenue performance.
- Weekday demand remains relatively underutilized.
- Targeted weekday promotions or corporate partnerships could improve occupancy.

Closing the weekday demand gap would significantly improve **portfolio RevPAR without increasing inventory capacity**.

---

### Key Takeaways from the Analysis

Across the Coral Properties portfolio, several structural patterns emerge:

- Revenue volatility is driven primarily by **demand fluctuations rather than pricing changes**
- **Booking platform strategy significantly influences realized revenue**
- Some properties significantly outperform others and serve as **operational benchmarks**
- Revenue generation is **concentrated among a subset of hotels**
- Significant opportunity exists to **increase revenue through improved capacity utilization**

Together, these insights provide a foundation for **data-driven revenue management strategies across the hotel portfolio.**

## Strategic Recommendations & Performance Metrics

Here’s the thing: insights are only useful when someone turns them into measurable work. Below are the priority plays for Coral Properties, each with short, actionable steps and the KPIs you should instrument from day one.

---

### 1) Improve weekday demand

#### Why
Weekends lift the portfolio while weekdays leave capacity idle. Raising midweek occupancy raises baseline RevPAR and smooths volatility.

#### Actions
- Run three weekday acquisition pilots focused on corporate travel and extended stays.
- Launch limited-time weekday packages and test placement in-app and on partner channels.
- Create low-cost weekday promos tied to local corporates and conference calendars.

#### KPIs
- **Weekday occupancy %** — booked rooms divided by sellable rooms on Mon–Thu. Target: +5 to 10% in pilots.
- **Weekday RevPAR** — revenue divided by sellable rooms for Mon–Thu. Use as primary revenue impact metric.
- **Orders per outlet (weekday)** — weekly bookings per property on weekdays.

---

### 2) Optimize channel mix

#### Why
Different platforms drive different value. Rebalance visibility and spend to favor channels that deliver higher realized revenue.

#### Actions
- Reallocate promotional budget toward platforms with stronger realisation %.
- Negotiate listing or fee terms with high-volume platforms that under-realise.
- Run A/B tests for platform-specific packaging and cancellation rules.

#### KPIs
- **Realisation % by platform** — revenue realized divided by revenue generated.
- **ADR by platform** — realized revenue divided by bookings.
- **Booking volume and CAC by platform** — to monitor acquisition efficiency.

---

### 3) Replicate best property practices

#### Why
Top properties combine demand capture and effective pricing. Systematize those practices so new or weaker properties scale faster.

#### Actions
- Document an operational playbook from top-performing properties covering assortment, launch cadence, and pricing rules.
- Run three 90-day replication pilots and iterate weekly.
- Bake successful playbook items into the standard roll-out checklist for new openings.

#### KPIs
- **RevPAR variance across properties** — aim to reduce standard deviation.
- **Occupancy improvement at pilot sites** — percentage point change vs baseline.
- **Time to positive payback for new outlets.**

---

### 4) Prioritize medium-format Tier 3 expansion

#### Why
Medium-format outlets in Tier 3 markets show the best unit economics in the data. Focus capital where the unit economics prove out.

#### Actions
- Build a Tier 3 cluster playbook with a repeatable medium-format layout.
- Run market-level ROI screens and a small cluster pilot before greenlighting openings.

#### KPIs
- **Revenue per outlet (tier adjusted).**
- **New outlet payback period.**
- **Orders per outlet.**

---

### 5) Protect and scale core categories

#### Why
A handful of categories anchor daily revenue. Zero stockouts and prioritized visibility protect the revenue base.

#### Actions
- Enforce zero-stockout SLAs for top 20 SKUs.
- Reallocate promotion spend to high-frequency categories like fruits and snack foods.
- Pilot bundles or private label for top SKUs.

#### KPIs
- **Stockout rate for top SKUs. Target: <3%.**
- **Category revenue concentration ratio:** percent of revenue from top 3 categories.
- **Weekly sales volatility for core categories.**

---

### 6) Shift focus to order volume, not basket size

#### Why
Growth historically came from more orders, not larger baskets. Frequency is the lever that scales sustainably.

#### Actions
- Make Orders per Outlet a primary KPI and instrument it daily.
- Run lightweight retention nudges and repeat-purchase campaigns.
- Measure CAC per retained order and optimize channel spend accordingly.

#### KPIs
- **Orders per outlet (weekly).**
- **Repeat purchase rate over 90 days.**
- **CAC per retained order.**

---

### 7) Upgrade data instrumentation & reporting

#### Why
Missing timestamps and customer identifiers prevent cohort, retention, and margin analysis. Better data unlocks long-term strategy.

#### Actions
- Add `transaction_date`, `order_id`, and `customer_id` to ingestion.
- Capture refunds, discounts, and margin fields.
- Implement a star schema and automate weekly KPI reports.

#### KPIs
- **Instrumentation coverage:** percent of transactions with `customer_id` and timestamp.
- **Time to baseline retention:** weeks until first cohort metrics are available.
- **Percent of reports sourced from star schema.**

---

### 8) Run structured experiments and governance

#### Why
Controlled tests prove what actually scales. Make pilots the default, require decision gates, and measure lift before scaling.

#### Actions
- Design holdout test/control experiments for category pilots and promotional changes.
- Define minimum detectable effect and decision gates for rollouts.
- Maintain a dashboard of active experiments and outcomes.

#### KPIs
- **Percent of initiatives run as controlled experiments.**
- **Percent of pilots that meet statistical thresholds before scaling.**
- **Incremental revenue lift vs control.**

## Tools & Methods

This project was built using a focused business intelligence stack to transform raw booking data into actionable hotel revenue insights.

### Power BI
Power BI was used as the primary analytics and visualization tool. It was used to build the dashboard, create the data model, and develop interactive visuals for revenue trends, property benchmarking, booking platform performance, and capacity utilization.

### Excel
Excel was used for initial data exploration, validation, and preparation before importing the datasets into Power BI. Pivot tables were used to verify revenue totals, booking counts, and create supporting calculations for some visualizations.

### DAX (Data Analysis Expressions)
DAX was used in Power BI to calculate the key hospitality KPIs used in the dashboard.

Core metrics implemented include:

- **Revenue** – Total realized booking revenue  
- **ADR (Average Daily Rate)** – Revenue per booked room  
- **RevPAR (Revenue per Available Room)** – Revenue per available room night  
- **Occupancy %** – Booked rooms divided by total available rooms  
- **Realisation %** – Ratio of realized revenue to generated revenue  
- **DSRN (Daily Sellable Room Nights)** – Total room inventory available per day  
- **DBRN (Daily Booked Room Nights)** – Total booked room nights per day  
- **DURN (Daily Utilized Room Nights)** – Total occupied room nights per day  

## Assumptions & Limitations

Like most analytical projects built from operational datasets, this analysis includes a few assumptions and limitations that influence the scope of insights. Documenting these helps provide transparency around how the results should be interpreted.

### Assumptions

- **Revenue is treated as gross revenue.**  
  The dataset does not include cost, commission, or margin information. All revenue calculations therefore represent gross booking revenue rather than net profit.

- **Capacity values represent total sellable room nights.**  
  The `capacity` field from the aggregated dataset is assumed to represent the number of rooms available for sale each day.

- **Booking status reflects actual room utilization.**  
  Successful bookings and check-outs are treated as indicators of actual room utilization when calculating occupancy and utilization metrics.

- **Calendar data is assumed to be complete.**  
  The `dim_date` table is assumed to contain all dates required for accurate time-based analysis.

### Limitations

- **No customer-level identifiers available.**  
  The dataset does not include customer IDs, which prevents analysis of customer behavior, repeat booking patterns, or customer lifetime value.

- **Limited cancellation context.**  
  While cancellation and no-show statuses exist, the dataset does not include detailed information about cancellation timing or reasons.

- **No cost or profitability data.**  
  Without operational costs, marketing spend, or platform commissions, the analysis focuses strictly on revenue performance rather than profitability.

- **Limited geographic context.**  
  While properties are identified, the dataset does not provide deeper location attributes such as market demand conditions or competitive pricing benchmarks.

- **Static dataset timeframe.**  
  The data represents a limited time window, which restricts long-term trend analysis and seasonality modeling.

Despite these limitations, the dataset provides sufficient information to evaluate **portfolio-level revenue performance, booking channel efficiency, property benchmarking, and capacity utilization trends** across the Coral Properties hotel network.

## Next Steps

This project focuses on descriptive analytics to understand hotel revenue performance, booking platform efficiency, and property-level benchmarking. Several opportunities exist to extend this analysis into more advanced revenue management and predictive analytics capabilities.

### Implement Dynamic Pricing Based on Demand

The current dataset suggests that room prices remain largely consistent across **weekdays, weekends, and different months**, even though demand levels fluctuate across these periods.

Future analysis could introduce **demand-based pricing strategies** where room rates adjust dynamically according to demand and room availability. This would allow hotels to increase prices during high-demand periods such as weekends or peak travel seasons, while using targeted discounts during low-demand periods to improve occupancy.

Potential analysis could include:

- Identifying **high-demand periods** using occupancy and booking trends
- Evaluating the relationship between **ADR, occupancy, and RevPAR**
- Simulating pricing scenarios to maximize revenue during peak demand
- Introducing **seasonal pricing models** based on monthly demand patterns

Implementing **dynamic pricing strategies** could significantly improve overall portfolio revenue and RevPAR.

---

### Customer-Level Behavioral Analysis

The current dataset does not include customer-level identifiers. Adding customer information would enable deeper insights into guest behavior and booking patterns.

Future enhancements could include:

- Customer retention and repeat booking analysis
- Customer segmentation based on booking behavior
- Customer lifetime value (CLV) analysis
- Loyalty program effectiveness evaluation

This would allow hotels to better understand **guest preferences and long-term demand drivers**.

---

### Demand Forecasting Models

The current analysis focuses on historical performance. Future work could incorporate **forecasting models** to predict future demand and support revenue management strategies.

Possible forecasting approaches include:

- Time-series forecasting for **occupancy and RevPAR**
- Predicting seasonal demand fluctuations
- Forecasting booking volumes by property or room category
- Supporting pricing decisions using demand projections

This would allow hotel managers to **anticipate demand changes and optimize inventory allocation**.

---

### Cancellation and No-Show Analysis

Although cancellation and booking status fields exist in the dataset, deeper analysis of cancellation behavior could provide important operational insights.

Future analysis could explore:

- Cancellation trends across booking platforms
- Impact of cancellations on revenue performance
- Identifying high-risk booking channels
- Developing strategies to reduce last-minute cancellations

This would improve **revenue predictability and operational planning**.

---

### Advanced Channel Performance Analysis

The current dashboard compares booking platforms using revenue and realization metrics. Future analysis could extend this by incorporating **cost and commission structures**.

Potential improvements include:

- Platform-level profitability analysis
- Customer acquisition cost by booking platform
- Revenue contribution vs commission fees
- Channel-specific pricing strategies

This would support **more efficient distribution channel management**.

---

### Expanded Operational Performance Monitoring

Future dashboards could extend beyond revenue analytics to include broader operational metrics.

Examples include:

- Property-level performance monitoring dashboards
- Real-time booking and occupancy tracking
- Automated alerts for declining occupancy or revenue trends
- Integration with external demand indicators such as seasonal travel trends

These enhancements would transform the dashboard from a **descriptive analytics tool into a comprehensive revenue management decision-support system**.
