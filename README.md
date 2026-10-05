# Inventory Accuracy & Stock Performance Analysis

Short project summary: analyse inventory levels, supplier performance, and replenishment patterns to identify stock risks and improve operational decisions.

## Project Stages

## PM-01 — Project Planning

Aim: assess how inventory, purchasing, and supplier factors affect stock availability and inventory stability.

Tools: Microsoft Excel, Git, GitHub.

Dataset: [original CSV](data/raw/supply_chain_dataset.csv); [Excel import](workbook/supply_chain_dataset_import.xlsx).

Project documents: [Proposal](docs/PERSONAL%20PROJECT%20PROPOSAL.md) | [Project management tracker](docs/PROJECT%20MANAGEMENT%20TRACKER.odt).

PM-01: Project Planning completed.
Next: PM-02 Dataset Preparation.

## PM-02 — Dataset Preparation
Preserved the original CSV and imported it into Excel format.

PM-02: Dataset Preparation completed.
Next: PM-03 Data Profiling.

## PM-03 — Data Profiling
The dataset has 91,250 records and 15 fields: 50 SKUs, 5 warehouses, 10 suppliers, and 4 regions. There are no blank fields, duplicate rows, duplicate date/SKU/warehouse keys, negative numeric values, or invalid flag values. It contains 365 daily records per SKU/warehouse combination.

**Data limitations:** 2024-12-31 is missing. `Stockout_Flag` is zero throughout, so it cannot support stockout-rate analysis. Physical count/adjustment records and actual order/delivery dates are absent, so inventory accuracy and on-time supplier performance cannot be directly measured.

PM-03: Data Profiling completed.
Next: PM-04 Data Cleaning.

## PM-04 — Data Cleaning
Created standardized processed CSV and Excel files. Checked all 91,250 records; no missing or invalid values required correction. Dates, numeric formats, and text fields were standardized, preserving the original raw dataset.

Cleaned files: [processed CSV](data/processed/supply_chain_dataset_cleaned.csv); [Excel workbook](workbook/supply_chain_dataset_cleaned.xlsx).

PM-04: Data Cleaning completed.
Next: PM-05 Data Validation.

## PM-05 — Data Validation
Validated the cleaned CSV and Excel workbook against the raw dataset. All 91,250 records and 15 fields match; no blanks, malformed values, duplicate rows, duplicate date/SKU/warehouse keys, invalid flags, negative values, or unit prices below unit costs were found. Each of the 250 SKU/warehouse pairs has 365 daily records, with 250 records per date.

The missing 2024-12-31 record and all-zero `Stockout_Flag` remain documented dataset limitations, not cleaning errors.

PM-05: Data Validation completed.
Next: PM-06 Formula Development.

## PM-06 — Formula Development
Created an Excel analysis workbook with formula-based measures for inventory value, sales value, forecast error, absolute forecast error, inventory-to-reorder-point gap, reorder status, and forecast coverage days. Added a formula guide with definitions and interpretation limits. The workbook is set to recalculate formulas when opened in Excel.

Workbook: [supply chain analysis](workbook/supply_chain_analysis.xlsx).

Forecast coverage assumes the forecast represents daily demand. Reorder status is an indicator only, not evidence of an actual stockout; inventory and sales values are estimates based on the dataset's unit cost and price.

PM-06: Formula Development completed.
Next: PM-07 Inventory Analysis.
