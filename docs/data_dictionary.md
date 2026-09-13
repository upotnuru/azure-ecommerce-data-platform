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

| Column | Data Type | Description |
|---|---|---|
| order_id | String | Unique order identifier |
| customer_id | String | Identifier of the customer who placed the order |
| product_id | String | Identifier of the purchased product |
| order_timestamp | Timestamp | Date and time when the order was placed |
| quantity | Integer | Number of units purchased |
| unit_price | Decimal | Selling price per unit at the time of purchase |
| discount_amount | Decimal | Discount applied to the order |
| total_amount | Decimal | Final order amount after discount |
| payment_method | String | Payment method used for the order |
| order_status | String | Current status of the order |
| shipping_city | String | Delivery city |
| shipping_state | String | Delivery state |

## Payments

| Column | Data Type | Description |
|---|---|---|
| payment_id | String | Unique payment transaction identifier |
| order_id | String | Identifier of the associated order |
| customer_id | String | Identifier of the customer making the payment |
| payment_timestamp | Timestamp | Date and time when the payment was processed |
| payment_method | String | Payment method used |
| amount | Decimal | Payment amount |
| currency | String | Currency used for the transaction |
| payment_status | String | Current payment status |
| transaction_reference | String | External payment transaction reference |
| failure_reason | String | Reason for payment failure, if applicable |
