# QuickBite-Express-Analysis-Dashboard

🚀 Crisis Impact Analysis Dashboard (SQL + Power BI)
📋 Overview

This project analyzes the impact of a business crisis (Jan–Sep 2025) on customer behavior, order patterns, cancellations, and revenue performance.

The analysis combines SQL for data preparation and Power BI for modeling, DAX calculations, and visualization — turning raw transactional data into clear business insights for management and stakeholders.

🛠️ Technologies Used

SQL (MySQL) – Data cleaning, transformation, and exploratory queries

Power BI – Data modeling, DAX measures, and dashboard visualization

DAX (Data Analysis Expressions) – Advanced measures for trends, KPIs, and comparisons

Excel/CSV – Source data review and structure verification

🧱 Data Workflow
1. Data Cleaning and Preparation (SQL)

Used SQL to:

Handle missing or inconsistent values (NULL orders, blank cities, etc.)

Remove duplicates and invalid timestamps

Convert timestamps to proper date formats

Create helper columns for analysis (e.g., Month, Year, Period)

Join multiple tables (fact_orders, dim_customer, dim_restaurant, etc.) to form a unified dataset

Key operations:

-- Example: Identifying missing or invalid order timestamps
SELECT * FROM fact_orders
WHERE order_timestamp IS NULL OR order_timestamp = '';

-- Create new columns
ALTER TABLE fact_orders
ADD COLUMN period VARCHAR(20);

2. Data Modeling (Power BI)

Imported the cleaned SQL data into Power BI and built a star schema model:

Fact tables:

fact_orders

fact_ratings

fact_delivery_performance

Dimension tables:

dim_customer

dim_restaurant

dim_date

Relationships were built using:

customer_id

restaurant_id

order_id

3. DAX Calculations and Business Metrics

Created multiple measures to answer key business questions.

Examples:

Total Orders

Total Revenue = SUMX(fact_orders, subtotal - discount + delivery_fee)

Cancellation Rate %

Avg Delivery Time

Avg Rating

SLA Compliance %

Order Decline % (Pre-crisis vs Crisis)

Each metric helped uncover specific performance shifts across phases.

4. Power BI Dashboard

A multi-page dashboard was built with slicers and navigation to guide stakeholders through insights:

Page	Purpose
Executive Overview	Snapshot of overall performance
Orders & Revenue	Volume and revenue trends
Cancellations & SLA	Operational performance
Customer Sentiment	Rating trends and review keywords
High-Value Customers	Loyalty impact and behavior change
Recommendations	Final business takeaways

Each page includes:

KPIs for quick comparison

Line and bar charts for trend analysis

Word Cloud for review sentiment

Dynamic DAX insights to auto-update summaries

🧩 Business Problems Solved

Monthly Orders Decline:
Compared total orders across Pre-crisis (Jan–May 2025) vs Crisis (Jun–Sep 2025) to measure demand drop.

City Performance:
Identified top 5 city groups with highest % order decline.

Cancellation Analysis:
Tracked cancellation rate trends and most affected cities.

Delivery SLA:
Evaluated average delivery time and SLA compliance before vs during the crisis.

Customer Ratings:
Analyzed average ratings month-by-month to find sharpest sentiment drops.

Sentiment Analysis:
Extracted top negative keywords from customer reviews using Power BI Word Cloud.

Revenue Impact:
Calculated total revenue loss (subtotal – discount + delivery fee).

Loyalty Analysis:
Identified top 5% high-value customers and analyzed how many stopped ordering or reduced ratings.

🧠 Key Challenges Faced
Challenge	Description	Solution
Incomplete Timestamps	Missing order_timestamp caused blank periods	Filtered invalid rows in SQL; added “Out of Range” flag
Blank Period Values in Power BI	DAX period logic returned (Blank) for null or out-of-range data	Added ELSE condition in DAX and filtered
Large Data Volume	>100K rows slowed visuals	Optimized DAX measures using SUMX and filtering context
Customer Review Cleaning	Text reviews contained special characters and stopwords	Cleaned in Power Query using Text.Replace and TransformColumns
Complex DAX Logic	Needed to compare multiple metrics across two time phases	Built modular measures for Pre-crisis and Crisis periods
📈 Insights Summary

Orders fell 28% during the crisis period.

Cancellations rose by 65%, especially in Delhi and Mumbai.

Revenue dropped 31%, mainly in top metros.

Average rating decreased from 4.6 to 4.2, with complaints about delivery delays.

High-value customers (top 5%) reduced orders by 37% and showed lower satisfaction.

🗺️ Dashboard Navigation

The final dashboard includes a navigation bar on every page for easy movement:

Button	Target Page
Overview	Executive Summary
Orders	Orders & Revenue
Cancellations	Cancellation & SLA
Sentiment	Customer Feedback
Loyalty	High-Value Customers
Insights	Recommendations

This layout makes it easy for non-technical clients to explore findings without confusion.

🧰 Repository Contents
├── SQL_Scripts/
│   ├── data_cleaning.sql
│   ├── transformation_queries.sql
│   └── analysis_queries.sql
│
├── PowerBI/
│   ├── Crisis_Impact_Dashboard.pbix
│   ├── Dashboard_Screenshots/
│
├── README.md
└── metadata.txt

🧾 Key Operations Performed

Data Import and Cleaning in MySQL

Transformation and Aggregation using SQL

Modeling and Relationships setup in Power BI

DAX Measures for KPIs and comparisons

Time-series and sentiment trend analysis

Dashboard design with navigation and dynamic insights

🏁 Conclusion

This project demonstrates how SQL + Power BI can deliver full-cycle analytics — from raw data to strategic insights.
The final dashboard provides an interactive story of how a business crisis affected performance, allowing decision-makers to act on data rather than guesswork.

📫 Contact

Author: Nishit Kumar
Role: Data Analyst
Email: nishit7902@gmail.com
