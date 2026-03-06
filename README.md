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
| **fact_aggregated_bookings** | Aggregated daily operational metrics including room capacity and successful bookings for each property. |
| **dim_hotels** | Dimension table containing hotel property information such as property name, city, and category. |
| **dim_rooms** | Dimension table defining room categories and room classification details. |
| **dim_date** | Calendar dimension used for time-based analysis including week numbers and day type (weekday/weekend). |

### Data Validation

Before building the dashboard and performing analysis, several validation checks were conducted to ensure data quality and consistency:

- **Missing Value Checks**  
  Verified that key fields such as revenue, booking status, and property identifiers did not contain critical missing values that could impact aggregation results.

- **Revenue Consistency Checks**  
  Confirmed that **revenue generated and revenue realized values align with booking status** and aggregated totals used for KPI calculations.

- **Capacity vs Bookings Validation**  
  Validated that **successful bookings (DBRN) do not exceed available capacity (DSRN)** and ensured logical consistency between available room inventory and booking counts.

These validation steps ensure that the dataset is reliable for analyzing **hotel revenue performance, booking behavior, and operational efficiency** across the Coral Properties portfolio.

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

![Weekly Revenue Trends](images/weekly_trends.png)

**Figure 1. Weekly trend of RevPAR, ADR, and Occupancy**

This chart analyzes how the three key hospitality KPIs — **RevPAR, ADR, and Occupancy** — evolve over time.

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

![Booking Platform Efficiency](images/channel_efficiency.png)

**Figure 2. ADR vs Realisation % by booking platform**

This visualization evaluates the performance of different booking channels by comparing **Average Daily Rate (ADR)** with **Realisation %**.

Different booking platforms demonstrate varying levels of pricing power and revenue efficiency. Some channels generate **higher ADR values but lower realization rates**, indicating higher commissions or promotional discounts. Others show **higher realization rates but lower ADR**, suggesting higher booking volume but lower pricing power.

#### Business Interpretation

This analysis highlights several important insights about distribution strategy:

- Direct booking channels typically produce **higher realization percentages**, since they avoid third-party commissions.
- Online travel agencies may drive booking volume but reduce realized revenue through platform fees.
- Platform efficiency varies significantly, meaning that **channel mix optimization is essential for maximizing revenue.**

Revenue managers should aim to balance **high-ADR channels with high-realization channels** rather than prioritizing booking volume alone.

---

### Insight 3 — Property Performance Benchmark

![Property Performance](images/property_scatter.png)

**Figure 3. RevPAR vs Occupancy by property**

This scatter plot compares hotel properties based on two critical performance metrics: **RevPAR and Occupancy %**.

The visualization divides properties into performance zones:

- **High RevPAR + High Occupancy** → Top-performing properties
- **High Occupancy + Low RevPAR** → Possible underpricing
- **Low Occupancy + High RevPAR** → Premium pricing but weaker demand
- **Low Occupancy + Low RevPAR** → Underperforming properties

In the analysis, **Coral Delhi emerges as the strongest-performing property**, achieving both high RevPAR and strong occupancy levels.

#### Business Interpretation

This benchmarking analysis reveals:

- Significant performance variation across properties
- Certain properties consistently outperform others
- High-performing hotels can serve as **operational benchmarks for the portfolio**

Understanding what drives success in top-performing properties can help replicate effective pricing and demand strategies across other locations.

---

### Insight 4 — Revenue Concentration

![Revenue Pareto](images/revenue_pareto.png)

**Figure 4. Revenue contribution by property**

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
