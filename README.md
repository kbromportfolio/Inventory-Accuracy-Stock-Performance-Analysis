# Inventory Accuracy & Stock Performance Analysis

Short project summary: analyse inventory levels, supplier performance, and replenishment patterns to identify stock risks and improve operational decisions.

## Project Stages

## PM-01 — Project Planning

Aim: assess how inventory, purchasing, and supplier factors affect stock availability and inventory stability.

Tools: Microsoft Excel, Git, GitHub.

Dataset: [original CSV](data/raw/supply_chain_dataset.csv); [Excel import](workbook/supply_chain_dataset_import.xlsx).

Project documents are in the `docs/` folder.

## PM-01- Project Planning completed.

## PM-02 — Dataset Preparation
Preserved the original CSV and imported it into Excel format.

## PM-03 — Data Profiling
The dataset has 91,250 records and 15 fields: 50 SKUs, 5 warehouses, 10 suppliers, and 4 regions. There are no blank fields, duplicate rows, duplicate date/SKU/warehouse keys, negative numeric values, or invalid flag values. It contains 365 daily records per SKU/warehouse combination.

**Data limitations:** 2024-12-31 is missing. `Stockout_Flag` is zero throughout, so it cannot support stockout-rate analysis. Physical count/adjustment records and actual order/delivery dates are absent, so inventory accuracy and on-time supplier performance cannot be directly measured.

**Next:** Clean and validate the dataset, accounting for these limitations.
