# ShopSphere — Azure Data Engineering Platform

An end-to-end, hands-on Azure data engineering project for ingesting, cleansing, transforming and preparing e-commerce data for analytics using Azure Data Factory and Azure Data Lake Storage Gen2.

## Project Overview

**ShopSphere** demonstrates a medallion-style data pipeline architecture for four e-commerce data domains: customers, products, orders and payments.

The implemented solution uses Azure Data Factory (ADF) to orchestrate ingestion and transformation workflows, while Azure Data Lake Storage Gen2 (ADLS Gen2) stores raw, curated and business-ready datasets.

The project includes Bronze, Silver and Gold layers, business summary transformations, and a watermark-based incremental processing workflow for orders.

> **Project type:** Personal portfolio project  
> **Current scope:** Azure Data Factory + ADLS Gen2  
> **Status:** Core batch processing implemented; incremental validation and migration verification remain.

---

## Business Problem

E-commerce platforms generate data across customers, products, orders and payments. Before this data can support meaningful analysis, it must be ingested, cleaned, standardized and transformed into reliable datasets.

ShopSphere demonstrates how to organize these workflows into reusable data pipelines and produce business-ready outputs for customer and product performance analysis.

## Architecture

![ShopSphere Implemented Architecture](architecture/shopsphere-implemented-architecture.png)

The implemented architecture uses Azure Data Factory for orchestration and Mapping Data Flows for transformations, with ADLS Gen2 providing the storage layers.

## Technology Stack

| Technology | Purpose |
|---|---|
| Azure Data Factory | Pipeline orchestration and data transformation |
| Azure Data Lake Storage Gen2 | Data lake storage |
| ADF Mapping Data Flows | Cleansing, joins, aggregations and transformations |
| CSV | Source and output data format |
| Git and GitHub | Source control and project documentation |

---

## Data Domains

- **Customers:** Customer profile and registration information.
- **Products:** Product details, categories, brands and pricing.
- **Orders:** Order transactions, quantities, prices and discounts.
- **Payments:** Payment transaction information and status.

## Medallion Architecture

### 1. Bronze — Raw Data

Stores source CSV data for customers, products, orders and payments in ADLS Gen2.

```text
shopsphere/bronze/
├── customers/
├── products/
├── orders/
└── payments/
```

### 2. Silver — Curated Data

ADF Mapping Data Flows cleanse and standardize the four source domains and write curated datasets.

```text
shopsphere/silver/curated/
├── customers/
├── products/
├── orders/
└── payments/
```

### 3. Gold — Business-Ready Data

Gold transformations combine curated datasets and calculate business metrics.

| Output | Example metrics |
|---|---|
| Customer Summary | Total orders, total spend, average order value, last order date |
| Sales Summary | Total quantity, total sales, average selling price, total discount |
| Product Summary | Quantity sold, total sales, discounts and average selling price |

Output paths:

```text
shopsphere/gold/
├── customer_summary/
├── sales_summary/
└── product_summary/
```

These outputs have been generated and verified in the original Azure environment.

---

## Incremental Orders Processing

ShopSphere includes a watermark-based incremental processing workflow for orders.

The workflow uses a control file to store the last processed timestamp and passes that value into a parameterized Data Flow.

```text
Read watermark
      ↓
Identify the orders watermark
      ↓
Filter orders newer than the watermark
      ↓
Process eligible records
      ↓
Calculate the latest processed timestamp
      ↓
Update the watermark control file
```

Control file:

```text
shopsphere/control/watermark.csv
```

The workflow has successfully executed in a no-new-data scenario. A positive end-to-end test with a new record, including confirmation that the watermark advances correctly, remains to be completed.

---

## Validation and Testing

The following work has been completed in the original Azure environment:

- Validated the Bronze-to-Silver ingestion pipelines.
- Validated the Silver cleansing Data Flows.
- Executed the Gold Customer Summary pipeline and verified its output.
- Executed the Gold Sales Summary pipeline and verified its output.
- Executed the Gold Product Summary pipeline and verified its output.
- Executed the Orders incremental workflow in a no-new-data scenario.
- Tested the watermark update and copy workflow.

Final migration and end-to-end regression testing will be performed after deployment to the new Azure subscription.

## Repository Structure

The repository is intended to contain the following project assets. Folder contents should reflect the files actually committed.

```text
azure-ecommerce-data-platform/
├── README.md
├── architecture/
│   └── shopsphere-implemented-architecture.png
├── data/
│   ├── customers/
│   ├── products/
│   ├── orders/
│   └── payments/
└── docs/
    ├── pipeline-design.md
    ├── data-dictionary.md
    └── testing-and-validation.md
```

Azure Data Factory ARM exports and pipeline definitions can also be added after reviewing them for secrets and environment-specific configuration. Do not commit passwords, access keys, SAS tokens or other credentials.

## Current Project Status

### Completed

- Azure Data Lake Storage Gen2 setup.
- Azure Data Factory setup and orchestration.
- Bronze ingestion for customers, products, orders and payments.
- Silver cleansing and curated outputs for all four domains.
- Gold Customer Summary Data Flow and pipeline.
- Gold Sales Summary Data Flow and pipeline.
- Gold Product Summary Data Flow and pipeline.
- Successful execution and output verification for the three Gold pipelines.
- Orders watermark-based incremental workflow implementation.
- Implemented architecture diagram and project documentation updates.

### Remaining

- Complete a positive new-record test for incremental Orders processing.
- Verify the project after migration to the new Azure subscription.
- Review the GitHub repository and finalize supporting documentation.
- Perform final end-to-end regression testing.

## Future Enhancements

These are planned extensions, not part of the currently verified implementation:

- Azure Databricks and PySpark transformations.
- Delta Lake storage and transaction handling.
- Automated data-quality framework and quarantine handling.
- Azure Event Hubs and real-time streaming.
- Azure Synapse Analytics.
- Power BI dashboards.
- Enhanced monitoring, alerting and recovery.
- CI/CD and automated deployment.
- Expanded automated testing.

## Learning Outcomes

This project provides hands-on practice with:

- Azure Data Factory pipeline orchestration.
- ADLS Gen2 folder and dataset organization.
- Mapping Data Flow transformations, joins and aggregations.
- Medallion-style data lake design.
- Watermark-based incremental processing.
- Pipeline validation, execution troubleshooting and GitHub documentation.

## Disclaimer

ShopSphere is a personal learning and portfolio project. It is not presented as a production deployment. Reproducing it may require creating Azure resources, configuring linked services and credentials, and updating environment-specific settings.
