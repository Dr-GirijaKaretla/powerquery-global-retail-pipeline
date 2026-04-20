# powerquery-global-retail-pipeline

📊 Power Query Global Retail Analytics Pipeline
A complete end‑to‑end data transformation project using Power Query (Excel/Power BI)

📌 Overview
This project demonstrates a realistic, enterprise‑style data transformation pipeline built using Power Query.
It simulates a global retail business operating across multiple regions, currencies, and product categories.

The goal of this project is to showcase:
Professional‑grade data ingestion
Complex data cleaning and transformation
Multi‑table joins and relationships
Folder‑based ingestion of monthly sales files
Currency conversion using lookup tables
Target vs Actual performance modelling

Returns processing
A clean, refreshable Power Query pipeline
This repository is designed as a portfolio project to demonstrate Power Query skills for data analyst, BI analyst, and reporting roles.

🗂️ Project Structure
Code
project/
   data/
      sales_data/
         sales_2024_01.csv
         sales_2024_02.csv
         sales_2024_03.csv
         sales_2024_04.csv
         sales_2024_05.csv
         sales_2024_06.csv
      product_master.csv
      store_master.csv
      currency_rates.csv
      sales_targets.csv
      returns.csv
   Retail_Analytics.xlsx (or .pbix)
   M_Code.txt
   README.md
✔ Fact data
Stored in a folder (sales_data) for folder ingestion.

✔ Dimension / lookup tables
Stored as individual CSV files for direct table ingestion.

🎯 Business Scenario
A global retail company sells electronics and accessories across:
APAC
North America
Europe

Each month, stores upload CSV files containing sales transactions.
The analytics team must:
Combine all monthly files
Clean and standardize the data
Convert currencies to USD
Join product and store metadata
Compare actual sales to monthly targets
Track returns and net sales
Produce a refreshable dataset for reporting

This project replicates that workflow.

🔧 Power Query Pipeline (Step‑by‑Step)
1. Data Ingestion
Load monthly sales files using Get Data → From Folder
Load lookup tables individually:
Product Master
Store Master
Currency Rates
Sales Targets

Returns

2. Data Cleaning
Remove duplicates
Fix data types (dates, numbers, text)
Handle missing values
Standardize salesperson names
Remove extra columns in inconsistent files
Replace invalid values (e.g., “ten” → 10)

3. Data Transformation
Expand folder files into a single fact table

Merge lookups:
Sales ↔ Product Master
Sales ↔ Store Master
Sales ↔ Currency Rates
Sales ↔ Sales Targets
Sales ↔ Returns

Add calculated columns:
SalesAmount = Quantity × UnitPrice
SalesUSD = SalesAmount × RateToUSD
Month = Date.YearMonth
NetSales = SalesUSD – ReturnedAmount

4. Business Logic
Region‑level performance
Store‑level performance
Product category analysis
Target vs Actual variance
Return rate analysis

5. Output
Clean, model‑ready dataset loaded into Excel or Power BI
Refreshable with one click

🧩 Data Model Diagram (ASCII)
Code
                 ┌──────────────────────┐
                 │   product_master     │
                 └──────────┬───────────┘
                            │
                            │ ProductID
                            │
┌──────────────┐     ┌──────▼───────┐      ┌──────────────────────┐
│ store_master │◄────│   SALES      │──────►│  currency_rates      │
└──────┬───────┘     └──────┬───────┘      └──────────────────────┘
       │                    │
       │ StoreID            │ Month
       │                    │
       │            ┌───────▼────────┐
       └────────────► sales_targets  │
                    └────────────────┘

                    ┌────────────────┐
                    │    returns     │
                    └────────────────┘
📈 Key Skills Demonstrated
Power Query / M Language
Folder ingestion
Append queries
Merge queries (joins)
Custom columns
Conditional logic
Error handling
Data type enforcement
Parameterized paths
M code review and editing
Data Modelling
Fact + dimension structure
Lookup relationships
Currency normalization
Target vs actual modelling
Analytics Concepts
Sales performance
Return rate
Profitability
Regional analysis
Trend analysis

🧪 Sample Insights Enabled by This Pipeline
Which region is performing above/below target
Which products generate the highest revenue
Which stores have the highest return rates
Month‑over‑month sales trends
Currency impact on revenue
Salesperson performance

🚀 How to Use This Project
Clone or download the repository
Open the Excel or Power BI file
Update the folder path parameter (if included)
Click Refresh All
Explore the transformed dataset



