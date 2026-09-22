# Sampling Weights for Cross-Country Job Posting Analysis

This repository provides the employment-based sampling weights used in Huang, Liu, Wang, and Yu (2026), "Who Takes the Hit? The Uneven Impact of Generative AI on Hiring Demand Across Countries," a background paper for the World Development Report 2026: The Promise of Artificial Intelligence.

## Why these weights

Online job postings are not representative of labor markets. Coverage varies widely across countries (Lightcast captures roughly 70 percent of U.S. vacancies but less than 1 percent in many developing economies), and within countries postings skew toward high-skill, white-collar, and ICT-intensive occupations. Unweighted estimates therefore over-represent cells where postings are dense rather than where workers are. These weights re-weight each cell by its share of wage employment, so that estimates are proportional to workers rather than to vacancies.

## Source data

Employment counts come from the ILOSTAT database of the International Labour Organization, which harmonizes national Labor Force Surveys to ISCO-08 (occupation) and ISIC Rev. 4 (industry). We use wage employees aged 15 and above.

## Construction

1. **Cells.** Employment is extracted at the country × year × one-digit ISCO occupation × two-digit industry level, for 2021 onward.
2. **Exclusions.** Armed forces occupations and agriculture are dropped, as they are rarely covered by online job boards.
3. **Industry harmonization.** Two roll-ups ensure consistency across survey releases: code 44 is combined with 42, and code 55 is combined with 56.
4. **Missing years.** When a country has no survey observation for a year in the sample window, the most recent pre-ChatGPT observation (2021 or 2022) is carried forward. This affects fewer than 10 percent of country-year cells.
5. **Occupation disaggregation.** Employment in each one-digit ISCO group is distributed equally across its four-digit subcategories, to match the four-digit occupation codes in the posting data.
6. **Weights.** Two schemes are provided:
   - `w_equal_country`: each cell's share of country wage employment, normalized to sum to one within each country, so every country contributes equally to pooled estimates (baseline specification).
   - `w_raw_emp`: raw employment counts, so larger countries and cells contribute proportionally more (robustness check).

## Coverage

Weights are provided for the 84-country baseline sample (42 high-income and 42 low- and middle-income economies) and the 68-country alternative sample. Income groups follow the World Bank FY2026 classification.

## Files

| File | Description |
|---|---|
| `weights_isco4.csv` | Weights at country × year × four-digit ISCO × two-digit industry |
| `weights_isco1.csv` | Underlying employment at country × year × one-digit ISCO × two-digit industry |
| `country_sample.csv` | Country list, income group, and sample membership (84 and 68) |

## Variables

| Variable | Description |
|---|---|
| `iso3` | ISO 3166-1 alpha-3 country code |
| `year` | Calendar year |
| `isco4` / `isco1` | ISCO-08 occupation code |
| `ind2` | Two-digit industry code (harmonized) |
| `emp` | Wage employment (ILOSTAT, persons) |
| `w_equal_country` | Within-country employment share (sums to one by country-year) |
| `w_raw_emp` | Raw employment count weight |
| `imputed` | 1 if the year was carried forward from 2021 or 2022 |

## Citation

Huang, Jingyun, Yan Liu, He Wang, and Shu Yu. 2026. "Who Takes the Hit? The Uneven Impact of Generative AI on Hiring Demand Across Countries." Background paper for the World Development Report 2026. World Bank, Washington, DC.

## Contact

Yan Liu (yanliu@worldbank.org), He Wang (hwang21@worldbank.org)
