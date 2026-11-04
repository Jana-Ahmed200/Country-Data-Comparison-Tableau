# Country Data Comparison: Excel Power Query and Tableau

An end-to-end analytics project: cleaning a raw country indicators dataset in **Excel Power Query**, then building an interactive **Tableau** report with four linked dashboards and a Tableau Story that compares countries on economy, trade, health, and energy.

---

## Project Overview

The raw dataset holds dozens of indicators per country (CIA World Factbook style, approx. 2005 estimates). The goal was to turn it into a clean, analysis-ready table and answer questions such as:

- Which economies and trade partners dominate the world?
- How are wealth, life expectancy, and infant mortality related?
- Who produces and consumes energy, and how does infrastructure compare across income groups?

## Dataset

- **Source:** country indicators table (CIA World Factbook), approx. 2005 estimates
- **Raw file:** `uncleaned Country Data Comparison.csv`, semicolon-delimited, 263 rows x 45 columns (the second row holds data types)
- **Cleaned file:** `cleaned Country Data Comparison.xlsx`, 192 countries x 36 indicators
- **Indicators:** population, GDP, trade, debt, reserves, inflation, health, HIV/AIDS, energy, roads, telephones, internet

## Data Cleaning (Excel Power Query)

**Structure**
- Loaded the semicolon-delimited CSV and removed the data-type row
- Trimmed and cleaned text, removed duplicates and blank rows, fixed data types
- Renamed columns to drop units from the headers

**Rows: 263 down to 192**
- Removed non-country entities (European Union, Antarctica, British Indian Ocean Territory, oceans, World)
- Removed dependent territories and very small islands

**Columns: 45 down to 36**
- Dropped columns that were mostly empty: natural gas (5 columns), oil exports, oil imports, oil proved reserves, public debt (% of GDP)
- Created `Oil Net exports` = oil production - oil consumption

**Missing values**
- `Current account balance` = Exports - Imports
- `People living with HIV/AIDS` = adult prevalence rate / 100 x Population
- `Military expenditures (USD)` = % of GDP / 100 x GDP
- `Military expenditures (% of GDP)` = median of available values (1.9% for 28 countries)
- Remaining blanks were left as null instead of being invented

## Tableau Work

**Calculated fields:** Trade Balance, Trade Status, Income Group, Selected Metric, Debt to GDP, Weighted Birth/Death Rate, Internet Penetration, KPI helper fields (Top GDP Country, Top Surplus/Deficit Country)

**Parameters:** Metric Selector (Exports / Imports / GDP / Population), Trade Size (Top N slider)

**Dashboards**

| Dashboard | What it shows |
|---|---|
| Executive Overview | KPIs, global metric map, top 10 exporters, wealth vs life expectancy, trade balance |
| Economy & Trade | Growth vs inflation, debt to GDP, foreign reserves, exports vs imports |
| Health & Demographics | Life expectancy, infant mortality, fertility, HIV prevalence, birth vs death rate by income group |
| Energy & Infrastructure | Oil production, net oil exporters, electricity, roads vs railways, internet and phone access |

**Interactivity:** dashboard filter actions, income and trade-status filters, Top N parameter, navigation buttons between dashboards

**Story:** a guided walk through the findings, one dashboard per story point

## Key Insights

- The **United States** has the largest GDP ($11.75T) and also the largest trade deficit (-$681B); **Germany** has the largest trade surplus (+$176.6B)
- Higher income goes with longer life and lower infant mortality, but high HIV prevalence pulls several African countries far below the trend (Swaziland has the highest adult prevalence at 38.8%)
- Fertility and infant mortality rise together, and both are highest in low-income countries
- Median inflation is only 3.5%, while a few countries (for example Zimbabwe at 133%) are extreme outliers

## Screenshots

| | |
|---|---|
| ![Global dashboard](screenshots/global%20dashboard.png) | ![Economy dashboard](screenshots/economy%20dashboard.png) |
| ![Demographics dashboard](screenshots/demographics%20dasboard.png) | ![Energy dashboard](screenshots/energy%20dashboard.png) |

Story and key insights: see the `screenshots` folder.

## Repository Structure

```
├── screenshots/                               Dashboard and story images
├── uncleaned Country Data Comparison.csv      Raw dataset
├── cleaned Country Data Comparison.xlsx       Cleaned dataset
├── country comparison project.twbx            Tableau packaged workbook
└── README.md
```

## Limitations

- Data is a snapshot of approx. 2005 estimates, not current figures
- Some values (HIV cases, military spending) were estimated to fill gaps, so those fields are approximate
- 28 countries share the same military spending % (the median), so that field is not meaningful for country-level comparison
- Some indicators still have gaps: railways (32% missing), investment (25%), HIV deaths (24%), unemployment (18%)
- Extreme outliers were capped on charts for readability; the raw values stay in the data

## Tools

Excel Power Query, Tableau Desktop, Tableau Public

## How to Explore

1. Open the live dashboard on Tableau Public: [Tableau Public link]
2. Or download `country comparison project.twbx` and open it in Tableau Desktop or Tableau Public (the data is packaged inside)
3. To reproduce the cleaning, load `uncleaned Country Data Comparison.csv` in Excel Power Query (delimiter: semicolon) and follow the steps above, or compare with the cleaned file

## Skills Demonstrated

- Data cleaning and transformation in Excel Power Query (custom columns, conditional logic, filtering, null handling)
- Tableau calculated fields, parameters, LOD expressions, and Top N filters
- Dashboard design: KPI cards, maps, scatter plots, diverging bars, dual-measure charts
- Dashboard actions, interactive filters, and navigation between dashboards
- Data storytelling with a Tableau Story
- Handling outliers and missing data transparently

## Future Improvements

- Replace the approx. 2005 data with a current source (for example World Bank indicators) and add a time dimension
- Add a Region field to compare regions, not only income groups
- Use population-weighted averages across all comparisons

## Acknowledgements

Data: CIA World Factbook (country indicators, approx. 2005 estimates)

## Author

**Jana Ahmed**
Business Information Systems student at Capital University | Aspiring Data Analyst

[GitHub](https://github.com/Jana-Ahmed200) · [LinkedIn link: https://www.linkedin.com/in/jana-ahmed-rashad-242328373?utm_source=share_via&utm_content=profile&utm_medium=member_ios] · [Email:ja01007325655@gmail.com]
- `Country_Dashboard.twbx`: Tableau packaged workbook
- `Country Data Comparison3.xlsx`: cleaned dataset
- `Country Data Comparison.csv`: original dataset
