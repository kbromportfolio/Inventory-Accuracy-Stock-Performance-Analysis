# Inventory Accuracy & Stock Performance Analysis

Short project summary: analyse inventory levels, supplier performance, and replenishment patterns to identify stock risks and improve operational decisions.

## Project Stages

## PM-01 — Project Planning

Aim: assess how inventory, purchasing, and supplier factors affect stock availability and inventory stability.

Tools: Microsoft Excel, Git, GitHub.

Dataset: [original CSV](data/raw/supply_chain_dataset.csv); [Excel import](workbook/supply_chain_dataset_import.xlsx).

Project documents: [Proposal](docs/PERSONAL PROPOSAL.md) | [Project management tracker](docs/PROJECT MANAGEMENT TRACKER.odt).

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

## PM-07 — Inventory Analysis
Added SKU, warehouse, stock-risk, and monthly-trend analyses to the Excel workbook. The summaries cover 50 SKUs, 5 warehouses, 250 SKU/warehouse pairs, and 12 months. The latest available inventory snapshot is 2024-12-30.

The latest stock-risk screen flags 14 SKU/warehouse pairs at or below their reorder point and 2 below estimated lead-time demand (one pair meets both conditions; 15 pairs meet at least one threshold). These are screening indicators, not confirmed stockouts. Inventory averages use daily snapshots; sales and demand are treated as daily activity.

Workbook: [supply chain analysis](workbook/supply_chain_analysis.xlsx).

PM-07: Inventory Analysis completed.

## PM-08 — PivotTable Analysis
Added a formula-based `Month` grouping key to the `Calculations` table and created five native Excel PivotTables: monthly units sold versus forecast, warehouse sales, average daily inventory by warehouse, daily reorder-status counts by warehouse, and SKU sales with average daily inventory.

Added three native PivotCharts: a monthly sales-versus-forecast line chart, a warehouse sales column chart, and a 100% stacked reorder-status chart. The pivots summarize daily records; reorder-status counts are screening indicators, not confirmed stockouts. `Stockout_Flag` remains zero throughout the source data.

Workbook: [supply chain analysis](workbook/supply_chain_analysis.xlsx). Refresh PivotTables after changing the source data.

PM-08: PivotTable Analysis completed.
Next: PM-09 KPI Development.

## PM-09 — KPI Development
Added a formula-driven KPI summary to the Excel workbook, covering SKU and warehouse counts, total and average daily sales, average inventory per daily SKU/warehouse record, latest-date inventory and estimated value, reorder-point screening rates, latest SKU/warehouse risk counts, and overall forecast WAPE.

Validated the measures against the source records and existing summaries. The reporting period is 2024-01-01 to 2024-12-30: 1,829,979 units sold across 50 SKUs and 5 warehouses; latest inventory totals 114,019 units, with an estimated value of $1,404,610.84. Overall forecast WAPE is 11.9%. The at/below-reorder screening condition occurs in 5.5% of daily records; on the latest date, 14 of 250 SKU/warehouse pairs are at or below reorder and 2 are below estimated lead-time demand, with one pair meeting both conditions.

`Stockout_Flag` is zero throughout the dataset, so an actual stockout rate is unavailable. Reorder and lead-time-demand measures are screening indicators, not confirmed stockouts.

Workbook: [supply chain analysis](workbook/supply_chain_analysis.xlsx).

PM-09: KPI Development completed.
Next: PM-10 Dashboard Development.

## PM-10 — Dashboard
Created an interactive Excel dashboard with five full-period KPI cards, three PivotCharts, and Warehouse and Month slicers. Both slicers are connected to all five PivotTables, so their selections filter the dashboard charts. KPI cards remain full-period summaries and do not change with slicer selections.

The dashboard links to the validated KPI analysis and PivotTables. Reorder measures remain screening indicators; the dataset does not support a confirmed stockout rate.

Workbook: [supply chain analysis](workbook/supply_chain_analysis.xlsx).

PM-10: Dashboard completed.
Next: PM-11 Findings and Recommendations.

## PM-11 — Findings & Recommendations
Added a findings and recommendations sheet to the Excel workbook, documenting the late-summer/fall increase in monthly forecast WAPE, latest-date SKU/warehouse reorder and lead-time-demand screening exceptions, similar warehouse-level summary results, the estimated latest inventory value, and the dataset limits affecting stockout and supplier-service analysis.

The sheet includes the full 15-pair latest-date screening watchlist and prioritizes verification of SKU_44 at WH_3 (both screening thresholds) and SKU_50 at WH_4 (below estimated lead-time demand). Recommendations call for checking physical stock and inbound orders before intervention, reviewing forecast errors by SKU and month, validating inventory valuation, and obtaining count and delivery-event data before claiming inventory accuracy or supplier performance.

These thresholds are screening indicators, not confirmed stockouts; the dataset does not establish that any flagged item was unavailable.

Workbook: [supply chain analysis](workbook/supply_chain_analysis.xlsx).

PM-11: Findings & Recommendations completed.
Next: PM-12 Documentation and Final Review.
