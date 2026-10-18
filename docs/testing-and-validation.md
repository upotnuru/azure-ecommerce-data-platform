# ShopSphere — Testing and Validation

## 1. Purpose

This document records the testing completed for the ShopSphere Azure Data Engineering project and identifies the remaining validation work.

## 2. Bronze and Silver

| Test | Status | Notes |
|---|---|---|
| Bronze ingestion for customers | Passed in original environment | Pipeline execution verified |
| Bronze ingestion for products | Passed in original environment | Pipeline execution verified |
| Bronze ingestion for orders | Passed in original environment | Pipeline execution verified |
| Bronze ingestion for payments | Passed in original environment | Pipeline execution verified |
| Silver cleansing for customers | Passed in original environment | Curated output verified |
| Silver cleansing for products | Passed in original environment | Curated output verified |
| Silver cleansing for orders | Passed in original environment | Curated output verified |
| Silver cleansing for payments | Passed in original environment | Curated output verified |

## 3. Gold Layer

| Test | Status | Notes |
|---|---|---|
| Gold Customer Summary | Passed in original environment | Pipeline succeeded and output verified |
| Gold Sales Summary | Passed in original environment | Pipeline succeeded and output verified |
| Gold Product Summary | Passed in original environment | Pipeline succeeded and output verified |

## 4. Incremental Orders Processing

| Test | Status | Notes |
|---|---|---|
| Watermark lookup | Passed | Control data was retrieved |
| Incremental filter | Passed in no-new-data scenario | Pipeline execution succeeded |
| Watermark update workflow | Executed successfully | No-new-data behavior observed |
| New record processing | Pending | Test with a genuinely newer order is required |
| Watermark advancement | Pending | Verify the watermark advances after processing a new record |

## 5. GitHub Repository Checks

- README documents the implemented architecture and project scope.
- Implemented architecture diagram is included.
- Synthetic sample CSV files are provided.
- Data dictionary and pipeline design documentation are included.

## 6. Remaining Validation

1. Deploy the project to the new Azure subscription.
2. Reconfigure linked services and environment-specific parameters.
3. Run the ingestion, Silver and Gold pipelines.
4. Verify output datasets.
5. Test incremental processing with a new order.
6. Confirm the watermark advances correctly.
7. Record final results and screenshots.

## 7. Testing Notes

The statuses above reflect previously observed runs in the original Azure environment. They do not imply that the project has already been redeployed and retested in the new subscription.

This document should be updated as additional tests are completed.
