## Enrollment Dataset

### 1. Dataset Overview

The enrollment dataset contains school enrollment rates for primary, secondary, and tertiary education from 2000 to 2023. The data is sourced from World Bank education indicators and represents different geographical regions (South Asia, European Union, etc) and economic regions (High, Middle and Low Income).

The purpose of this dataset is to analyze:

* trends in enrollment over time
* differences across education levels and regions
* gender disparities in access to education

---

### 2. Data Sources

The dataset was constructed from six raw CSV files:

* Primary School Enrollment(male and female)
* Secondary School Enrollment (male and female)
* Tertiary School Enrollment (male and female)

Each file contains yearly enrollment rates with years as columns for multiple regions and countries.

---

### 3. Data Cleaning and Preprocessing

First we had to clean and transform our enrollment dataset.

* Skipped metadata rows using `skiprows=4`

* Selected relevant columns:
  * Country Name
  * Country Code
  * Indicator Name
  * Years 2000–2023
* Removed unnecessary columns such as indicator code and years prior to 2000

* Filtered for our project's selected regional groups:
  * AFE, AFW, ARB, AUS, EAS, EUU, LCN, NAC, SAS, LIC, LMC, UMC, HIC
* Fixed any whitespace inconsisencies in the country codes and names using, which also helped to standardize the column names
`TRIM("Country Code") AS country_code`

* Removed rows with all missing values across selected years

---

### 4. Data Transformation

The data was transformed from wide (years as columns) to long (years as rows) format:

* Resulting structure:
  * one row per country, year, and education level, with separate columns for male and female enrollment rates


Male and female datasets were then merged on:
* country_code
* year

---

### 5. Data Integration

Separate datasets for:

* primary
* secondary
* tertiary

were combined into a single dataset with an additional column:
`level` (primary, secondary, tertiary) to indicate education level

The final dataset (all_enrollment_combined.csv) contains:
* one row per country, year and education level
* separate columns for male and female enrollment rates

---

### 6. Key Variables

| Column       | Description                                    |
| ------------ | ---------------------------------------------- |
| country_name | Name of region                                 |
| country_code | Region code (e.g., EUU, SAS)                   |
| year         | Year (2000–2023)                               |
| level        | Education level (primary, secondary, tertiary) |
| male         | Male enrollment rate (%)                       |
| female       | Female enrollment rate (%)                     |
gender_gap | *(Derived variable)* Difference between female and male enrollment (calculated during analysis, not stored in dataset)

---

### 7. Final Dataset Structure

The final dataset is a panel dataset containing:

* 13 regions
* 24 years (2000–2023)
* 3 education levels

This dataset enables analysis of enrollment trends and gender differences across different regions and times.

---

### 8. Notes and Limitations

* Data is aggregated at the regional level, not individual countries
* Some values are missing depending on region and year
* Enrollment rates are expressed as gross percentages and may exceed 100% in some cases

---
## Trained Teacher Dataset

### 1. Dataset Overview

The trained teachers dataset contains the percentage of trained teachers in secondary education from 2000 to 2023. The data is sourced from World Bank education indicators and represents selected geographical regions and income groups, such as South Asia, the European Union, High income, and Low income.

The purpose of this dataset is to analyze:

* Trained teacher percentages over time
* Compare patterns across regions and income groups
* Evaluate how teacher training levels vary across the selected groups

---

### 2. Data Sources

The dataset was constructed from one raw CSV file:

* Total trained teachers in secondary education

The file contains yearly trained teacher percentages with years stored as columns for different regions and income groups.

---

### 3. Data Cleaning and Preprocessing

First, the trained teachers dataset was cleaned and transformed.

* Skipped metadata rows using `skiprows=4`
* Selected relevant columns:
    * Country Name
    * Country Code
    * Indicator Name
    * Years 2000–2023
* Removed unnecessary columns, including the indicator code and data from years prior to 2000
* Filtered for the project’s selected regional groups:
    * AFE, AFW, ARB, AUS, EAS, EUU, LCN, NAC, SAS, LIC, LMC, UMC, HIC
* Standardized column names and preserved only the needed variables for analysis
* Retained missing values where data was not reported, since some regions and years did not contain trained teacher observations

---

### 4. Data Transformation
The data was transformed from wide format, where years were columns, into long format, where years became rows.

* Resulting structure:
    * one row per country and year, with a single column for trained teacher percentage

The final long-format variables were:

* country_name
* country_code
* year
* trained_teacher


---

### 5. Data Integration
Unlike the enrollment dataset, this dataset came from a single source and did not require merging across multiple files or categories.

The final dataset (total_trained_teachers_secondary_cleaned.csv) contains:

* one row per country and year
* one column for trained teacher percentage in secondary education


---

### 6. Key Variables
| Column          | Description                                           |
| ------------    | ----------------------------------------------------- |
| country_name    | Name of region                                        |
| country_code    | Region code (e.g., EUU, SAS)                          |
| year            | Year (2000–2023)                                      |
| trained_teacher | Percentage of trained teachers in secondary education |

---

### 7. Final Dataset Structure

The final dataset is a panel dataset containing:

* 13 regions
* 24 years (2000–2023)
* 1 outcome measure: trained teacher percentage

This dataset enables analysis of trained teacher trends across different regions and income groups over time.

---
### 8. Basic descriptive statistics 

* Observations: 312 country-year rows
* Non-missing trained_teacher: 126
* Mean: 78.67
* Median: 80.43
* Min / Max: 45.50/99.86

---

### 9. Notes and Limitations

* Data is aggregated at the regional or income-group level, not individual countries
* Some values are missing depending on region and year
* Missingness is a major limitation since after reshaping, the dataset had 312 country-year rows, but only 126 had non-missing trained teacher values

---


