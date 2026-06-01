---
name: Pandas
slug: pandas
language: python
description: Fast, flexible data analysis library — DataFrames, time series, and data wrangling for Python.
logo: https://upload.wikimedia.org/wikipedia/commons/e/ed/Pandas_logo.svg
website: https://pandas.pydata.org
github: pandas-dev/pandas
year: 2008
pricing: free
open_source: true
license: BSD-3-Clause
tool_type: data
tags: [data, data-science, dataframe, etl, analysis, python, wrangling]
related_frameworks: [numpy, scikit-learn, polars]
features:
  - "DataFrame and Series — labelled, flexible data structures"
  - "Read/write CSV, Excel, SQL, Parquet, JSON, and HDF5"
  - "GroupBy, merge, join, pivot_table for SQL-like data manipulation"
  - "Time series support with DatetimeIndex and resampling"
  - "Missing data handling with `fillna()`, `dropna()`, `interpolate()`"
  - "Rolling and expanding window calculations"
  - "Categorical data type for memory efficiency"
  - "Integrates with matplotlib, seaborn, plotly for visualisation"
install:
  pip: "pip install pandas"
  conda: "conda install pandas"
---

Pandas is the foundation of Python data science — its DataFrame structure brings SQL-like operations (groupby, merge, pivot) and time series handling to Python. It reads and writes CSV, Excel, SQL, Parquet, and JSON. For larger datasets that don't fit in RAM or need better performance, Polars and Dask offer faster or distributed alternatives with a similar API.

## Quick start

```bash
pip install pandas
```

```python
import pandas as pd

# Load and inspect data
df = pd.read_csv('sales.csv')
print(df.head())
print(df.info())
print(df.describe())

# Filtering and selection
high_value = df[df['amount'] > 1000]
q1_sales = df[df['date'].str.startswith('2024-Q1')]

# Groupby aggregation
by_region = df.groupby('region')['amount'].agg(['sum', 'mean', 'count'])
print(by_region)

# Merge two DataFrames
customers = pd.read_csv('customers.csv')
merged = df.merge(customers, on='customer_id', how='left')

# Pivot table
pivot = df.pivot_table(
    values='amount',
    index='region',
    columns='product',
    aggfunc='sum',
    fill_value=0,
)

# Time series resampling
df['date'] = pd.to_datetime(df['date'])
df = df.set_index('date')
monthly = df['amount'].resample('ME').sum()
print(monthly)

# Apply custom function
df['discounted'] = df['amount'].apply(lambda x: x * 0.9 if x > 500 else x)

# Export
merged.to_csv('output.csv', index=False)
merged.to_parquet('output.parquet')
```

## When to use

Pandas is the default choice for data manipulation and analysis in Python. Use it for ETL scripts, exploratory data analysis (EDA), feature engineering for ML models, and any task involving tabular data. For datasets larger than available RAM, Polars (faster, Rust-based) or Dask (distributed Pandas) are better choices. For SQL users, DuckDB lets you run SQL queries directly on DataFrames and Parquet files.
