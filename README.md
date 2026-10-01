🛒 Retail Data Engineering Project --- Microsoft Fabric
An end-to-end Retail Data Engineering pipeline built using Microsoft
Fabric, implementing a Medallion Architecture (Bronze → Silver →
Gold) with PySpark, Delta tables, and Power BI.
The project focuses on ingesting raw retail data, cleaning and
standardizing it in the Silver layer, creating business-level KPIs in
the Gold layer, and visualizing the results through Power BI.
📌 Project Overview
The objective of this project is to build a complete retail analytics
pipeline that transforms raw, inconsistent retail data into clean,
analysis-ready business data.
Pipeline
Raw Retail Data
      │
      ▼
┌─────────────────────┐
│       BRONZE        │
│    Raw Data Layer   │
│                     │
│ Orders              │
│ Inventory           │
│ Returns             │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│       SILVER        │
│  Cleaned Data Layer │
│                     │
│ Data Cleaning       │
│ Standardization     │
│ Data Type Handling  │
│ Null Handling       │
│ Deduplication       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│        GOLD         │
│   Business KPIs     │
│                     │
│ Product Analytics   │
│ Revenue             │
│ Orders              │
│ Returns             │
│ Inventory           │
│ Profit              │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│      POWER BI       │
│ Interactive Report  │
└─────────────────────┘
🏗️ Architecture
The project follows the Medallion Architecture implemented in
Microsoft Fabric.
🥉 Bronze Layer
The Bronze layer stores the raw retail datasets with minimal
transformation.
Datasets used:
- orders_data.parquet
- inventory_data.parquet
- returns_data.xlsx.parquet
The raw files are stored in the Lakehouse Bronze area.
🥈 Silver Layer
The Silver layer contains cleaned and standardized data.
Three Delta tables were created:
silver_orders
silver_inventory
silver_returns
Main transformations include:
- Column name standardization
- Date format normalization
- Numeric value extraction
- Currency symbol removal
- Data type conversion
- Customer ID standardization
- Email normalization
- Payment mode cleaning
- Promo code handling
- Warehouse/address cleaning
- Boolean standardization
- Null handling
- Duplicate removal
- Invalid record filtering
- Hash generation for order tracking
🥇 Gold Layer
The Gold layer combines the cleaned Silver datasets and creates
product-level business KPIs.
Final Gold table:
gold_product_kpis
The table contains metrics such as:
- Total Orders
- Unique Customers
- Total Returns
- Return Rate
- Total Revenue
- Average Order Value
- Total Stock
- Average Cost
- Net Profit
🛠️ Technologies Used
  Technology             Purpose
  Microsoft Fabric   End-to-end data platform
  Fabric Lakehouse   Data storage and analytics
  OneLake            Unified data storage
  PySpark            Data transformation and processing
  Spark SQL          Table access and analytics
  Delta Lake         Silver and Gold table storage
  Power BI           Dashboard and visualization
  Fabric Notebook    PySpark development
  GitHub             Project documentation and version control
📂 Project Structure
A suggested GitHub repository structure:
Retail-Data-Engineering-Fabric/
│
├── README.md
│
├── notebooks/
│   └── Retail_Notebook.py
│
├── sql/
│   └── gold_kpi_queries.sql
│
├── architecture/
│   └── medallion_architecture.png
│
├── screenshots/
│   ├── bronze_layer.png
│   ├── silver_layer.png
│   ├── gold_layer.png
│   └── powerbi_dashboard.png
│
└── documentation/
    └── project_documentation.pdf
Raw customer or business data should not be uploaded to a public
GitHub repository.

🔄 Data Processing Workflow
1. Data Ingestion
Raw retail datasets were loaded into the Microsoft Fabric Lakehouse
Bronze layer.
Orders
Inventory
Returns
   ↓
Fabric Lakehouse
   ↓
Bronze
2. Silver Transformation
PySpark was used to clean and standardize the datasets.
Examples include:
.withColumnRenamed(...)
.withColumn(...)
regexp_replace(...)
regexp_extract(...)
to_date(...)
trim(...)
upper(...)
lower(...)
coalesce(...)
dropna(...)
dropDuplicates(...)
3. Gold Transformation
The Silver tables were joined and aggregated to produce product-level
KPIs.
silver_orders
       │
       ├──────────────┐
       │              │
       ▼              ▼
silver_returns   silver_inventory
       │              │
       └──────┬───────┘
              ▼
       Product KPIs
              │
              ▼
      gold_product_kpis
4. Visualization
The Gold table was connected to Power BI to create an interactive retail
analytics report.
📊 Gold KPI Model
The Gold table includes the following analytical fields:
  KPI                                 Description
  ProductName                       Product identifier/name used for
                                      product-level analysis
  Total_Orders                      Number of orders
  Unique_Customers                  Distinct customers
  Total_Returns                     Number of returns
  Return_Rate_Percent               Return percentage
  Total_Revenue                     Total order revenue
  Avg_Order_Value                   Average order value
  Total_Stock                       Available inventory quantity
  Avg_Cost                          Average product cost
  Net_Profit                        Revenue-based profit metric
📈 Power BI Dashboard
The Power BI report is designed to provide a high-level view of retail
performance.
KPI Cards
- Total Revenue
- Total Orders
- Unique Customers
- Total Returns
- Net Profit
Visualizations
- Revenue by Product
- Orders by Product
- Inventory Stock by Product
- Average Order Value by Product
- Return Rate by Product
🧹 Data Quality Handling
The source datasets contain inconsistent values and formats.
Examples of data quality issues handled include:
Dates
Multiple date formats were normalized into standard date values.
2023/06/01
01-07-2023
2023.06.30
2023-07-20
25.07.2023
07/15/2023
Stock
Text-based quantities were converted into numeric values where possible.
25 units → 25
twenty → 20
fifteen → 15
Currency
Currency symbols and text were removed before converting values to
numeric types.
$700      → 700
Rs.25000  → 25000
INR 72000 → 72000
Text Standardization
Text fields were cleaned using trimming, case normalization, and removal
of unwanted characters.
🚀 Key Learning Outcomes
This project provided hands-on experience with:
- Microsoft Fabric Lakehouse
- OneLake
- Fabric Notebooks
- PySpark
- Data ingestion
- Medallion Architecture
- Data cleansing
- Data transformation
- Delta tables
- Data quality handling
- Data joins
- Aggregations and KPIs
- Power BI reporting
- End-to-end data pipeline development
🎯 Project Outcome
The project demonstrates an end-to-end data engineering workflow:
Raw Data
   ↓
Microsoft Fabric Lakehouse
   ↓
Bronze Layer
   ↓
PySpark Transformations
   ↓
Silver Layer
   ↓
KPI Aggregations
   ↓
Gold Layer
   ↓
Power BI Dashboard
The final solution converts raw retail datasets into structured,
analytics-ready data and provides a business-facing reporting layer
through Power BI.
👩‍💻 Author
Anna Vincent
B.Tech Computer Science & Engineering
Data Engineering Trainee
Areas of Interest
- Data Engineering
- Microsoft Fabric
- Azure
- PySpark
- SQL
- Data Analytics
- Power BI
⭐ Project Highlights
- Built an end-to-end retail data pipeline using Microsoft Fabric
- Implemented Bronze, Silver, and Gold data layers
- Performed real-world data cleaning and standardization using PySpark
- Created Delta-based Silver and Gold tables
- Developed product-level business KPIs
- Connected the Gold layer to Power BI for reporting
