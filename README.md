# NYC Taxi Dataset Analysis (PySpark on Databricks)

This project analyzes the NYC Yellow Taxi dataset using PySpark on Databricks. It performs EDA and real-time insights, stores results in DBFS, and creates external Parquet tables from flattened JSON.

## Dataset
- Source: [NYC TLC Trip Data](https://data.cityofnewyork.us/api/views/t29m-gskq/rows.csv?accessType=DOWNLOAD)
- File used: `yellow_tripdata_2018-01.csv`

## Key Tasks
1. Loaded dataset into **DBFS** (`/FileStore/tables/`)
2. Created new column `Revenue = Fare_amount + Extra + MTA_tax + Improvement_surcharge + Tip_amount + Tolls_amount + Total_amount`
3. Performed the following PySpark queries:
   - **Q1**: Added `Revenue` column
   - **Q2**: Grouped by area to show increasing passenger count
   - **Q3**: Real-time avg fare/earnings by VendorID using 10-min time windows
   - **Q4**: Moving count of payments using window functions
   - **Q5**: Top 2 vendors by earnings on a specific date with trip distance and passengers
   - **Q6**: Most passengers between pickup/drop zones
   - **Q7**: Top pickup locations in the last 5–10 seconds (time windowing)

## JSON Flattening & External Parquet Table
- Saved query result (`total_fare`) as JSON to DBFS
- Flattened nested `window` field (start, end)
- Saved flattened result as **external Parquet table**:
