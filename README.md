# **Databricks SaaS Churn Analysis (PySpark + Spark SQL + Power BI)**

---

## **Executive Summary**

This project delivers an end-to-end SaaS churn analysis using Databricks and Power BI, following a structured **bronze–silver–gold analytics architecture**.
Raw subscription data was ingested and cleaned using PySpark, churn metrics were modeled using Spark SQL views, and insights were visualized through a Power BI dashboard connected to Databricks SQL Warehouse.

The analysis identifies **high-risk churn segments**, highlights **revenue exposure**, and translates analytical findings into **actionable business recommendations** focused on retention and revenue protection.

---

## **Business Problem**

Subscription-based businesses face direct revenue loss when customers churn.
The key business questions addressed in this analysis are:

* What is the overall churn and retention rate?
* Which customer segments churn the most?
* When in the customer lifecycle does churn occur?
* How much revenue is at risk due to churn?
* Which levers can be used to reduce churn and protect revenue?

The objective is not prediction, but **descriptive and diagnostic analytics** to support strategic retention decisions.

---

## **Methodology**

### 1. Data Ingestion (Bronze Layer)

* Dataset ingested into Databricks as a raw Delta table using the file upload interface.
* No transformations applied to preserve source data integrity.

### 2. Data Cleaning & Feature Engineering (Silver Layer)

* Cleaned data using **PySpark**:

  * Converted blank numeric fields (e.g., `TotalCharges`) to proper numeric types.
  * Standardized churn into a binary `churn_flag`.
  * Engineered tenure buckets to support lifecycle analysis.
* Created a clean, analytics-ready customer table.

### 3. Metrics Layer (Gold Layer)

* Built reusable **Spark SQL views** for:

  * Overall churn and retention KPIs
  * Churn by contract type
  * Churn by tenure bucket
  * Churn by monthly charge bands
  * Revenue at risk (MonthlyCharges proxy)
* Views act as a **single source of truth** for BI consumption.

### 4. Visualization & Storytelling

* Connected Power BI to Databricks SQL Warehouse.
* Built a dashboard with:

  * KPI cards
  * Segment-wise churn comparisons
  * Revenue exposure analysis
* Corrected aggregation logic to ensure **weighted churn rates**, not summed ratios.

---

## **Skills**

* Databricks (Notebooks, SQL Warehouse)
* PySpark (data cleaning, feature engineering)
* Spark SQL (analytical views, metric modeling)
* Delta Lake (bronze–silver–gold architecture)
* Power BI (data modeling, DAX, dashboard design)
* Churn analytics & business storytelling

---

## **Results and Business Recommendations**

### Key Results

* **Overall Churn Rate:** 26.54%
* **Retention Rate:** 73.46%
* **Revenue at Risk (proxy):** 30.50% of monthly charges
* **Highest churn segment:** Month-to-month contracts (~42.7%)
* **Lifecycle risk:** Churn highest in the first 0–12 months
* **Revenue insight:** Revenue risk exceeds customer churn, indicating higher-value customers are more likely to churn

### Business Recommendations

1. **Contract Upgrade Strategy**

   * Incentivize month-to-month customers to move to annual contracts.
   * Focus upgrades within the first year of tenure.

2. **Early Lifecycle Retention Programs**

   * Improve onboarding, billing clarity, and early customer support.
   * Target customers in the first 12 months where churn risk is highest.

3. **Revenue Protection Focus**

   * Prioritize retention efforts for high monthly charge customers.
   * Offer proactive support and targeted incentives for premium segments.

---
### Dashboard
<img width="2000" height="1156" alt="image" src="https://github.com/user-attachments/assets/c2726271-5eea-437f-a0e4-f5811023491e" />



## **Next Steps**

* Extend analysis to service-level features (e.g., add-ons, support usage).
* Build rule-based churn risk segmentation (non-ML).
* Incorporate time-series data to calculate MRR churn, GRR, and NRR.
* Add cohort-based retention analysis once longitudinal data is available.

---


