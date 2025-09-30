# OLAP Operations Demo
This assignment demonstrates various Online Analytical Processing (OLAP) operations using Python, pandas, and SQLite. It showcases the three main types of OLAP architectures: ROLAP, MOLAP, and HOLAP, along with common OLAP operations like slice, dice, drill-down, and roll-up.

## Overview
The notebook provides hands-on examples of:

1. ROLAP (Relational OLAP): SQL-based operations on relational databases
2. MOLAP (Multidimensional OLAP): Pre-aggregated data cubes using pandas pivot tables
3. HOLAP (Hybrid OLAP): Combining both relational and multidimensional approaches
4. OLAP Operations: Slice, Dice, Drill-down, and Roll-up operations

## Prerequisites
### Required Libraries

```python
import pandas as pd
import sqlite3
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

## Installation
```python
pip install pandas numpy matplotlib seaborn
```

## Dataset
The demo uses synthetic employee and department data:

```
### Employees Table
emp_id: Employee ID (1-6)
name: Employee names (Alice, Bob, Charlie, David, Eva, Frank)
age: Ages ranging from 25 to 50
salary: Salaries from $50,000 to $100,000
dept_id: Foreign key linking to departments
Departments Table
dept_id: Department ID (1-6)
dept_name: Department names (HR, Engineering, Sales, Marketing, Finance, Support)


## OLAP Architectures Demonstrated
1. ROLAP (Relational OLAP)
Uses SQL queries on relational database (SQLite)
Performs aggregations using SQL GROUP BY and JOIN operations
Real-time querying with flexibility for complex queries

2. MOLAP (Multidimensional OLAP)
Creates pre-aggregated data cubes using pandas pivot_table()
Fast query performance for pre-defined dimensions
Visualized using heatmaps to show salary distribution by department and age

3. HOLAP (Hybrid OLAP)
Combines SQL queries for detailed data with pandas aggregations
Leverages both relational storage and multidimensional processing
Provides balance between storage efficiency and query performance

## OLAP Operations
### Slice Operation
Extracts a subset of data by filtering on one dimension:

```python
slice_df = detail_df[detail_df['dept_name'] == 'IT']

```

### Dice Operation
Filters data across multiple dimensions simultaneously:

```python
dice_df = detail_df[(detail_df['dept_name'] == 'HR') & (detail_df['salary'] > 60000)]

```

### Drill-Down Operation
Moves from summarized to more detailed data:
Visualizes individual employee salaries by department
Shows granular breakdown of aggregated information

### Roll-Up Operation
Aggregates data from detailed to summary level:

```python
rollup_df = detail_df.groupby('dept_name')['salary'].sum().reset_index()

```

Visualizations
The notebook includes several visualization types:

1. Bar plots for ROLAP and HOLAP results
2. Heatmaps for MOLAP cube visualization
3. Grouped bar charts for drill-down analysis
4. Summary charts for roll-up operations

## Usage
Setup Environment: Ensure all required libraries are installed
Run Notebook: Execute cells in order from top to bottom
Database Creation: Sample data is loaded into an in-memory SQLite database
OLAP Operations: Each section demonstrates different OLAP concepts
Visualizations: Charts are generated automatically for each operation

## Important Notes
The database connection uses :memory: for temporary storage
Data relationships are established through dept_id foreign key
All visualizations use seaborn and matplotlib for consistent styling
The notebook demonstrates educational concepts with synthetic data

Author: Nathan Orang'o Omenge ...637
Course: Data Mining and Warehousing
