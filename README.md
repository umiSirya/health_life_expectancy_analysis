# Health & Life Expectancy : Global Development Indicators Analysis

This is an end-to-end analysis of global health outcomes using the World Bank's World Development Indicators (WDI) dataset exploring how life expectancy, mortality, and health expenditure vary across income groups from 2015–2023, and whether spending more actually buys better outcomes.

---

## Contents

- [Objective](#objective)
- [Dataset](#dataset)
- [Data Cleaning](#data-cleaning)
- [Key Findings](#key-findings)
- [Dashboard Preview](#dashboard-preview)
- [Deliverables](#deliverables)
- [Tools Used](#tools-used)
- [Author](#author)

---

## Objective

Do health outcomes converge across income levels over time, and does higher healthcare expenditure reliably predict better outcomes? This project investigates both questions using country-level WDI data.

## Dataset

| | |
|---|---|
| **Source** | [World Bank World Development Indicators](https://datatopics.worldbank.org/world-development-indicators/) |
| **Files used** | `WDICSV.csv` (indicator values, 217 countries, 1960–2025) · `WDICountry.csv` (Region, Income Group) |
| **Time range** | 2015–2023 |

**Indicators analyzed:**
- Life expectancy at birth, total (years)
- Mortality rate, under-5 (per 1,000 live births)
- Mortality rate, infant (per 1,000 live births)
- Maternal mortality ratio (per 100,000 live births)
- Current health expenditure (% of GDP)

## Data Cleaning

- **Fixed a silent load failure** — pandas' default C parser truncated the 189MB source file to 11,598 rows. Reloading with `engine='python'` correctly parsed all 396,970 rows.
- **Dropped Physicians per 1,000 people** after EDA showed 42% missing data even in the recent decade : too sparse for reliable comparison.
- **Joined country metadata** via inner merge, which cleanly excluded regional/income-group aggregates (e.g. "World," "Arab World") from the country-level analysis.
- **Reshaped** from wide (year columns) to long format for Power BI modeling.
- **Final cleaned file:** `health_indicators_clean_long.csv` (9,765 rows).

## Key Findings

| Finding | Detail |
|---|---|
| Life expectancy gap narrowing | High–low income gap fell from **18.8 → 15.6 years** (2015–2023) |
| Under-5 mortality | Fell faster in low-income countries (**−23.7%**) than high-income (**−14%**), though the absolute gap remains large (65.7 vs. 6.3 per 1,000) |
| Maternal mortality | Widest disparity of all indicators studied — low-income countries have an **18.7x higher rate** than high-income countries |
| Spending vs. outcomes | Weak correlation (**≈ 0.15**) between health expenditure and life expectancy. The US overspends relative to outcomes; Tuvalu's high ratio reflects small-economy cost structure, not overspending |

## Dashboard Preview

<img width="587" height="334" alt="image" src="https://github.com/user-attachments/assets/8337c10f-abc2-442f-b153-c3f7db6e7271" />

## Deliverables

| Deliverable | File |
|---|---|
| Final Report (PDF) | `health_life_expectancy_report.pdf` |
| Power BI Dashboard | `health_dashboard.pbix` |
| Custom Power BI Theme | `health_dashboard_theme.json` |
| Cleaned Dataset | `health_indicators_clean_long.csv` |
| Python Notebook | `health_life_expectancy_capstone.ipynb` |
| Demo Video | *link here once recorded* |

## Tools Used

- **Python (Google Colab):** pandas — data loading, cleaning, reshaping
- **Power BI:** DAX measures, custom theme, interactive dashboard (KPI cards, trend lines, scatter plot, map, bar chart)
- **GitHub:** version control and portfolio documentation

## Author

**Naomi Sirya** — [github.com/umiSirya](https://github.com/umiSirya)
