# Contoso Retail Sales Analysis

## 1. Introduction / Overview
* **Goal:** To analyze sales patterns for the fictional Contoso retail company using a subset of their data, identifying key trends and drivers
* **Dataset:** Contoso sample dataset (subset) simulating retail business data, including sales transactions, product details, customer information, and store data.
* **Tools:** Python data science ecosystem, PostgreSQL, Jupyter Notebook, Git.
* **Date:** April 2025 (Update with current date/year)

## 2. Business Questions
* Analyze overall sales performance and temporal trends (monthly KPIs, seasonality).
* Evaluate product portfolio performance (profitability, pricing).
* Gain insights into customer behavior and segmentation (demographics, RFM).
* Assess store and regional performance.

## 3. Data Source
* **Source:** Dataset from Luke Barousse's Intermediate SQL for Data Analytics Course
* **Tables Used:** `sales`, `product`, `customer`, `store`

## 4. Data Cleaning & Preparation
*(Detail the steps taken to create `analysis_df_processed`)*
1.  **Connection:** Established connection to PostgreSQL using SQLAlchemy.
2.  **Loading:** Loaded `sales`, `product`, `customer`, `store` tables into pandas DataFrames.
3.  **Indexing:** Set primary key columns (`productkey`, `customerkey`, `storekey`) as the index for respective dimension tables (`product_df`, `customer_df`, `store_df`) to optimize merges. Verified key uniqueness.
4.  **Date Handling:** Converted `orderdate` and `deliverydate` columns in `sales_df` to datetime objects using `pd.to_datetime`.
5.  **Merging:** Created a central `analysis_df` by performing left merges: `sales_df` -> `product_df` -> `customer_df` -> `store_df` based on their respective keys. Verified merge integrity (row counts).
6.  **Metric Calculation:** Calculated line-item level totals based on per-unit columns:
    * `line_revenue = quantity * netprice`
    * `line_cost = quantity * unitcost`
    * `line_profit = line_revenue - line_cost`
7.  **Currency Conversion:** Standardized monetary values (`line_revenue`, `line_cost`, `line_profit`) to USD using the `exchangerate` column (assuming `exchangerate` = Local Currency units per 1 USD). Created `revenue_usd`, `cost_usd`, `profit_usd`. Handled potential division by zero/null exchange rates.
8.  **Final DataFrame:** Stored the results in `analysis_df_processed`.
9.  **DateTimeIndex:** Set the `orderdate` column as the `DateTimeIndex` for `df` and sorted the index for time series analysis.
10. **Result:** The final `df` DataFrame has shape (199873, 64 columns) and is ready for analysis.

## 6. Exploratory Data Analysis (EDA)
*(Upcoming)*

## 7. Analysis & Findings
*(Upcoming - Will address the business questions outlined above)*
* Theme 1: Temporal Sales Analysis
* Theme 2: Product Performance
* Theme 3: Customer Insights
* Theme 4: Store & Regional Performance

## 8. Visualizations
*(Upcoming - Key visualizations will be generated during the analysis)*

## 9. Conclusion & Summary
*(Upcoming)*

## 10. Future Work & Limitations
*(Upcoming)*