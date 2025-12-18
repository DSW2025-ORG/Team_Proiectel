# Team_Proiectel

# Energy Transition, Emissions and Economic Development in the EU

## Project Overview
This project explores the relationship between renewable energy adoption, greenhouse gas emissions, and economic development across European Union member states. Using aggregated panel data, the analysis investigates whether increasing the share of renewable energy is associated with lower CO₂ emissions and how energy consumption relates to GDP per capita.

---

## Research Objectives
The main objectives of this analysis are:
- To assess whether a higher share of renewable energy is associated with lower greenhouse gas emissions.
- To examine the relationship between energy consumption per capita and economic development.

---

## Data
- **Geographical scope:** European Union countries (27)
- **Time period:** 2000–2022
- **Data structure:** Country–year aggregated panel data
- **Key indicators:**
  - Renewable final energy share (%)
  - CO₂ emissions (absolute and percentage change)
  - Energy use per capita
  - GDP per capita
  - Population and institutional indicators

---

## Methodology
The analysis follows an exploratory and statistical approach:
- Data cleaning and validation
- Univariate exploratory data analysis (EDA)
- Bivariate correlation analysis (Pearson and Spearman)
- Simple linear regression to assess the relationship between energy consumption and GDP per capita

Pearson correlation was used to identify linear relationships, while Spearman correlation was applied to ensure robustness given the presence of outliers and non-normal distributions.

---

## Key Findings
- A higher share of renewable energy is negatively and significantly associated with CO₂ emissions, particularly with their percentage variation.
- Energy consumption per capita shows a strong positive and statistically significant correlation with GDP per capita.
- Results suggest a partial decoupling between economic growth and emissions through renewable energy expansion.

---

## Repository Structure
```text
├── data/
│   └── aggregated_data.sql
├── notebooks/
│   └── EDA_and_Correlation_Analysis.ipynb
├── src/
│   └── utils.py
├── .env.example
├── requirements.txt
└── README.md
