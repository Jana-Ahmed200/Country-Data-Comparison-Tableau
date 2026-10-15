# Country Data Comparison: Excel Power Query and Tableau

Data cleaning in Excel Power Query and an interactive Tableau dashboard and story comparing country indicators (population, GDP, life expectancy, electricity use, unemployment and trade).

## Project Overview
The raw dataset had 263 rows and 41 columns. I cleaned it in Excel Power Query, then built three linked Tableau dashboards and one Tableau Story to explore patterns, correlations and outliers across countries.

## Tools
- Excel Power Query (data cleaning)
- Tableau (dashboards and story)

## Data Cleaning (Power Query)
- Split the semicolon-delimited file, removed the type row and promoted headers
- Trimmed and cleaned the `Country` column and removed duplicates
- Removed rows with fewer than 5 non-null values (28 rows)
- Removed columns with more than 50% missing values (natural gas columns and public debt)
- Converted zeros to null in Unemployment rate and telephone columns
- Filled remaining nulls in rate columns with the column median
- Final result: 235 rows and 36 columns

## Tableau Work
**Calculated fields:** Electricity per Capita, Natural Increase, Income Group, Trade Balance, Trade Size

**Parameters:** Top N (controls the top countries shown) and bin size (controls the histogram)

**Visualization types:** filled map, bar chart, scatter plot (log scale), histogram, treemap, KPI tiles

**Dashboards**
1. **Population Dashboard:** population and natural growth treemap, population vs electricity scatter, unemployment rate
2. **GDP Analysis Dashboard:** top GDP per capita, life expectancy by income group
3. **Trade Finance Dashboard:** trade surplus vs deficit, imports vs exports

Dashboards include navigation icons to move between pages, and everything is tied together in one Tableau Story.
## Dashboards

### Population Dashboard
![Population Dashboard](dashboards/dash population.jpg)

### GDP Analysis Dashboard
![GDP Analysis Dashboard](dashboards/dash gdp.jpg)

### Trade Finance Dashboard
![Trade Finance Dashboard](dashboards/dash trade.jpg)

## Tableau Story

### Welcome
![Story - Welcome](story/home.jpg)

### Population
![Story - Population](story/population.jpg)

### GDP Analysis
![Story - GDP Analysis](story/gdp.jpg)

### Trade Finance
![Story - Trade Finance](story/trade.jpg)

## Key Insights
- China and India dominate population, while natural growth is highest in parts of Africa and South Asia and near zero in countries like Russia, Japan and Italy.
- Electricity consumption rises with population, but countries of similar size can differ a lot.
- Luxembourg leads GDP per capita, and many top spots are small, finance-driven economies.
- Life expectancy rises with income: high-income countries cluster at 75 to 80 years.
- Germany has the largest trade surplus (about 177B), while the United States has by far the largest deficit (about -681B).
- Bangladesh's unemployment rate (about 40%) is an outlier in this dataset.


## Files
- `Country_Dashboard.twbx`: Tableau packaged workbook
- `Country Data Comparison3.xlsx`: cleaned dataset
- `Country Data Comparison.csv`: original dataset
