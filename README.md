# Replication files

R code, data and figures for an analysis of monthly accommodation demand and tour itinerary networks across the 81 provinces of Türkiye (January 2017 – September 2026).

## Contents

| Item | Description |
|---|---|
| `step00_01b_paper_tourism.R` | Complete R code (steps 00–13) |
| `paper_tourism/` | Data: inputs and outputs of every step (CSV, XLSX) |
| `paper_tourism/figures/` | Figures 1–4 (PNG and PDF) |

## Code flow

| Step | What it does | Main output |
|---|---|---|
| 00–00c | Finds the Ministry's monthly accommodation bulletins | `step00*.csv` |
| 01a–01b | Downloads the bulletins and builds the province × month panel | `step01b_il_monthly_panel.csv` |
| 01c | Derives bed capacity from occupancy rates and detects coverage breaks | `step01c_*.csv` |
| 01d | Builds the analysis panel with coverage periods and growth rates | `step01d_analysis_panel.csv` |
| 02a | Geographic matrices: kNN-5, inverse distance, contiguity | `step02a_*.csv` |
| 02b0–02b1 | Collects tour programmes from Jolly, Tatil Sepeti, Setur and TourRadar | `step02b1_tours.csv`, `step02b1_tour_days.csv` |
| 02b2 | Matches place names to provinces and builds the itinerary matrices | `step02b2_*.csv` |
| 03a | Space–time panel model with placebo network and permutation test | `step03a_*.csv` |
| 03b | February 2023 earthquake shock test | `step03b_*.csv` |
| 03c | Pairwise (dyadic) co-movement model | `step03c_*.csv` |
| 03d | Destination-similarity controls | `step03d_*.csv` |
| 04 | Tables and figures | `step04_tables.xlsx`, `figures/` |
| 05 | Robustness of the itinerary networks (source exclusion, programme bootstrap) | `step05_*` |
| 06 | DSP and Freedman–Lane permutation tests | `step06_*` |
| 07 | Timing and sensitivity checks | `step07_*` |
| 08 | Pandemic period excluded | `step08_*` |
| 09 | Lead–lag tests; deduplicated international network | `step09_*` |
| 10 | Lead–lag test without holiday months | `step10_*` |
| 11 | Early (2017–2020) versus late (2022–2026) period | `step11_*` |
| 12 | Province bootstrap for the similarity attenuation | `step12_*` |
| 13 | Gazetteer match rate | `step13_*` |

## How to run

1. Set `base_dir` at the top of the R file to the folder that contains `paper_tourism/`.
2. Run the whole file. A step is skipped when its output files exist, so with the files provided nothing is recomputed. To re-run a step, delete its output files.
3. Steps 00–02 download data from the web. The tour websites change over time, so keep the `step02b*` files to reproduce the networks used here.

Object and column names are in Turkish (for example `yerli` = domestic, `yabanci` = international, `il` = province); a glossary is given at the top of the R file. All random procedures use fixed seeds.

## Not included

Province boundaries from GADM (licence) and copies of the original tour web pages (copyright). Step 02a downloads the boundaries when it is re-run; Figure 1 needs them saved as `paper_tourism/raw_gadm41_TUR_1.json`.

## Data sources

* Ministry of Culture and Tourism of Türkiye, monthly accommodation statistics: https://yigm.ktb.gov.tr/TR-201121/bakanlik-belgeli-tesis-konaklama-istatistikleri.html and https://yigm.ktb.gov.tr/TR-201122/belediye-belgeli-tesis-konaklama-istatistikleri.html
* Public tour programme pages of Jolly, Tatil Sepeti, Setur and TourRadar (November 2026)
* GADM version 4.1, https://gadm.org

## Licence

Code: MIT. Data files created by the authors: CC BY 4.0.
