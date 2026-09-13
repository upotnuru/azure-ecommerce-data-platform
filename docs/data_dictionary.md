# ShopSphere Data Dictionary

This document defines the structure and meaning of the datasets used in the ShopSphere data platform.

## Customers

| Column | Data Type | Description |
|---|---|---|
| customer_id | String | Unique customer identifier |
| first_name | String | Customer first name |
| last_name | String | Customer last name |
| email | String | Customer email address |
| phone | String | Customer phone number |
| city | String | Customer city |
| state | String | Customer state |
| country | String | Customer country |
| signup_date | Date | Customer registration date |
| customer_segment | String | Customer classification |

## Products

| Column | Data Type | Description |
|---|---|---|
| product_id | String | Unique product identifier |
| product_name | String | Name of the product |
| category | String | Product category |
| subcategory | String | Product subcategory |
| brand | String | Product brand |
| price | Decimal | Selling price of the product |
| cost | Decimal | Cost of the product |
| stock_quantity | Integer | Available inventory quantity |
| supplier | String | Product supplier |
| product_status | String | Current product status |
| created_date | Date | Date the product was added |

## Orders

To be defined.

## Payments

To be defined.
