# Exploratory Data Analysis in Pandas — World Population

## Overview

An exploratory analysis of world population data using pandas, seaborn,
and matplotlib. The dataset contains population figures for every
country across multiple years (1970–2022), along with area and density
metrics. The goal is to understand how population is distributed
across countries and continents, and how it has changed over time.

**Tool:** Python — pandas, seaborn, matplotlib
**File:** `eda_analysis.ipynb`
**Input data:** `world_population.csv`

---

## What the notebook covers

1. **Initial inspection** — shape, column names, dtypes, null counts
2. **Summary statistics** — mean, median, min/max across numeric columns
3. **Correlation analysis** — a heatmap of every numeric column against
   every other
4. **Continental trend analysis** — population by continent over time
5. **Distribution analysis** — a box plot of population figures across
   years, to expose outliers and skew

---

## Key findings

### 1. Population is extremely unequally distributed

The box plot of population by year shows the striking shape of the
data: **most countries cluster near zero, while a tiny handful sit at
1.4 billion**. The median country has a population in the low tens of
millions; the outliers — China and India — are roughly **200× that
size**. Population is one of the most unequally distributed metrics
in the world, and any global analysis has to account for this skew.

### 2. Asia dominates — and its lead is widening

The population-by-continent chart shows **Asia** as a clear outlier,
with roughly **4.6 billion people in 2022** — more than all other
continents combined. Asia's growth rate is also the steepest among
large continents, particularly between 1990 and 2010. This is one of
the single most consequential demographic facts of the last 50 years.

### 3. Africa is growing fastest relative to its size

While Asia dominates in absolute numbers, **Africa** shows the most
dramatic relative growth. Starting from a low base in 1970, it has
grown faster than any other continent — the slope of its line is
steeper than the others in percentage terms. Many demographers
project Africa to be the dominant source of global population growth
through the 21st century.

### 4. Time-series population columns are almost perfectly correlated

The correlation heatmap shows the population columns from 1970 through
2022 have correlations between **0.97 and 1.0** with each other. This
makes intuitive sense — a country's population today strongly predicts
its population in past years. It also means for modeling purposes,
including all year columns would be redundant; one or two are enough.

### 5. Area correlates with population more than density does

Surprisingly, **`Area (km²)` has a moderate positive correlation with
population (~0.45–0.51)**, while **`Density (per km²)` has essentially
zero correlation with population**. Large countries tend to have more
people; but population density tells you very little about total
population. This is a useful reminder that intuitively similar metrics
can behave very differently.

---

## Files in this folder

| File | What it is |
|---|---|
| `eda_analysis.ipynb` | The full analysis notebook with code, charts, and outputs |
| `world_population.csv` | Raw dataset used in the analysis |

---

## Notes

- The notebook uses a local file path — update `pd.read_csv(...)` to
  point to your own location before running.
- Charts are rendered inline in the notebook and visible on GitHub.

---

## Skills demonstrated

- pandas: `read_csv`, `info`, `describe`, `isna`, `groupby`, aggregation
- Correlation matrix and heatmap with seaborn
- Line plots with matplotlib for multi-series time data
- Box plots for distribution and outlier analysis
- Continental aggregation and grouping
- Iterative exploration — starting broad, then narrowing to specific questions
