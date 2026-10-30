# 🏢 SQL Data Warehouse Project

### Building an End-to-End Data Warehouse Using Microsoft SQL Server

## 📌 Project Overview

This project focuses on designing and implementing a modern **SQL Server Data Warehouse** that integrates data from multiple source systems (CRM and ERP) into a centralized repository for efficient data management, transformation, and analytical reporting.

The project follows the **Medallion Architecture (Bronze, Silver, and Gold)** to organize data into three layers: raw data ingestion, data cleansing and transformation, and business-ready analytical models.

Using six CSV datasets, the project demonstrates how raw operational data can be transformed into structured, reliable, and analytics-ready information using SQL Server and T-SQL.

## 🎯 Project Objectives

- Design and implement a modern data warehouse using SQL Server.
- Integrate data from CRM and ERP source systems.
- Build an ETL pipeline to extract, transform, and load data.
- Implement Bronze, Silver, and Gold data layers.
- Perform data cleaning, standardization, and transformation using SQL.
- Develop a dimensional data model using a Star Schema.
- Create fact and dimension views for analytical queries.
- Perform data quality checks to improve data reliability.

## 🏗️ Data Architecture

The project follows the Medallion Architecture, consisting of three layers:

### 1. 🥉 Bronze Layer – Raw Data

The Bronze layer stores raw data directly from the six CSV source files.

**Key operations:**
- Create database schemas and raw tables.
- Load source data into SQL Server using BULK INSERT.
- Preserve the original source data without applying business transformations.
- Use stored procedures to manage data loading.

### 2. 🥈 Silver Layer – Data Cleansing & Transformation

The Silver layer processes raw data from the Bronze layer and prepares it for analytical use.

**Key operations:**
- Handle NULL and missing values.
- Remove duplicate records.
- Standardize data formats and values.
- Perform data type conversions.
- Validate and clean customer and product information.
- Apply data transformation rules.
- Integrate related CRM and ERP data.

### 3. 🥇 Gold Layer – Business-Ready Data

The Gold layer contains the final analytical data models.

It organizes the transformed data into a **Star Schema** consisting of fact and dimension views.

**Key operations:**
- Create dimension views for customers and products.
- Create fact views for sales transactions.
- Integrate data from multiple source systems.
- Establish relationships between fact and dimension entities.
- Prepare structured data for business intelligence and analytical queries.

## 📂 Project Structure

```text
sql_datawarehouse_project/
│
├── datasets/
│   ├── source_crm/
│   │   ├── cust_info.csv
│   │   ├── prd_info.csv
│   │   └── sales_details.csv
│   │
│   └── source_erp/
│       ├── CUST_AZ12.csv
│       ├── LOC_A101.csv
│       └── PX_CAT_G1V2.csv
│
├── docs/
│   └── Project documentation and diagrams
│
├── scripts/
│   ├── init_database.sql
│   │
│   ├── bronze/
│   │   ├── ddl_bronze.sql
│   │   └── proc_load_bronze.sql
│   │
│   ├── silver/
│   │   ├── ddl_silver.sql
│   │   └── proc_load_silver.sql
│   │
│   └── gold/
│       └── ddl_gold.sql
│
├── tests/
│   └── Data quality and validation scripts
│
├── LICENSE
└── README.md
```

*Note: The tree above illustrates the intended organization. Adjust individual filenames and subfolders to match the actual repository.*

## 📊 Dataset Description

The project uses six datasets from two different source systems.

### CRM (Customer Relationship Management)

| Dataset | Description |
|---|---|
| `cust_info.csv` | Contains customer details such as customer ID, name, gender, and marital status. |
| `prd_info.csv` | Contains product details, including product ID, product name, cost, and product line. |
| `sales_details.csv` | Contains sales transaction details such as order number, customer ID, product ID, order date, quantity, and sales amount. |

### ERP (Enterprise Resource Planning)

| Dataset | Description |
|---|---|
| `CUST_AZ12.csv` | Contains additional customer information, including birthdate and gender. |
| `LOC_A101.csv` | Contains customer location information, including country details. |
| `PX_CAT_G1V2.csv` | Contains product category information, including category, subcategory, and maintenance details. |

## 🔄 ETL Pipeline

The data warehouse implements an ETL workflow using SQL Server.

