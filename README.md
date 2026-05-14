# Snowpark in Snowflake Python Worksheets and Notebooks

Based on the official Snowflake tutorial: [Getting Started with Snowpark in Snowflake Python Worksheets](https://www.snowflake.com/en/developers/guides/getting-started-with-snowpark-in-snowflake-python-worksheets/)

## Overview

This project demonstrates how to use Snowpark for Python inside Snowflake Notebooks to build a data pipeline that transforms campaign spend and monthly revenue data.

## Prerequisites

- Snowflake account with `ACCOUNTADMIN` role
- Warehouse: `SNOWPARK_DEMO_WH`
- Database: `SNOWPARK_DEMO_DB`
- Schema: `SNOWPARK_DEMO_SCHEMA`
- Tables: `CAMPAIGN_SPEND`, `MONTHLY_REVENUE` (loaded during setup as per the tutorial)

## What the Notebook Does

1. **Import Snowpark** and create a session
2. **Set context** — warehouse, database, and schema
3. **Load tables** — `campaign_spend` and `monthly_revenue` into Snowpark DataFrames
4. **Transform spend data** — group by year/month/channel, then pivot channels into columns
5. **Transform revenue data** — aggregate revenue per year/month
6. **Join** spend and revenue data side by side
7. **Examine** the DataFrame execution plan
8. **Save** the result to a Snowflake table: `SPEND_AND_REVENUE_PER_MONTH`
9. **Deploy** the entire pipeline as a stored procedure: `campaign_spend_monthly_revenue_data_pipeline_sp()`

## Output Table

`SPEND_AND_REVENUE_PER_MONTH` with columns:
- `YEAR`, `MONTH`
- `SEARCH_ENGINE`, `SOCIAL_MEDIA`, `VIDEO`, `EMAIL` (spend per channel)
- `REVENUE`

## Stored Procedure

```sql
call campaign_spend_monthly_revenue_data_pipeline_sp();
```

## Files

| File | Description |
|------|-------------|
| `Code.ipynb` | Main notebook with the full data pipeline |
| `README.md` | This file |
| `LICENSE` | License file |