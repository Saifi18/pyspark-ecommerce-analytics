# Data Dictionary

## Customers

| Column           | Data Type | Description                | Business Rule                 |
| ---------------- | --------- | -------------------------- | ----------------------------- |
| customer_id      | STRING    | Unique customer identifier | Should be unique and non-null |
| first_name       | STRING    | Customer first name        | Should not be empty           |
| last_name        | STRING    | Customer last name         | Should not be empty           |
| email            | STRING    | Customer email             | Should be valid format        |
| country          | STRING    | Customer country           | Should be valid               |
| city             | STRING    | Customer city              | Should not be empty           |
| signup_date      | DATE      | Customer registration date | Should be valid               |
| customer_segment | STRING    | Customer business segment  | Valid segment required        |
| account_status   | STRING    | Customer account state     | Valid status required         |

## Products

| Column         | Data Type | Description               | Business Rule                 |
| -------------- | --------- | ------------------------- | ----------------------------- |
| product_id     | STRING    | Unique product identifier | Should be unique and non-null |
| product_name   | STRING    | Product name              | Should not be empty           |
| category       | STRING    | Product category          | Should be valid               |
| department     | STRING    | Product department        | Should be valid               |
| brand          | STRING    | Product brand             | Should not be empty           |
| unit_price     | DOUBLE    | Selling price per unit    | Should be >= 0                |
| cost_price     | DOUBLE    | Product cost              | Should be >= 0                |
| stock_quantity | INT       | Available inventory       | Should be >= 0                |
| product_status | STRING    | Product availability      | Valid status required         |

## Orders

| Column           | Data Type | Description             | Business Rule                 |
| ---------------- | --------- | ----------------------- | ----------------------------- |
| order_id         | STRING    | Unique order identifier | Should be unique and non-null |
| customer_id      | STRING    | Customer placing order  | Should reference customer     |
| order_date       | DATE      | Date order was placed   | Should be valid               |
| order_status     | STRING    | Current order status    | Valid status required         |
| shipping_country | STRING    | Shipping country        | Should be valid               |
| shipping_city    | STRING    | Shipping city           | Should not be empty           |
| payment_method   | STRING    | Payment method          | Valid method required         |
| sales_channel    | STRING    | Sales channel           | Valid channel required        |
| coupon_code      | STRING    | Applied coupon          | Can be null                   |
| order_total      | DOUBLE    | Total order value       | Should be >= 0                |

## Transactions

| Column             | Data Type | Description                   | Business Rule                 |
| ------------------ | --------- | ----------------------------- | ----------------------------- |
| transaction_id     | STRING    | Unique transaction identifier | Should be unique and non-null |
| order_id           | STRING    | Related order                 | Should reference order        |
| customer_id        | STRING    | Related customer              | Should reference customer     |
| product_id         | STRING    | Purchased product             | Should reference product      |
| transaction_date   | DATE      | Financial transaction date    | Should be valid               |
| quantity           | INT       | Units purchased               | Should be > 0                 |
| unit_price         | DOUBLE    | Price per unit                | Should be >= 0                |
| discount_amount    | DOUBLE    | Discount applied              | Should be >= 0                |
| tax_amount         | DOUBLE    | Tax applied                   | Should be >= 0                |
| transaction_amount | DOUBLE    | Final transaction amount      | Should be >= 0                |
| transaction_status | STRING    | Financial transaction status  | Valid status required         |
| payment_method     | STRING    | Transaction payment method    | Valid method required         |
