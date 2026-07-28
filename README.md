Health & Life Expectancy — Global Development Indicators Analysis

This is an end-to-end analysis of global health outcomes using the World Bank's World Development Indicators (WDI) dataset, exploring how life expectancy, mortality, and health expenditure vary across income groups from 2015–2023 and whether spending more actually buys better outcomes.

Objective

Do health outcomes converge across income levels over time, and does higher healthcare expenditure reliably predict better outcomes? This project investigates both questions using country-level WDI data.

Dataset
Source: World Bank World Development Indicators
Files used: WDICSV.csv (indicator values, 217 countries, 1960–2025), WDICountry.csv (country metadata: Region, Income Group)
Indicators analyzed:
Life expectancy at birth, total (years)
Mortality rate, under-5 (per 1,000 live births)
Mortality rate, infant (per 1,000 live births)
Maternal mortality ratio (per 100,000 live births)
Current health expenditure (% of GDP)
Time range: 2015–2023
Data Cleaning
Fixed a silent load failure: pandas' default C parser truncated the 189MB source file to 11,598 rows; reloading with engine='python' correctly parsed all 396,970 rows.
Filtered to the five health indicators above; dropped Physicians per 1,000 people after EDA showed 42% missing data even in the recent decade — too sparse for reliable comparison.
Joined country metadata via inner merge, which also cleanly excluded regional/income-group aggregates (e.g. "World," "Arab World") from the country-level analysis.
Reshaped from wide (year columns) to long format for Power BI modeling.
Final cleaned file: health_indicators_clean_long.csv (9,765 rows).
Key Findings
The life expectancy gap between high- and low-income countries narrowed from 18.8 to 15.6 years (2015–2023) — real progress, but still wide.
Under-5 mortality fell faster in low-income countries (-23.7%) than high-income (-14%), though the absolute gap remains large (65.7 vs. 6.3 deaths per 1,000).
Maternal mortality shows the starkest disparity of all: low-income countries have an 18.7x higher rate than high-income countries.
Health expenditure (% of GDP) is a weak predictor of life expectancy (correlation ≈ 0.15). The US overspends relative to its outcomes; Tuvalu's high ratio reflects small-economy cost structure, not overspending.
Deliverables
Deliverable	File
Final Report (PDF)	health_life_expectancy_report.pdf
Power BI Dashboard	health_dashboard.pbix
Custom Power BI Theme	health_dashboard_theme.json
Cleaned Dataset	health_indicators_clean_long.csv
Python Cleaning Pipeline	capstone_health_pipeline.py
Demo Video	(link here once recorded)
Dashboard Preview

Show Image

<img width="598" height="332" alt="image" src="https://github.com/user-attachments/assets/8b4f565d-e266-4dff-8f50-728dc27cc9ee" />

Tools Used
Python (Google Colab): pandas — data loading, cleaning, reshaping
Power BI: DAX measures, custom theme, interactive dashboard (KPI cards, trend lines, scatter plot, map, bar chart)
GitHub: version control and portfolio documentation
Author

Naomi Sirya — github.com/umiSirya
