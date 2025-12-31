# Baltimore City Employee Salary Analysis

SQL analysis of Baltimore City government employee salaries comparing pre-COVID (2019) and during-COVID (2021) workforce data.

## Motivation

I wanted to practice SQL while exploring a real-world dataset. Baltimore City's public salary data offers an interesting opportunity to analyze workforce changes during COVID-19.

## Key Findings

- **Workforce Growth:** Baltimore gained ~1,000 employees from 2019 (13,134) to 2021 (14,179)
- **Retention:** 11,281 employees stayed with the city through COVID
- **COVID Raises:** Employees who stayed received an average raise of ~$4,174
- **Top Earners:** Operations Managers and Police leadership are among the highest-paid
- **Tenure vs Salary:** Longer-tenured employees generally earn more

## Skills Demonstrated

**SQL:**
- SELECT, COUNT, AVG
- GROUP BY with HAVING clause
- ORDER BY with LIMIT
- JOIN between tables
- Aggregate functions

**Python:**
- SQLite database creation
- Downloading data from public APIs
- pandas DataFrames
- matplotlib visualizations

## Data Source

**Baltimore Open Data** - Baltimore City Employee Salaries  
https://data.baltimorecity.gov/

The notebook automatically downloads data and creates a local SQLite database.

## Files

- `baltimore_salary_analysis.ipynb` - Main analysis notebook
- `baltimore_salaries.db` - SQLite database (generated when you run the notebook)

## How to Run

1. Clone this repository
2. Install requirements: `pip install pandas matplotlib`
3. Run the notebook - it will download data and create the database automatically

## Sample Queries

```sql
-- Employees who stayed through COVID and their raises
SELECT AVG(salary_2021.annualSalary - salary_2019.annualSalary) 
FROM salary_2019 
JOIN salary_2021 ON salary_2019.name = salary_2021.name

-- Top paying job titles with 50+ employees
SELECT jobClass, AVG(annualSalary), COUNT(*) 
FROM salary_2021 
GROUP BY jobClass 
HAVING COUNT(*) >= 50 
ORDER BY AVG(annualSalary) DESC 
LIMIT 10
```
