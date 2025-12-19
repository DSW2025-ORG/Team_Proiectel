# Team_Proiectel

# Energy Transition, Emissions and Economic Development in the EU

## Project Overview
This project explores the relationship between renewable energy adoption, greenhouse gas emissions, and economic development across European Union member states. Using aggregated panel data, the analysis investigates whether increasing the share of renewable energy is associated with lower CO₂ emissions and how energy consumption relates to GDP per capita.

---

## Research Objectives
The main objectives of this analysis are:
- To assess whether a higher share of renewable energy i**Final Report - Energy Transition, Renewable Energy, Emissions, and
Socio-Economic Development in the European Union (2001--2023)**

**1. Project Description**

The energy transition represents one of the defining economic, social,
and environmental challenges of the 21st century. European Union (EU)
member states-particularly those in Central and Eastern Europe-face the
dual pressure of reducing greenhouse gas (GHG) emissions while ensuring
economic growth and increasing the share of renewable energy. This
challenge is intensified by the legacy of fossil-fuel-dependent energy
systems and recent policy developments such as the *European Green Deal*
(2019).

Our project investigates the relationship between:

-   **energy consumption**,

-   **renewable energy capacity and generation**,

-   **GHG emissions (CO₂, CH₄, N₂O)**, and

-   **socio-economic development indicators**

across **all EU member states** over the period **2001--2023**.

**Research Questions**

1.  **To what extent is the increase in the share of renewable energy
    associated with reductions in GHG emissions across EU member
    states?**

2.  **How is total energy consumption related to the level of economic
    development (GDP per capita) and demographic dynamics?**

An example of this tension is the recent infringement case where the
**European Commission referred Romania to the Court of Justice of the
EU** for failing to comply with air quality regulations (Directives
2008/50/CE and 2004/107/CE) - illustrating the environmental and
economic pressures faced by Eastern European states.

**Objectives**

The project aims to:

-   quantify the links between energy mix, emissions, and development;

-   assess whether renewable energy adoption contributes meaningfully to
    decarbonization;

-   explore cross-country disparities within the EU;

-   understand whether economic growth continues to drive emissions or
    whether decoupling is visible.

Our unit of analysis is **country × year**, allowing us to capture both
temporal dynamics and structural differences across EU states.

**2. Data Sources and Literature**

**2.1 Data Sources**

The project integrates two major data systems:

**(A) U.S. Energy Information Administration (EIA)**

Extracted through Python API queries and cleaned in
*01_eia_data_Sovan_Cristian_Vasile.ipynb*.

**Indicators used:**

-   primary energy production (Mtoe)

-   primary energy consumption (Mtoe)

-   renewable energy installed capacity (GW)

-   renewable electricity generation (billion kWh)

All indicators were standardized, harmonized by country and year, and
converted to comparable units.

**(B) World Development Indicators (WDI), World Bank**

Collected automatically through API requests and cleaned in\
*02_wdi_data_Valentina Vasile.ipynb* and
*03_wdi_curatare_ValentinaV.ipynb*.

**Indicators:**

-   GDP per capita (constant USD)

-   population

-   urbanization rate (%)

-   greenhouse gas emissions: CO₂, CH₄, N₂O (absolute values and %
    change)

-   institutional indicators:

    -   government effectiveness

    -   regulatory quality

    -   rule of law

    -   control of corruption

-   energy use per capita

-   access to electricity (almost 100% for EU, therefore excluded from
    modeling)

The final combined panel dataset includes all EU countries, 2001--2023
(with 2001 excluded in some WDI series due to 98% missingness).

**2.2 Relevant Literature**

**Lojanica et al. (2025)**

*"The Effects of Renewable Energy, Economic Growth, and Trade on CO₂
Emissions in the EU-15"*\
The study finds that renewable energy reduces emissions, while economic
growth tends to increase them. This supports our decision to analyze the
interplay between GDP per capita, renewable share, and emissions using
panel models.

**Ziemblińska et al. (2025)**

