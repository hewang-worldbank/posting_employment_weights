# Posting Employment Weights

This repository provides the employment-based sampling weights used in Huang, Liu, Wang, and Yu (2026), "Who Takes the Hit? The Uneven Impact of Generative AI on Hiring Demand Across Countries," a background paper for the World Development Report 2026: The Promise of Artificial Intelligence.

## Why these weights

Online job postings are not representative of labor markets. Coverage varies widely across countries (Lightcast captures roughly 70 percent of U.S. vacancies but less than 1 percent in many developing economies), and within countries postings skew toward high-skill, white-collar, and ICT-intensive occupations. Unweighted estimates therefore over-represent occupations where postings are dense rather than where workers are. These weights re-weight each occupation by its share of wage employment, so that estimates are proportional to workers rather than to vacancies.

## Source data

Employment comes from the ILOSTAT database of the International Labour Organization, which harmonizes national Labor Force Surveys to ISCO-08. We use wage employees aged 15 and above, excluding armed forces occupations and the agriculture sector.

## Construction

1. **One-digit employment.** Wage employment is taken from ILOSTAT for each country and one-digit ISCO-08 major group.
2. **Four-digit disaggregation.** Employment in each major group is distributed equally across its four-digit unit groups, matching the occupation codes in the Lightcast posting data. All four-digit occupations within the same major group in a country therefore carry the same employment value.
3. **Normalization.** Each occupation's employment is divided by the country total, so that the weights sum to one within each country. This gives every country equal influence in pooled estimates.

## File

`occupation_employment_84countries.csv` contains 27,242 rows, one per country and four-digit occupation. It covers the 84 countries in the baseline sample (42 high-income and 42 low- and middle-income economies, following the World Bank FY2026 income classification) and 410 ISCO-08 unit groups. Not every occupation appears in every country; the number per country ranges from 158 to 408.

| Variable | Type | Description |
|---|---|---|
| `iso3` | string | ISO 3166-1 alpha-3 country code |
| `occupation` | integer | ISCO-08

Huang, Jingyun, Yan Liu, He Wang, and Shu Yu. 2026. "Who Takes the Hit? The Uneven Impact of Generative AI on Hiring Demand Across Countries." Background paper for the World Development Report 2026. World Bank, Washington, DC.

## Contact

Yan Liu (yanliu@worldbank.org), He Wang (hwang21@worldbank.org), Shu Yu ()
