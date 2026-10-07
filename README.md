# Inventory Accuracy & Stock Performance Analysis

This project evaluates inventory health, replenishment risk, and forecast performance using a daily supply chain dataset. The objective is to identify stock risk signals, assess inventory coverage relative to demand, and provide a decision-support dashboard that highlights operational exceptions without overstating what the data can prove.

## Project overview

The analysis focuses on how inventory levels, unit economics, and forecast performance interact across SKUs, warehouses, and time. It combines data profiling, cleaning, validation, Excel modeling, KPI development, PivotTable analysis, and dashboard reporting to produce a practical overview of stock exposure and replenishment risk.

The project is designed to answer the following questions:

- Which SKU/warehouse combinations are approaching or falling below practical replenishment thresholds?
- How do sales, inventory, and forecast coverage vary over time and by warehouse?
- Which parts of the network show the strongest inventory risk or forecast deviation?
- What can be concluded from the dataset, and what remains unobservable due to missing operational data?

## Business context

This analysis supports operational decision-making related to inventory management and stock performance. The underlying data includes daily records for demand, stock, forecast, unit cost, unit price, supplier identifiers, and warehouse activity across a multi-SKU network.

The aim is not to claim actual stockouts or supplier-service performance where the source data does not include physical counts, actual order dates, or delivery-event logs. Instead, the project uses screening indicators to flag items requiring review and validation in the real operating environment.

## Dataset summary

The project uses the dataset in [data/raw/supply_chain_dataset.csv](data/raw/supply_chain_dataset.csv), with a cleaned version in [data/processed/supply_chain_dataset_cleaned.csv](data/processed/supply_chain_dataset_cleaned.csv).

Dataset characteristics:

- 91,250 records
- 15 fields
- 50 SKUs
- 5 warehouses
- 10 suppliers
- 4 regions
- 365 daily records per SKU/warehouse pair
- Reporting window: 2024-01-01 to 2024-12-30

Important data limitations:

- 2024-12-31 is missing from the dataset.
- `Stockout_Flag` is zero for every record, so actual stockout rates cannot be measured.
- Physical count and adjustment records are not available.
- Actual order and delivery dates are not present.
- Because of these limitations, inventory accuracy and supplier service performance cannot be measured directly.

These limitations are documented throughout the workbook and analysis rather than treated as data errors.

## Repository structure

- **Data:** original source CSV (data/raw/supply_chain_dataset.csv) and cleaned CSV (data/processed/supply_chain_dataset_cleaned.csv)

- **Documentation:** project proposal (docs/PERSONAL PROJECT PROPOSAL.md) and project tracker (docs/PROJECT MANAGEMENT TRACKER.odt)

- **Reports:** Reports (Reports/) contains exported PNGs, listed below

- **Workbooks:** analysis workbook (workbook/supply_chain_analysis.xlsx) and cleaned-data workbook (workbook/supply_chain_dataset_cleaned.xlsx)

Report images:

- Executive summary (Reports/executive_summary.png)
- Excel dashboard snapshot (Reports/supply_chain_dashboard.png)
- Pivot analysis sheet (Reports/pivot_analysis.png)
- Monthly units sold vs. forecast (Reports/monthly_sales_vs_forecast.png)
- Units sold by warehouse(Reports/warehouse_sales.png)
- Reorder status by warehouse (Reports/reorder_status_by_warehouse.png)

## Project methodology

The project follows a structured workflow from planning through final documentation:

### PM-01 — Project Planning
Established the business problem, project goals, tools, and documentation plan. The project was framed around inventory stability, purchasing, and replenishment risk.

### PM-02 — Dataset Preparation
Preserved the original source CSV and prepared the data for the Excel analysis workflow.

### PM-03 — Data Profiling
Profiled the data to confirm structure, completeness, and record integrity. Verified the main dimensions and data limitations before cleaning and modeling.

### PM-04 — Data Cleaning
Standardized, validated, and stored cleaned files while preserving the original dataset.

### PM-05 — Data Validation
Confirmed that the cleaned data matched the raw source with no material integrity issues, while documenting the known limitations.

### PM-06 — Formula Development
Created formula-based measures for:

- inventory value
- sales value
- forecast error
- absolute forecast error
- inventory-to-reorder-point gap
- reorder status
- forecast coverage days

### PM-07 — Inventory Analysis
Added SKU-level, warehouse-level, stock-risk, and monthly trend views to review quantities and exceptions across the network.

### PM-08 — PivotTable Analysis
Built native Excel PivotTables and charts to review performance by month and warehouse, and to summarize reorder-status counts.

### PM-09 — KPI Development
Developed a KPI summary that includes sales totals, inventory value, average inventory, forecast WAPE, and reorder-point screening rates.

### PM-10 — Dashboard Development
Created an interactive Excel dashboard with KPI cards, charts, and slicers to support scenario review and operational monitoring.

### PM-11 — Findings & Recommendations
Prepared an evidence-based watchlist of at-risk SKU/warehouse combinations and documented operational recommendations.

### PM-12 — Documentation & Final Review
This README completes the final documentation pass, summarizing the project purpose, outputs, analysis findings, limitations, and usage guidance.

## Workbook deliverables

The main analytical output is the Excel workbook at [workbook/supply_chain_analysis.xlsx](workbook/supply_chain_analysis.xlsx).

The workbook contains:

- formula-driven calculations
- KPI summary sheets
- PivotTables and PivotCharts
- interactive dashboard
- findings and recommendations sheet

To use the workbook effectively:

1. Open the Excel file.
2. Refresh PivotTables if the source data has changed.
3. Review the KPI summary for overall network health.
4. Use the dashboard slicers to segment by warehouse or month.
5. Check the findings sheet for the priority exception list and interpretation guidance.

## Key results

The analysis produced the following headline figures for the covered reporting period:

- Total units sold: 1,829,979
- Total inventory on latest date: 114,019 units
- Estimated inventory value on latest date: $1,404,610.84
- Forecast WAPE: 11.9%
- Reorder screening condition observed in 5.5% of daily records
- Latest-date exception count: 14 SKU/warehouse pairs at or below reorder point; 2 below estimated lead-time demand

Priority watchlist examples:

- SKU_44 at WH_3 — flagged by both reorder-point and lead-time-demand screening
- SKU_50 at WH_4 — below estimated lead-time demand

These results are operational screening indicators, not confirmed stockouts or confirmed inventory discrepancies.

## Interpretation guidance

The analysis is strongest for identifying areas that deserve operational follow-up rather than confirming stock unavailability.

Use the project outputs to:

- prioritize review of exception pairs
- examine forecast deviation by month and SKU
- compare warehouse-level stock risk patterns
- validate inventory valuation and physical counts before formal conclusions

Do not treat the project as a definitive record of stockout incidence, supplier performance, or inventory accuracy without supplementary transactional and physical-count data.

## Limitations and caveats

The source dataset supports inventory and replenishment screening, but not complete operational audit measurement.

Key caveats:

- no actual stockout events are present in the data
- no physical inventory adjustment or count records are available
- no actual order or delivery date records are available
- no direct supplier service KPI can be calculated with confidence
- findings should be validated with operational records before intervention or formal claims

## Final status

This project is complete in terms of planning, data preparation, validation, analysis, dashboarding, and documentation. The workbook and supporting files are ready to review and use as a decision-support tool for inventory risk screening.

The final conclusion is best framed as follows: the project demonstrates a structured, data-supported screening process for inventory risk and replenishment pressure, while explicitly recognizing that confirmed stockouts, supplier performance, and inventory accuracy require additional operational data.