```text
       CRM SOURCE SYSTEM          ERP SOURCE SYSTEM
       ┌───────────────┐          ┌───────────────┐
       │ cust_info.csv │          │ CUST_AZ12.csv │
       │ prd_info.csv  │          │ LOC_A101.csv  │
       │ sales_details │          │ PX_CAT_G1V2   │
       └───────┬───────┘          └───────┬───────┘
               │                         │
               └────────────┬────────────┘
                            ▼
                   ┌─────────────────┐
                   │  BRONZE LAYER   │
                   │   Raw Data      │
                   └────────┬────────┘
                            ▼
                   ┌─────────────────┐
                   │  SILVER LAYER   │
                   │ Clean & Transform│
                   └────────┬────────┘
                            ▼
                   ┌─────────────────┐
                   │   GOLD LAYER    │
                   │ Analytical Data │
                   └────────┬────────┘
                            ▼
                   ┌─────────────────┐
                   │  DATA ANALYSIS  │
                   │ SQL Queries     │
                   │ Reporting       │
                   └─────────────────┘
```

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Microsoft SQL Server | Data warehouse development and storage |
| SQL / T-SQL | Data manipulation and transformation |
| SQL Server Management Studio (SSMS) | Database development and management |
| Stored Procedures | ETL process execution |
| BULK INSERT | Loading CSV source files |
| Common Table Expressions (CTEs) | Organizing complex SQL queries |
| Views | Creating analytical data models |
| Git & GitHub | Version control and project management |

## 🧠 Key SQL Concepts Implemented

- Database and schema creation
- DDL and DML operations
- BULK INSERT
- Stored Procedures
- Data type conversion
- NULL handling
- Data cleaning and standardization
- Duplicate detection and removal
- Joins and subqueries
- Common Table Expressions (CTEs)
- Window Functions
- Aggregate Functions
- CASE Statements
- Views
- Fact and Dimension Modeling
- Data Quality Validation

## ⭐ Data Modeling

The Gold layer follows the Star Schema dimensional modeling approach.

**Dimension Tables:**
- `dim_customers` – Contains customer-related information.
- `dim_products` – Contains product-related information.

**Fact Table:**
- `fact_sales` – Contains sales transaction measures and references to customer and product dimensions.

This structure helps simplify analytical queries and supports reporting on sales performance, customer behavior, and product performance.

## 🚀 Getting Started

### Prerequisites

- Microsoft SQL Server
- SQL Server Management Studio (SSMS)
- Git
- Six source CSV datasets included in the repository

### Step 1: Clone the Repository

```bash
git clone https://github.com/tejas123106/sql_datawarehouse_project.git
```

### Step 2: Navigate to the Project Directory

```bash
cd sql_datawarehouse_project
```

### Step 3: Create the Database

Open SQL Server Management Studio and execute the database initialization script:

```sql
scripts/init_database.sql
```

### Step 4: Create Bronze Layer Tables

Execute the Bronze layer DDL script to create the raw data tables.

```sql
scripts/bronze/ddl_bronze.sql
```

### Step 5: Load Bronze Layer Data

Execute the Bronze loading stored procedure script.

```sql
scripts/bronze/proc_load_bronze.sql
```

Update the CSV file paths inside the loading procedure to match your local dataset location.

Execute the procedure:

```sql
EXEC bronze.load_bronze;
```

### Step 6: Create and Load Silver Layer

Execute the Silver layer table creation script:

```sql
scripts/silver/ddl_silver.sql
```

Execute the Silver layer transformation procedure script:

```sql
scripts/silver/proc_load_silver.sql
```

Run the procedure:

```sql
EXEC silver.load_silver;
```

### Step 7: Create Gold Layer

Execute the Gold layer script to create the analytical views:

```sql
scripts/gold/ddl_gold.sql
```

### Step 8: Validate the Data

Execute the available SQL validation scripts inside the `tests/` folder to verify data consistency and quality.

## 📈 Expected Outcomes

- A centralized data warehouse integrating six CRM and ERP datasets.
- A structured Bronze, Silver, and Gold architecture.
- A repeatable SQL-based ETL pipeline.
- Cleaned and standardized customer, product, and sales information.
- A Star Schema for analytical querying.
- Business-ready fact and dimension views.
- Improved data consistency and reliability.

## 🎓 Learning Outcomes

Through this project, I gained practical experience in:

- Designing a modern data warehouse architecture.
- Working with multiple source systems.
- Developing ETL workflows using SQL Server.
- Writing SQL stored procedures for data loading.
- Performing data cleaning and transformation.
- Implementing dimensional data modeling.
- Developing analytical queries and data quality checks.


