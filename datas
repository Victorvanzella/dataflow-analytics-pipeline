# 🚀 DataFlow Analytics Pipeline

> End-to-end data engineering pipeline for ingestion, transformation, validation, orchestration and analysis of e-commerce data.

<p align="center">
  <img src="architecture.png" alt="DataFlow Analytics Pipeline Architecture" width="100%">
</p>

---

## 📌 Overview

The **DataFlow Analytics Pipeline** is a portfolio project designed to simulate a real-world data engineering environment for an e-commerce company.

The solution is designed to ingest sales, customer and product data, store raw information in a Data Lake, transform and validate datasets, load analytical structures into a Data Warehouse, and make business-ready information available for analytics.

The project focuses on practical Data Engineering concepts including ETL/ELT, data quality, orchestration, dimensional modeling, cloud storage, SQL and business intelligence.

> **Portfolio note:** the architecture image above is an overview illustration. Tool-specific evidence such as Airflow, PostgreSQL, AWS and Power BI screenshots will be added from the running implementation as the project is executed.

---

## 🎯 Project Objective

Build a reliable and reproducible data pipeline capable of:

- Ingesting data from external sources
- Storing raw data in a Data Lake
- Cleaning and transforming datasets
- Applying data quality rules
- Orchestrating ETL workflows
- Loading structured data into a Data Warehouse
- Implementing dimensional data modeling
- Providing analytical datasets through SQL
- Supporting business intelligence dashboards

---

## 🏗️ Architecture

```text
Data Source / API
       │
       ▼
    Python
   Ingestion
       │
       ▼
    AWS S3
 Bronze Layer
       │
       ▼
    Airflow
 Orchestration
       │
       ▼
Python / Pandas
 Transformation
       │
       ▼
    AWS S3
 Silver / Gold
       │
       ├───────────────┐
       ▼               ▼
 PostgreSQL         AWS Athena
Data Warehouse      SQL Analysis
       │               │
       └───────┬───────┘
               ▼
           Power BI
           Analytics
```

---

## 🛠️ Technologies

### Programming & Data
- Python
- Pandas
- SQL
- PostgreSQL

### Data Engineering
- ETL / ELT
- Data Quality
- Data Lake
- Data Warehouse
- Dimensional Modeling
- Apache Airflow

### Cloud
- AWS S3
- AWS Glue
- AWS Athena

### Infrastructure
- Docker
- Docker Compose
- Linux

### Analytics
- Power BI
- DAX

### Version Control
- Git
- GitHub

---

# 🔄 Data Pipeline

The pipeline is organized into the following stages.

### 1. Extract

Data is collected from external sources such as APIs and structured files.

```text
API / CSV / JSON
       ↓
    Python
```

The ingestion layer is responsible for collecting source data while preserving the original structure.

### 2. Raw Data — Bronze

Raw data is stored without business transformations.

```text
s3://dataflow-analytics/

└── bronze/
    ├── customers/
    ├── products/
    ├── orders/
    └── payments/
```

### 3. Transformation — Silver

Python and Pandas are used for cleaning and transformation.

Operations include:

- Data type conversion
- Null value treatment
- Duplicate removal
- Column standardization
- Date normalization
- Data validation
- Business rule application

```text
s3://dataflow-analytics/

└── silver/
    ├── customers/
    ├── products/
    ├── orders/
    └── payments/
```

### 4. Data Quality

Before loading the analytical layer, validation rules are applied.

Examples:

```text
customer_id  → NOT NULL
product_id   → NOT NULL
order_id     → UNIQUE
quantity     → > 0
unit_price   → >= 0
order_date   → VALID DATE
```

### 5. Data Warehouse — Gold

The analytical layer follows dimensional modeling principles.

```text
                 ┌───────────────┐
                 │  dim_customer │
                 └───────┬───────┘
                         │
                         ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│ dim_product │───▶│  fact_sales │◀───│   dim_date  │
└─────────────┘    └─────────────┘    └─────────────┘
                         ▲
                         │
                  ┌──────┴──────┐
                  │ dim_payment │
                  └─────────────┘
```

