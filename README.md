# Dbx_fun

# RetailPulse Lite (Databricks Serverless ETL)

Goal: Build a small end-to-end ETL pipeline in Databricks using Spark/Databricks SQL with minimal compute (Free Edition friendly).

## What this project builds
Medallion-style tables inside the `retailpulse_lite` database:

- **Landing**: `landing_*` tables (generated sample data)
- **Bronze**: `bronze_*` tables (raw + ingest metadata)
- **Silver**: `silver_*` tables (cleaned, typed, validated)
- **Gold**: `fact_order_item`, `mart_daily_revenue`

Also includes a simple incremental update (CDC-lite) using `MERGE`.

## How to run (in order)
Run notebooks in `notebooks/`:

1. `00_setup` (Python)  
2. `01_generate_data_small` (Python)  
3. `02_bronze_ingest` (SQL)  
4. `03_silver_gold_checks` (SQL)

## Incremental run
Re-run:
- `02_bronze_ingest`
- `03_silver_gold_checks`

This applies the incremental tables and refreshes marts.

## Notes / constraints
- Designed for Databricks Free Edition + Serverless
- Avoids DBFS paths (Public DBFS root may be disabled)

