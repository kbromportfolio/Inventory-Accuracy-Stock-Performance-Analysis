# Inventory Accuracy & Stock Performance Analysis

**Project Status:** Completed

**Primary Tool:** Microsoft Excel

**Supporting Tools:** Git & GitHub

**Dataset:** Public supply-chain inventory 

**Analysis Type:** Inventory risk, replenishment and forecast performance analysis


This project evaluates inventory health, replenishment risk, and forecast performance using a daily supply chain dataset. The objective is to identify inventory risk signals, assess inventory coverage relative to demand, and provide a decision-support dashboard that highlights operational exceptions without overstating what the data can prove.

## Project Overview

The analysis focuses on how inventory levels, unit economics, and forecast performance interact across SKUs, warehouses, and time. It combines data profiling, cleaning, validation, Excel modelling, KPI development, PivotTable analysis, and dashboard reporting to produce a practical overview of inventory exposure and replenishment risk.

The project is designed to answer the following questions:

* Which SKU/warehouse combinations are approaching or falling below practical replenishment thresholds?
* How do sales, inventory, and forecast coverage vary over time and by warehouse?
* Which parts of the network show the strongest inventory risk or forecast deviation?
* What can be concluded from the dataset, and what remains unobservable due to missing operational data?

## Business Context

This analysis supports operational decision-making related to inventory management and stock performance. The underlying data includes daily records for demand, inventory, forecast, unit cost, unit price, supplier identifiers, and warehouse activity across a multi-SKU network.

The aim is not to claim actual stockouts or supplier-service performance where the source data does not include physical counts, actual order dates, or delivery-event logs. Instead, the project uses screening indicators to flag items requiring review and validation in the real operating environment.

## Dataset Summary

The project uses the dataset in [data/raw/supply_chain_dataset.csv](data/raw/supply_chain_dataset.csv), with a cleaned version in [data/processed/supply_chain_dataset_cleaned.csv](data/processed/supply_chain_dataset_cleaned.csv).

### Dataset Characteristics

* **91,250 records**
* **15 fields**
* **50 SKUs**
* **5 warehouses**
* **10 suppliers**
* **4 regions**
* **365 daily records across the 2024 reporting period for each SKU/warehouse combination represented in the dataset**
* **Reporting window:** 2024-01-01 to 2024-12-30

### Important Data Limitations

* 2024-12-31 is missing from the dataset.
* `Stockout_Flag` is zero for every record, so actual stockout rates cannot be measured.
* Physical inventory count and adjustment records are not available.
* Actual order and delivery dates are not present.
* Inventory accuracy and supplier-service performance therefore cannot be measured directly.

These limitations are documented throughout the workbook and analysis rather than treated as data errors.

## Repository Structure

```text
Inventory-Accuracy-Stock-Performance-Analysis/
│
├── data/
│   ├── raw/
│   │   └── supply_chain_dataset.csv
│   └── processed/
│       └── supply_chain_dataset_cleaned.csv
│
├── docs/
│   ├── PERSONAL PROJECT PROPOSAL.md
│   └── PROJECT MANAGEMENT TRACKER.odt
│
├── Reports/
│   ├── project_workflow.png
│   ├── executive_summary.png
│   ├── supply_chain_dashboard.png
│   ├── pivot_analysis.png
│   ├── monthly_sales_vs_forecast.png
│   ├── warehouse_sales.png
│   └── reorder_status_by_warehouse.png
│
└── workbook/
    ├── supply_chain_analysis.xlsx
    └── supply_chain_dataset_cleaned.xlsx
```

## Reports

* [Project workflow](Reports/project_workflow.png)
* [Executive summary](Reports/executive_summary.png)
* [Excel dashboard snapshot](Reports/supply_chain_dashboard.png)
* [Pivot analysis sheet](Reports/pivot_analysis.png)
* [Monthly units sold vs. forecast](Reports/monthly_sales_vs_forecast.png)
* [Units sold by warehouse](Reports/warehouse_sales.png)
* [Reorder status by warehouse](Reports/reorder_status_by_warehouse.png)

## Project Methodology

The project follows a structured workflow from planning through final review and documentation.

### PM-01 — Project Planning

Established the business problem, project goals, tools, scope, and documentation plan. The project was framed around inventory stability, purchasing, and replenishment risk.

### PM-02 — Dataset Preparation

Preserved the original source CSV and prepared the data for the Excel analysis workflow.

### PM-03 — Data Profiling

Profiled the data to confirm structure, completeness, record integrity, main dimensions, and known data limitations before cleaning and modelling.

### PM-04 — Data Cleaning

Standardised, validated, and stored cleaned files while preserving the original dataset.