*"Decoupling of economic growth and CO₂ emissions in Central and Eastern
European EU Member States"*\
The paper examines whether economic development can occur without
proportional increases in emissions. It confirms that decoupling exists
in some states but is uneven regionally - directly relevant to our
EU-wide investigation.

**European Green Deal (2019) & EU Energy Policy Framework**

These policies justify including renewable capacity/generation
indicators, as member states adopted binding climate and energy targets.
They also explain structural differences between Western and Eastern EU
states.

**How the literature informs our analysis:**

-   validates the importance of renewable energy share as a predictor of
    emissions;

-   motivates the use of per-capita and relative indicators;

-   provides theoretical grounding for analyzing economic growth vs.
    emissions ("decoupling").

**3. Methodology and Project Steps**

**Step 1: Problem Definition (Entire Team)**

We formulated the research questions, justified the EU as our unit of
analysis, and identified the indicators most relevant for the
energy--economy--emissions nexus.

**Step 2: Data Collection (EIA & WDI)**

**Student 1 - EIA data**

Notebook: *01_eia_data_Sovan_Cristian_Vasile.ipynb*

Main tasks:

-   queried EIA International Data API v2;

-   extracted indicators for production, consumption, renewables
    capacity and generation;

-   validated units, timestamps, missingness patterns;

-   standardized column names;

-   exported clean tables to Neon database.

**Student 2 - WDI data**

Notebooks:\
*02_wdi_data_Valentina Vasile.ipynb*,\
*03_wdi_curatare_ValentinaV.ipynb*

Tasks:

-   automated API extraction with endpoint-specific scripts and
    pagination;

-   created a consistent long-format table (country, year, indicator,
    value);

-   filtered only EU member states;

-   harmonized ISO3 country codes;

-   removed duplicates, standardized data types;

-   uploaded final WDI table to Neon.

**Step 3: Data Cleaning & Integration**

Notebook: *03_cleaning_aggregation_Andreea_Spinu.ipynb*

Tasks:

-   downloaded both database tables and conducted:

    -   variable renaming,

    -   unit standardization,

    -   type casting,

    -   missing value inspection;

-   unified the time range to 2001--2023;

-   merged datasets on *(country, year)*;

-   reshaped into wide format;

-   resolved mismatches between EIA and WDI sampling frequencies;

-   exported the final table **energy_panel_final**.

**Step 4: Exploratory Data Analysis (EDA)**

Notebook: *04_eda_Klaudia_Poka.ipynb*

Analyses included:

-   descriptive statistics for 20+ indicators,

-   histograms, line plots, boxplots, scatterplots,

-   preliminary cross-country comparisons.

**Key EDA Findings:**

1.  **GHG emissions (CO₂, CH₄, N₂O)**

    -   strongly right-skewed (skew \> 1)

    -   dominated by structurally large economies (Germany, France,
        Italy, Poland)

    -   negative % change values indicate gradual decarbonization

2.  **Renewable energy share & generation**

    -   wide variation (0--58%)

    -   strong outliers (Nordic states vs. fossil-heavy Eastern states)

3.  **Energy use per capita**

    -   correlates strongly with GDP per capita

    -   indicates very different economic structures across the EU

4.  **Institutional indicators**

    -   relatively symmetric, stable across time

    -   limited variation compared to energy variables

5.  **Electricity access**

    -   almost constant at 100%

    -   excluded from statistical modeling

**EDA Conclusion:**\
EU countries exhibit high heterogeneity in energy profiles and
emissions, justifying multivariate analysis and normalization
techniques.

**Step 5: Feature Engineering and Statistical Analysis**

Notebook: *05_feature_engineering_analysis_Roberta.ipynb*

**5.1 Feature Engineering**

To enable meaningful cross-country comparisons:

-   **per-capita indicators**

    -   energy use per capita

    -   emissions per capita

-   **ratio-based indicators**

    -   renewable_final_share (%)

    -   renewables_capacity per capita

    -   renewables_generation per capita

