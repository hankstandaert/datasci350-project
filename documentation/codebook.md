## Enrollment Dataset

### 1. Dataset Overview

The enrollment dataset contains school enrollment rates for primary, secondary, and tertiary education from 2000 to 2023. The data is sourced from World Bank education indicators and represents different geographical regions (SOuth Asia, European Union, etc) and economical regions (High, Middle and Low Income).

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

Each file contains yearly enrollment rates with years as columns for numerous different regions and countries.

---

### 3. Data Cleaning and Preprocessing

First we had to clean and transform our enrollment dataset.

* Skipped metadata rows using `skiprows=4`

* Selected relevant columns:
  * Country Name
  * Country Code
  * Indicator Name
  * Years 2000–2023
* Removed unnecessary columns such as indicatory code and years prior to 2000

* Filtered for our project's selected regional groups:
  * AFE, AFW, ARB, AUS, EAS, EUU, LCN, NAC, SAS, LIC, LMC, UMC, HIC
* Fixed any whitespace inconsisencies in the country codes and names using. This was also used to standardize the column names
`TRIM ("Country Code") AS country_code`

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
