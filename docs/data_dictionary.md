# ShopSphere — Sample Data Dictionary

## 1. Overview

This document describes the structure of the synthetic sample CSV files included in the ShopSphere repository.

These small datasets are intended for portfolio demonstrations, schema understanding and basic testing. They are not copies of the original Azure source data.

**Data location:** `data/`

## 2. Customers — `data/customers/customers.csv`

| Column | Data Type | Description |
|---|---|---|
| customer_id | String | Unique customer identifier |
| first_name | String | Customer's first name |
| last_name | String | Customer's last name |
| email | String | Synthetic example email address |
| city | String | Customer's city |
| state | String | Customer's state |
| signup_date | Date | Customer registration date |
| customer_segment | String | Customer classification |

## 3. Orders — `data/orders/orders.csv`

| Column | Data Type | Description |
|---|---|---|
| order_id | String | Unique order identifier |
| customer_id | String | Identifier of the customer who placed the order |
| product_id | String | Identifier of the purchased product |
| order_timestamp | Timestamp | Date and time when the order was placed |
| quantity | Integer | Number of units purchased |
| unit_price | Decimal | Selling price per unit |
| discount_amount | Decimal | Discount applied |
| total_amount | Decimal | Final order amount after discount |
| order_status | String | Current order status |

## 4. Products — `data/products/products.csv`

| Column | Data Type | Description |
|---|---|---|
| product_id | String | Unique product identifier |
| product_name | String | Name of the product |
| category | String | Product category |
| subcategory | String | Product subcategory |
| brand | String | Product brand |
| unit_price | Decimal | Selling price |
| cost_price | Decimal | Cost price |
| created_date | Date | Date the product was added |

## 5. Payments — `data/payments/payments.csv`

| Column | Data Type | Description |
|---|---|---|
| payment_id | String | Unique payment identifier |
| order_id | String | Associated order identifier |
| payment_timestamp | Timestamp | Date and time of the payment |
| payment_method | String | Payment method used |
| amount | Decimal | Payment amount |
| payment_status | String | Current payment status |

## 6. Relationships

- `customers.customer_id` relates to `orders.customer_id`.
- `products.product_id` relates to `orders.product_id`.
- `orders.order_id` relates to `payments.order_id`.

These relationships can be used for joins and aggregations in data transformation exercises.

## 7. Data Notes

- All sample records are synthetic and created for demonstration.
- The datasets contain only a subset of the columns described in the main `data_dictionary.md`.
- Column names and data types should be checked against the actual source datasets before using these samples to reproduce the complete Azure pipelines.
- Timestamps use ISO-style date and time values.
- Monetary fields are represented as numeric values in the CSV files; currency is not explicitly specified in these samples.

## 8. Intended Use

These sample datasets support:

- Understanding source schemas.
- Demonstrating relationships between datasets.
- Testing basic joins and aggregations.
- Explaining the ShopSphere data model to reviewers and recruiters.