### PM-05 — Data Validation

Confirmed that the cleaned data remained consistent with the raw source and documented known limitations and validation decisions.

### PM-06 — Formula Development

Created formula-based measures for:

* Inventory value
* Sales value
* Forecast error
* Absolute forecast error
* Inventory-to-reorder-point gap
* Reorder status
* Forecast coverage days

### PM-07 — Inventory Analysis

Added SKU-level, warehouse-level, stock-risk, and monthly trend views to review quantities, demand patterns, and operational exceptions across the network.

### PM-08 — PivotTable Analysis

Built native Excel PivotTables and charts to review performance by month and warehouse and to summarise reorder-status counts.

### PM-09 — KPI Development

Developed a KPI summary covering sales totals, inventory value, average inventory, forecast WAPE, and reorder-point screening rates.

### PM-10 — Dashboard Development

Created an interactive Excel dashboard with KPI cards, charts, and slicers to support scenario review and operational monitoring.

### PM-11 — Findings & Recommendations

Prepared an evidence-based watchlist of SKU/warehouse combinations requiring attention and documented practical operational recommendations.

### PM-12 — Documentation

Documented the project purpose, methodology, outputs, findings, limitations, interpretation guidance, and usage instructions.

### PM-13 — GitHub Publication

Organised the project repository for GitHub publication, including the data, documentation, analysis files, workbook outputs, and reporting assets in a clear, review-friendly structure.

**GitHub repository:** [kbromportfolio/Inventory-Accuracy-Stock-Performance-Analysis](https://github.com/kbromportfolio/Inventory-Accuracy-Stock-Performance-Analysis)

### PM-14 — Final Review

Completed the final validation check across the project documentation, dataset integrity, workbook outputs, and reporting assets to confirm the project is ready for stakeholder review and handoff.

The final review confirmed that the project is complete, internally consistent, and aligned with the stated business purpose and data limitations.

## Workbook Deliverables

The main analytical output is the [Excel analysis workbook](workbook/supply_chain_analysis.xlsx).

The workbook contains:

* Formula-driven calculations
* KPI summary sheets
* PivotTables and PivotCharts
* Interactive dashboard
* Findings and recommendations sheet

### How to Use the Workbook

1. Open the Excel analysis workbook.
2. Refresh PivotTables if the source data has changed.
3. Review the KPI summary for overall network health.
4. Use the dashboard slicers to segment by warehouse or month.
5. Review the findings sheet for the priority exception list and interpretation guidance.

## Key Results

The analysis produced the following headline figures for the covered reporting period:

* **Total units sold:** 1,829,979
* **Total inventory on latest date:** 114,019 units
* **Estimated inventory value on latest date:** $1,404,610.84
* **Forecast WAPE:** 11.9%
* **Reorder screening condition:** observed in 5.5% of records
* **Latest-date exception count:** 14 SKU/warehouse pairs at or below reorder point
* **Lead-time-demand exceptions:** 2 SKU/warehouse pairs below estimated lead-time demand

### Priority Watchlist Examples

* **SKU_44 at WH_3** — flagged by both reorder-point and lead-time-demand screening.
* **SKU_50 at WH_4** — below estimated lead-time demand.

These results are operational screening indicators, not confirmed stockouts or confirmed inventory discrepancies.

## Interpretation Guidance

The analysis is strongest for identifying areas that deserve operational follow-up rather than confirming stock unavailability.

Use the project outputs to:

* Prioritise review of exception pairs
* Examine forecast deviation by month and SKU
* Compare warehouse-level inventory-risk patterns
* Review inventory exposure against replenishment thresholds
* Validate inventory valuation and physical counts before formal conclusions

Do not treat the project as a definitive record of stockout incidence, supplier performance, or inventory accuracy without supplementary transactional and physical-count data.

## Limitations and Caveats

The source dataset supports inventory and replenishment screening, but not complete operational audit measurement.

Key caveats:

* No actual stockout events are present in the data.
* No physical inventory adjustment or count records are available.
* No actual order or delivery date records are available.
* No direct supplier-service KPI can be calculated with confidence.
* Inventory accuracy cannot be measured directly from the available fields.
* Findings should be validated against operational records before intervention or formal business claims.

## Final Status

**Completed**

This project is complete in terms of planning, data preparation, profiling, validation, analysis, dashboard development, documentation, GitHub publication, and final review.

The workbook and supporting files are ready for review and use as a decision-support tool for inventory risk screening.

The final conclusion is deliberately evidence-based: the project demonstrates a structured, data-supported screening process for inventory risk and replenishment pressure, while explicitly recognising that confirmed stockouts, supplier performance, and inventory accuracy require additional operational data.