---

# ⚙️ Apache Airflow

Apache Airflow is planned as the orchestration layer for scheduling and monitoring the pipeline.

```text
START
  │
  ▼
Extract Data
  │
  ▼
Validate Raw Data
  │
  ▼
Transform Data
  │
  ▼
Load Data
  │
  ▼
Data Quality Checks
  │
  ▼
Update Analytical Layer
  │
  ▼
END
```

The implementation will cover:

- Scheduling
- Task dependencies
- Retry mechanisms
- Pipeline monitoring
- Execution logs
- Failure handling

---

# ☁️ AWS Data Lake

AWS S3 is used as the planned Data Lake storage layer.

```text
dataflow-analytics/
│
├── bronze/
├── silver/
└── gold/
```

AWS Glue is used for metadata management and cataloging.

AWS Athena is used for SQL-based analysis over data stored in S3.

---

# 🐘 PostgreSQL Data Warehouse

PostgreSQL is used as the planned analytical Data Warehouse.

The warehouse follows a dimensional modeling approach with fact and dimension tables.

### Fact

`fact_sales`

```text
sale_id
order_id
customer_id
product_id
date_id
payment_id
quantity
unit_price
discount
total_amount
```

### Dimensions

```text
dim_customer
dim_product
dim_date
dim_payment
dim_region
```

Example analytical query:

```sql
SELECT
    d.year,
    d.month,
    SUM(f.total_amount) AS revenue
FROM fact_sales f
JOIN dim_date d
    ON f.date_id = d.date_id
GROUP BY
    d.year,
    d.month
ORDER BY
    d.year,
    d.month;
```

---

# 📊 Power BI

The analytical layer is designed to support a Power BI dashboard containing:

- Total Revenue
- Total Orders
- Total Customers
- Average Order Value
- Revenue by Month
- Revenue by Region
- Revenue by Product
- Revenue by Category
- Customer Segmentation

Screenshots of the implemented dashboard will be stored in:

```text
docs/powerbi-dashboard.png
```

once the dashboard is actually built.

---

# 🐳 Docker

Docker and Docker Compose will be used to provide a reproducible local development environment.

Planned services:

```text
Docker Compose
│
├── Airflow
├── PostgreSQL
└── Python
```

---

# 📁 Project Structure

```text
dataflow-analytics-pipeline/
│
├── airflow/
│   └── dags/
│
├── src/
│   ├── ingestion/
│   ├── transformation/
│   └── quality/
│
├── sql/
│   ├── staging/
│   ├── warehouse/
│   └── analytics/
│
├── tests/
├── dashboard/
├── infrastructure/
├── data/
├── docs/
│
├── architecture.png
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

---

# 🧪 Data Engineering Practices

The project is designed around the following engineering practices:

- Modular Python code
- SQL organization
- Data validation
- Error handling
- Logging
- Pipeline orchestration
- Containerization
- Environment variables
- Automated testing
- Version control
- Layered data architecture

---

# 📈 Business Questions

The analytical layer is designed to answer questions such as:

- What is the total monthly revenue?
- Which products generate the highest revenue?
- Which regions have the highest sales volume?
- What is the average order value?
- Which customer segments generate the most revenue?
- How are sales evolving over time?
- Which product categories generate the highest revenue?

---

# 🎓 Skills Demonstrated

This project is intended to demonstrate practical knowledge of:

```text
Python
SQL
Pandas
ETL / ELT
PostgreSQL
Data Warehousing
Data Lake Architecture
Dimensional Modeling
Apache Airflow
Docker
AWS S3
AWS Glue
AWS Athena
Data Quality
Git
Power BI
```

---

# 👨‍💻 Author

**Victor Vanzella Ribeiro**

Data Engineering | Python | SQL | AWS

[LinkedIn](https://www.linkedin.com/in/victor-vanzella/)
