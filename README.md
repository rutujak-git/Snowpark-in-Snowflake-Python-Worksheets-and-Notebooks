# Snowpark in Snowflake Python Worksheets and Notebooks

Based on the official Snowflake tutorial: [Getting Started with Snowpark in Snowflake Python Worksheets](https://www.snowflake.com/en/developers/guides/getting-started-with-snowpark-in-snowflake-python-worksheets/)

## Overview

This project demonstrates how to use Snowpark for Python inside Snowflake Notebooks to build a data pipeline that transforms campaign spend and monthly revenue data.

## Setup Lab Environment

Before starting, set up the lab environment using this link: [Get Started with Snowpark in Python Worksheets - Lab Setup](https://app.snowflake.com/resources/labs/getStartedWithSnowparkInPythonWorksheets)

This will create the required database, schema, warehouse, and load the sample data tables.

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

<img width="1440" height="730" alt="image" src="https://github.com/user-attachments/assets/19d5e2f1-2526-4ac3-a2d8-7271fc76b1b7" />


## Stored Procedure

The final step deploys the entire pipeline as a stored procedure. Once created, you can view it in the Snowsight Database Explorer under:

`SNOWPARK_DEMO_DB > SNOWPARK_DEMO_SCHEMA > Procedures > CAMPAIGN_SPEND_MONTHLY_REVENUE_DATA_PIPELINE_SP()`

<img width="1440" height="736" alt="image" src="https://github.com/user-attachments/assets/2b862b68-42e6-4907-9171-c0942b5c283e" />


```sql
call campaign_spend_monthly_revenue_data_pipeline_sp();
```

## Files

| File | Description |
|------|-------------|
| `Code.ipynb` | Main notebook with the full data pipeline |
| `README.md` | This file |
| `LICENSE` | License file |