-   **growth and transformation variables**

    -   log(GDP per capita)

    -   percentage change in emissions

-   **composite institutional index**

    -   averaged governance indicators to reduce multicollinearity

Rationale: These transformations address outlier dominance, scale
differences, and skewed distributions.

**5.2 Statistical Analysis**

Analyses included:

-   Pearson correlations

-   cross-country comparisons

-   simple and multiple linear regression models

-   interaction terms between economic and energy variables

**Main Results:**

**(A) Renewable energy share significantly reduces CO₂ emissions.**

Countries with higher renewable shares show lower emissions per capita,
consistent with Lojanica et al. (2025).

**(B) Economic growth remains positively associated with emissions.**

Despite EU decarbonization policies, GDP per capita still predicts
higher carbon output - evidence of **incomplete decoupling**.

**(C) Combining renewable expansion with economic growth reduces
emissions more effectively.**

Interaction terms (renewable_share × GDP) were negative and significant.

**(D) Institutional quality is stable but helps explain long-term
adoption of clean energy.**

Although variation is small, better governance correlates with higher
renewable shares and lower emissions.

**4. Main Conclusions**

1.  **Renewable energy expansion is an effective driver of emission
    reductions** in the EU.\
    Higher renewable capacity and generation correlate with lower CO₂
    emissions per capita.

2.  **Economic development still increases emissions**, although the
    magnitude differs by country.\
    Decoupling is visible but incomplete - matching findings from
    Ziemblińska et al. (2025).

3.  **Energy consumption strongly mirrors economic structure**.\
    Industrialized countries show higher per-capita consumption and
    emissions.

4.  **The EU is not homogeneous.**\
    Western and Nordic countries lead in renewable adoption; several
    Eastern states still rely heavily on fossil fuels.

5.  **Institutional indicators matter, but structurally.**\
    Governance affects long-term energy policy success, though with less
    short-run variation.

6.  **Policy implication:**\
    Achieving EU climate targets requires a combined strategy:

    -   accelerating renewable deployment,

    -   improving energy efficiency,

    -   ensuring equitable economic development across regions.

**5. Difficulties and Limitations**

-   **Missing values**, especially WDI series for 2001, required
    exclusion of certain years.

-   **Unit inconsistencies** across EIA indicators required substantial
    normalization.

-   **Outliers** reflect real economic structures; they cannot be
    removed and complicate modeling.

-   **Electricity access** was uniform in the EU and had no explanatory
    power.

-   **Institutional indicators** showed low variance, limiting their
    statistical impact.

Despite these challenges, the final dataset is coherent, reproducible,
and suitable for panel analysis.

**6. Team Contributions**

**Cristian Sovan**

EIA data extraction, cleaning, normalization, structuring as long
format.

**Valentina Vasile**

WDI data extraction, API automation, cleaning, standardization, and
restructuring.

**Andreea Spînu**

Merging datasets, unit harmonization, resolving missingness,
constructing the final integrated panel.

**Klaudia Poka**

Full EDA: descriptive statistics, univariate and bivariate
visualizations, preliminary conclusions.

**Roberta Grosu**

Feature engineering, creation of transformed variables, composite
governance indices, and statistical modeling.

**7. References**

-   U.S. Energy Information Administration. (2023). *International
    Energy Statistics*.

-   World Bank. (2023). *World Development Indicators*.

-   Lojanica, N., et al. (2025). *The Effects of Renewable Energy,
    Economic Growth, and Trade on CO₂ Emissions in the EU-15*. Energies.

-   Ziemblińska, K., et al. (2025). *Decoupling of Economic Growth and
    CO₂ Emissions in Central and Eastern EU Member States*.

-   European Commission (2019). *European Green Deal*.

-   Focus Energetic (2025). *Romania referred to the CJEU for air
    quality directive non-compliance*.
s associated with lower greenhouse gas emissions.
- To examine the relationship between energy consumption per capita and economic development.
