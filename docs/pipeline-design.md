# ShopSphere — Pipeline Design

## 1. Overview

ShopSphere is a hands-on Azure Data Engineering project built using Azure Data Factory (ADF) and Azure Data Lake Storage Gen2 (ADLS Gen2).

ADF orchestrates ingestion and transformation workflows. ADLS Gen2 stores raw source data, curated datasets and business-ready outputs.

## 2. Bronze Ingestion

**Purpose:** Ingest source data into the Bronze layer.

Source datasets:
- Customers
- Products
- Orders
- Payments

The Bronze-to-Silver pipelines copy the source data and orchestrate the subsequent processing workflows.

Storage path:

`shopsphere/bronze/`

## 3. Silver Transformations

**Purpose:** Clean and standardize the source datasets.

The Silver cleansing Mapping Data Flows process customers, products, orders and payments. The curated outputs are stored separately.

Storage path:

`shopsphere/silver/curated/`

Curated folders:
- `customers/`
- `products/`
- `orders/`
- `payments/`

## 4. Gold Transformations

**Purpose:** Produce datasets for business analysis.

### Customer Summary

Combines customer and order information to calculate:
- Total orders
- Total spend
- Average order value
- Last order date

Output: `shopsphere/gold/customer_summary/`

### Sales Summary

Combines order and product information to calculate:
- Total quantity
- Total sales
- Average selling price
- Total discount

Output: `shopsphere/gold/sales_summary/`

### Product Summary

Combines product and order information to calculate:
- Total quantity sold
- Total sales
- Total discount
- Average selling price

Output: `shopsphere/gold/product_summary/`

All three Gold pipelines were executed successfully and their outputs were verified in the original Azure environment.

## 5. Incremental Orders Processing

The incremental workflow uses a control file to identify the last processed order timestamp.

Control file:

`shopsphere/control/watermark.csv`

Workflow:
1. Read the watermark control data.
2. Identify the Orders watermark.
3. Pass the watermark into the parameterized Data Flow.
4. Filter orders with timestamps later than the watermark.
5. Process eligible records.
6. Calculate the latest processed timestamp.
7. Write the updated watermark to the control file.

The workflow successfully executed in a no-new-data scenario. A positive new-record test, including confirmation that the watermark advances correctly, remains pending.

## 6. Validation and Execution Status

### Completed and tested
- Bronze ingestion pipelines.
- Silver cleansing Data Flows and curated outputs.
- Gold Customer Summary pipeline and output.
- Gold Sales Summary pipeline and output.
- Gold Product Summary pipeline and output.
- Orders incremental workflow in a no-new-data scenario.
- Watermark update and copy workflow.

### Remaining
- Test incremental processing with a genuinely newer order.
- Verify all workflows after migration to the new Azure subscription.
- Perform final end-to-end regression testing.

## 7. Current Scope and Future Enhancements

The implemented solution focuses on Azure Data Factory and ADLS Gen2.

Potential future enhancements include:
- Azure Databricks and PySpark.
- Delta Lake.
- Automated data-quality checks and quarantine handling.
- Azure Event Hubs and streaming.
- Azure Synapse Analytics.
- Power BI dashboards.
- Monitoring, alerting and CI/CD.

These enhancements are planned and are not claimed as implemented in the current version.

## 8. Notes

This is a personal portfolio project. Azure resource names, linked-service credentials and environment-specific configuration may need to be updated when deploying to another subscription.
