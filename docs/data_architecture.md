# Data Architecture

## 1. Architecture Overview

The pipeline follows a layered data architecture:

Raw Sources
↓
Bronze
↓
Silver
↓
Gold
↓
Analytics

## 2. Source Layer

The project receives data from four simulated operational systems:

- Customer system
- Product catalog
- Order management system
- Payment/transaction system

Source formats:

- customers.csv
- products.json
- orders.csv
- transactions.csv

The product JSON file will use JSON Lines (NDJSON), allowing
row-oriented ingestion with Spark.

## 3. Bronze Layer

Bronze contains raw ingested data with minimal transformation.

Responsibilities:

- Read source files
- Apply compatible schemas
- Preserve source information
- Add ingestion metadata where appropriate
- Store data in a Spark-friendly format
- Enable replay and reprocessing

Bronze should not perform business-level cleaning.

## 4. Silver Layer

Silver contains cleaned and validated data.

Responsibilities:

- Standardize columns
- Handle null values
- Remove or identify duplicates
- Validate data types
- Validate business rules
- Identify invalid records
- Identify orphan records
- Standardize status values
- Prepare trusted datasets for analytics

## 5. Gold Layer

Gold contains business-ready analytical datasets.

### Customer Analytics

Grain:

One row per customer.

### Product Analytics

Grain:

One row per product.

### Sales Analytics

Grain:

One row per transaction date and country.

### Customer Transaction Analytics

Grain:

One row per transaction.

## 6. Entity Relationships

Customer
|
| 1:N
↓
Order
|
| 1:N
↓
Transaction
|
| N:1
↓
Product

## 7. Data Flow

customers.csv
↓
Bronze
↓
Silver
↓
Customer Analytics
↓
Gold

products.json
↓
Bronze
↓
Silver
↓
Product Analytics
↓
Gold

orders.csv
↓
Bronze
↓
Silver
↓
Gold

transactions.csv
↓
Bronze
↓
Silver
↓
Customer / Product / Sales / Transaction Analytics

## 8. Technology Stack

- Python
- PySpark
- Apache Spark
- Parquet
- JSON
- CSV
- Google Colab
- Git
- GitHub

## 9. Design Principles

### Preserve Raw Data

Raw data should remain available for replay and debugging.

### Define Dataset Grain

Every Silver and Gold dataset must have an explicitly documented grain.

### Separate Transformation Layers

Cleaning and validation belong primarily in Silver.

Business aggregations belong in Gold.

### Avoid Premature Optimization

Correctness comes before performance optimization.

Performance improvements will be supported by Spark execution-plan analysis.

### Reproducibility

The project should be reproducible from the repository without
depending on undocumented manual steps.

## 10. Future Enhancements

Potential future enhancements include:

- Automated data-quality tests
- Pipeline logging
- Incremental processing
- Job orchestration
- CI/CD
- Delta Lake
- Databricks deployment
- Dashboard integration
