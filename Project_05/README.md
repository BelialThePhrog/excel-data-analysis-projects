# Project 5: Power Query ETL & Data Modeling

## Project Overview
This project showcases an automated **ETL (Extract, Transform, Load)** pipeline built entirely within Excel using **Power Query** and **Power Pivot**. The objective was to ingest raw, messy CSV files, clean the data structure, build a relational Data Model, and generate accurate financial Pivot Tables.

## The Business Challenge
The raw data extract suffered from several common real-world anomalies:
*   **Misnamed Source Files:** The `Customers.csv` and `Products.csv` files had their data swapped by the source system.
*   **Wide-Format Sales Data:** Monthly sales quantities were pivoted across columns (Jan, Feb, Mar...) making time-series aggregations impossible.
*   **Segmented Data:** Sales records were split across multiple yearly files (`Sales_2020.csv`, `Sales_2021.csv`).
*   **Chronological Sorting Bug:** Initial analysis attempts (`Book1.xlsx`) resulted in Pivot Tables sorting months alphabetically (Apr, Aug, Dec, Feb...) instead of their true chronological order.

## Core Technologies & Skills Demonstrated

### 1. Power Query (Get & Transform)
*   **Automated Extraction:** Connected Excel directly to the folder containing the raw CSVs, establishing a dynamic refresh path.
*   **Data Reshaping (Unpivot):** Applied the "Unpivot Other Columns" transformation to convert the wide-format monthly sales data into a proper, normalized long-format layout (Year, Month, Quantity).
*   **Appending Queries:** Combined the historical 2020 and 2021 sales tables into a single unified Fact Table.
*   **Data Cleansing:** Renamed queries to correct the swapped Customers/Products source files and filtered out null/zero-quantity transactions to optimize the model size.

### 2. Power Pivot & Data Modeling
*   **Star Schema Design:** Loaded the cleaned queries directly into the Excel Data Model (bypassing the worksheet limit). Created one-to-many (1:*) relationships between the central Sales Fact Table and the Products/Customers Dimension Tables.
*   **Chronological Sorting Fix:** Created a custom Month/Date dimension table and applied the **Sort by Column** feature to fix the alphabetical month sorting issue seen in early pivot attempts.

### 3. DAX (Data Analysis Expressions)
*   **Financial Metrics:** Created calculated columns and explicit DAX measures to compute `Total Revenue`, `Total Cost`, and `Net Profit` by dynamically multiplying related fields from the Fact and Dimension tables (`RELATED()` function equivalents).

## How to Explore
1. Open the finalized `.xlsx` workbook.
2. Go to the **Data** tab and select **Queries & Connections** to inspect the applied M code steps.
3. Open the **Power Pivot** window to view the diagram view of the Star Schema relationship and the DAX formulas.
