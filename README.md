# Quality, Moisture, and Sourcing Efficiency in Gum Arabic Exports

**Author:** Musaddiq Talle  
**Organisation:** Pluck Agro  
**Role:** Managing Director  
**Programme:** LBA – EMBA (UA High)

---

## Overview

This capstone analyses Pluck Agro's internal shipment register to identify which combination of sourcing region, grade, and handling practices best protects EUR export invoice value. The central commercial problem is moisture control: European buyers penalise shipments that exceed the 12% moisture specification (Grade 1 / Acacia Senegal) or 14% (Grade 2 / Acacia Seyal), and turnaround delays create financing and contract performance risk.

---

## Business Question

> Which sourcing regions, grades, and operational practices maximise EUR export value — and what is the quantified EUR cost of moisture excess and turnaround delay per shipment?

---

## Data

| Item | Detail |
|---|---|
| File | `data/shipment_data_reports.csv` |
| Records | 100 shipments |
| Sourcing regions | Bornu, Yobe, Jigawa, Kano |
| Grades | Grade 1 (Acacia Senegal), Grade 2 (Acacia Seyal) |
| Key variables | `shipment_date`, `sourcing_region`, `grade`, `moisture_content` (%), `turnaround_days`, `value` (EUR) |
| Quality threshold | Grade 1 ≤ 12% moisture (NAFDAC + buyer contract); Grade 2 ≤ 14% |

All data are drawn from Pluck Agro's own operational systems. No commercially sensitive buyer information is included.

---

## Analytical Techniques

1. **Exploratory Data Analysis** — baseline distribution of moisture, grade composition, and EUR value by region; Pareto analysis of moisture exceedances
2. **Data Visualisation** — boxplots of moisture by region, scatter plots of moisture vs. EUR value, export value time series
3. **Hypothesis Testing** — ANOVA on turnaround days by region; t-test on EUR value by grade; Kruskal-Wallis robustness check
4. **Correlation Analysis** — Pearson correlations to assess independence of moisture and turnaround as value predictors before regression
5. **Multiple Regression (OLS)** — EUR value modelled on moisture content, turnaround days, grade, and sourcing region simultaneously; coefficients quantify the per-shipment cost of each quality lever

---

## Key Findings

- Grade 1 (Acacia Senegal) commands a statistically significant EUR premium over Grade 2.
- Regional differences in turnaround time are statistically significant — some regions are consistently slower, creating supply chain governance risk.
- Moisture content above the 12% threshold correlates with materially lower invoice values.
- Regression coefficients directly quantify the EUR cost of moisture excess and turnaround delay per shipment.

---

## Recommendation

Enforce a **moisture threshold gate**: no shipment exceeding 12% moisture (Grade 1) proceeds to loading without re-drying. Differentiate sourcing volume allocation by region based on turnaround performance data.

---

## Project Structure

```
musaddiq_capstone.qmd      # Quarto source (R + Python dual implementation)
musaddiq_capstone.html     # Rendered output
requirements.txt           # Python dependencies
data/
  shipment_data_reports.csv
docs/
  30_marks_template.md
  case_study_recommendation.md
```

---

## Reproducing the Analysis

### R packages

Install from CRAN: `readr`, `dplyr`, `tidyr`, `ggplot2`, `lubridate`, `scales`, `broom`, `knitr`, `kableExtra`, `ggcorrplot`, `patchwork`

### Python packages

```bash
pip install -r requirements.txt
```

Packages: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, `statsmodels`

### Render

```bash
quarto render musaddiq_capstone.qmd
```
