# DATASCI 350 - Final Project
## Gender Gaps in Education: A Cross-Regional Analysis of Enrollment and Teacher Quality (2000–2023)

### Group Members
- [Ayushi Chowksey] (2556332)
- [Hank Standaert] (2558027)
- [Ryana Rajesh] (2549737)
- [Chau Anh Nguyen] (2575963)
- [Jacob Hillman] (2580176)

---

## Project Overview
This project analyzes gender disparities in school enrollment and the relationship between trained teachers and student persistence across global regions from 2000 to 2023. Data is sourced from the World Bank's World Development Indicators (WDI) database.

**Research Questions:**
1. How do male vs. female school enrollment rates compare across global regions (primary, secondary, and tertiary) from 2000–2023?
2. How does the percentage of trained teachers in secondary schools affect student persistence/completion rates across regions?

---

## Repository Structure

datasci350-project/
├── data/
│   ├── raw/          # Original downloaded CSVs from World Bank
│   └── cleaned/      # Cleaned and filtered datasets
├── docs/             # Codebook and entity-relationship diagram
├── figures/          # Plots and tables from analysis
├── quarto/           # Quarto report (.qmd, .pdf, .html)
└── scripts/          # SQL and Python scripts

---

## Data Sources
All data sourced from the [World Bank WDI database](https://databank.worldbank.org/source/world-development-indicators).

| Indicator | Code |
|-----------|------|
| School enrollment, primary female (% gross) | SE.PRM.ENRR.FE |
| School enrollment, primary male (% gross) | SE.PRM.ENRR.MA |
| School enrollment, secondary female (% gross) | SE.SEC.ENRR.FE |
| School enrollment, secondary male (% gross) | SE.SEC.ENRR.MA |
| School enrollment, tertiary female (% gross) | SE.TER.ENRR.FE |
| School enrollment, tertiary male (% gross) | SE.TER.ENRR.MA |
| Trained teachers, secondary female (%) | SE.SEC.TCAQ.FE.ZS |
| Trained teachers, secondary male (%) | SE.SEC.TCAQ.MA.ZS |
| Persistence to last grade, primary (%) | SE.PRM.PRSL.ZS |

---

## How to Reproduce
1. Clone the repository:
   git clone https://github.com/hankstandaert/datasci350-project
   cd datasci350-project
2. Install Python dependencies:
   pip install pandas matplotlib seaborn wbgapi
3. Run SQL cleaning scripts in /scripts/
4. Run Python notebooks/scripts in /scripts/
5. Render the Quarto report:
   quarto render quarto/report.qmd

---

## Regions Analyzed
| Region | Code |
|--------|------|
| Africa Eastern & Southern | AFE |
| Africa Western & Central | AFW |
| Arab World | ARB |
| East Asia & Pacific | EAS |
| European Union | EUU |
| Latin America & Caribbean | LCN |
| North America | NAC |
| South Asia | SAS |
| Low income | LIC |
| Lower middle income | LMC |
| Upper middle income | UMC |
| High income | HIC |