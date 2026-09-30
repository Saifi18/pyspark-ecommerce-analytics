# Business Requirements

## 1. Project Overview

The e-commerce platform needs a reliable analytics data pipeline that
integrates customer, product, order, and transaction data.

The pipeline will ingest raw CSV and JSON data, validate and clean the
data, and produce analytics-ready datasets for customer, product, and
sales analysis.

## 2. Business Problem

The source systems contain data from multiple operational domains.
The analytics team needs trusted datasets to answer questions such as:

- Which customers generate the most revenue?
- How frequently do customers purchase?
- Which products generate the most revenue?
- Which products generate the highest profit?
- How is revenue changing over time?
- What is the running and rolling revenue?
- Which customers are becoming less active?
- Are there data-quality problems affecting analytics?

## 3. Business Objectives

- Build a reliable PySpark data pipeline.
- Integrate customer, product, order, and transaction data.
- Detect and handle data-quality issues.
- Produce trusted Silver datasets.
- Produce analytics-ready Gold datasets.
- Apply aggregations, joins, and window functions.
- Analyze Spark execution plans.
- Apply appropriate performance optimizations.
- Maintain a reproducible and documented GitHub project.

## 4. Source Systems

| Source       | Format     | Grain                   |
| ------------ | ---------- | ----------------------- |
| Customers    | CSV        | One row per customer    |
| Products     | JSON Lines | One row per product     |
| Orders       | CSV        | One row per order       |
| Transactions | CSV        | One row per transaction |

## 5. Core Business Entities

### Customer

One row represents one customer.

### Product

One row represents one product.

### Order

One row represents one customer order.

### Transaction

One row represents one financial transaction.

## 6. Key Business Relationships

Customer 1:N Order

Order 1:N Transaction

Product 1:N Transaction

Customer 1:N Transaction

## 7. Key Metrics

### Customer Metrics

- Total orders
- Completed orders
- Total transactions
- Total spend
- Average order value
- Average transaction value
- First purchase date
- Latest purchase date
- Days since last purchase
- Running customer spend
- Customer revenue rank

### Product Metrics

- Total units sold
- Total revenue
- Total discount
- Total tax
- Estimated cost
- Gross profit
- Profit margin
- Product rank within department

### Sales Metrics

- Daily transaction count
- Daily units sold
- Gross revenue
- Discount
- Tax
- Net revenue
- Previous-day revenue
- Revenue change
- Revenue growth percentage
- Running revenue
- Rolling revenue

## 8. Data Quality Requirements

The pipeline should identify:

- Null identifiers
- Duplicate business keys
- Invalid numeric values
- Invalid dates
- Negative quantities
- Invalid monetary amounts
- Invalid status values
- Orphan customer references
- Orphan product references
- Orphan order references
- Invalid records

## 9. Expected Data Layers

### Bronze

Raw/minimally transformed source data.

### Silver

Cleaned, validated, standardized and trusted data.

### Gold

Business-ready analytical datasets.

## 10. Expected Gold Datasets

- Customer Analytics
- Product Analytics
- Sales Analytics
- Customer Transaction Analytics

## 11. Success Criteria

The project is successful when:

- All four source datasets can be ingested.
- Data-quality issues can be identified.
- Clean Silver datasets are produced.
- Gold datasets have clearly defined grain.
- Business metrics are reproducible.
- Spark execution plans can be explained.
- Performance bottlenecks can be identified and addressed.
- The project can be reproduced from the GitHub repository.
