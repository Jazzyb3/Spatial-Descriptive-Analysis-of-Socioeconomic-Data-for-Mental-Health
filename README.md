# Spatial Exploration and Descriptive Analysis of Survey, Crime, and Census Data for Mental Health Research

**Authors:** Jasmine Baldwin, Yvonne Yang
**Institution:** Southern Methodist University
**Tools:** ArcGIS Pro, R / R Shiny

## Overview

This project explores how county-level social and economic conditions relate to mental-health outcomes across the United States. It integrates demographic, income, crime, and survey data into two complementary visualization tools:

- An **ArcGIS Pro web map** that situates survey respondents within their broader geographic and social environment
- An **R Shiny dashboard** that allows interactive exploration of mental-health outcomes across demographic and socioeconomic groups

The project was conducted in collaboration with Dr. Hans Oh and his research team, using survey data collected from Black and Asian/Pacific Islander American emerging adults covering mental-health symptoms, stigma, help-seeking intentions, substance use, food insecurity, and awareness of mental-health services.

## Data Sources

| Source | Description |
| --- | --- |
| FBI Crime Data Explorer | County-level reported crime counts and categories |
| American Community Survey (ACS), U.S. Census Bureau | County-level demographic, racial composition, and median household income data |
| Client-provided survey data (Dr. Hans Oh's team) | Individual-level mental-health, demographic, and geolocation data |
| U.S. Census TIGER/Line Shapefiles | County boundary geography for spatial joins and mapping |

## Methods

### Data Preprocessing
- Crime, demographic, and income datasets were cleaned, standardized, and joined to county boundaries in ArcGIS Pro
- Duplicate and inconsistent county/agency records were resolved, and total crime counts and majority-crime-category percentages were computed per county
- ACS demographic and income fields were converted from coded metadata to descriptive, numeric variables and merged into unified county-level tables
- Survey respondents were spatially joined to counties using an expanding search radius (5-mile increments up to 35 miles) to correct for coordinate inaccuracies
- The final integrated dataset (2,801 rows × 467 variables) was exported to CSV and imported into R, where simplified race/education/insurance categories and outcome percentage variables (depression/anxiety, self-harm, suicidal ideation/attempts) were derived

### ArcGIS Mapping
Interactive layers were built to visualize:
- Crime per capita by county
- Majority race/predominance by county
- Median household income by county
- Survey respondent density (heat map)

### R Shiny Application
Built with `shiny`, `shinydashboard`, `plotly`, `reactable`, `scales`, and `purrr`, the dashboard includes:
- **Visualizations tab** – interactive bar charts comparing mental-health outcomes across user-selected demographic variables
- **All Counties tab** – searchable, sortable summary table of demographic, income, and crime indicators by county
- **Individual County tab** – detailed county-level breakdown of racial composition, income, and crime type, with downloadable charts

## Key Findings

- **Gender:** Males reported higher rates of suicide attempts (12.6%) and self-harm (19%); females reported more suicidal ideation only (12.4%)
- **Age:** Anxiety, depression, and self-harm were most elevated among young adults (18–29) and again in the late twenties
- **Sexual orientation:** Suicidal ideation was reported by 19.7% of homosexual and 22.2% of bisexual respondents, vs. 9.3% of heterosexual respondents; a similar pattern held for self-harm
- **Employment:** Respondents on disability/medical leave reported the highest combined depression and anxiety (53.5%–58.1%); unemployed respondents not seeking work reported the highest suicide attempt rate (20.5%)
- **Race/education/insurance:** Outcomes varied meaningfully by race, education level, and insurance status, pointing to structural and health-care-access factors as contributors to mental-health disparities
- **Geography:** Crime was concentrated in urban areas, while the Midwest and Great Plains showed lower crime and more homogenous populations; survey coverage was geographically uneven and concentrated in metropolitan counties (e.g., Bergen County, NJ had the most respondents at 251)

## Limitations

- Survey data are geographically uneven and not population-representative
- Over one-third of counties had only one respondent, and nearly two-thirds had fewer than five, limiting generalizability
- Census income data reflect the head-of-household's race, which may affect interpretation of racial income comparisons

## Future Work

- Expand geographic coverage and sample size for improved representativeness
- Incorporate additional contextual data sources
- Apply longitudinal or predictive methods to study how environmental influences on mental health evolve over time


## Links

- ArcGIS Web Map Application: https://arcg.is/njvaL1
- R Shiny Dashboard: https://yvonne6341yang.shinyapps.io/surveyexplorerfinal/

## References

- Federal Bureau of Investigation. (2024). *Crime Data Explorer: Reported Violent Crimes by County.*
- Sampson, R. J., Raudenbush, S. W., & Earls, F. (1997). Neighborhoods and Violent Crime: A Multilevel Study of Collective Efficacy. *Science*, 277, 918–924.
- U.S. Census Bureau. (2023). *American Community Survey 5-Year Estimates.*
- U.S. Census Bureau. (2025). *TIGER/Line Shapefiles.*
- World Health Organization. (2014). *Social determinants of mental health.*
