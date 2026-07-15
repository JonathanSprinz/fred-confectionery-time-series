# fred-confectionery-time-series
 Time series analysis of U.S. confectionery production (FRED data) in R . Trend and seasonal decomposition revealing Halloween/Christmas demand spikes.
# Confectionery Production Time Series Analysis

Time series analysis of U.S. confectionery product manufacturing (FRED IPG3113N series) in R, exploring long-term trend and seasonal demand patterns using `ts()` decomposition.

## Overview

This project uses monthly confectionery production data (1972–2022, sourced from FRED) to investigate seasonal demand patterns in the confectionery industry, driven by events like Halloween and Christmas. 

## Data

- **File:** `FRED.csv`
- **Source:** Federal Reserve Economic Data (FRED)
- **Variables:** `DATE` (monthly), `IPG3113N` (production index)
- **Period:** January 1972 – December 2022 (600 monthly observations)

## Methods

The analysis, in `Time Series.Rmd`, covers:

1. Importing and sense-checking the data
2. Converting the date column to R `Date` format
3. Creating a `ts()` object with monthly frequency
4. Windowing a subset of years for closer inspection
5. Visualising the full series and a monthly boxplot (`cycle()`) to check for seasonality
6. Decomposing the series into trend, seasonal, and random components (`decompose()`)
7. Isolating and inspecting one year of the seasonal component

## Key findings

- Production shows a clear upward trend from the 1970s to around 2000, a dip afterward, and renewed growth in later years, consistent with broader economic cycles (e.g. 2008 recession, COVID-19).
- Strong, repeating seasonality: production is below the yearly average from February through August, and rises sharply from September, peaking in November and December — consistent with Halloween and Christmas demand.

## Requirements

\`\`\`r
install.packages(c("tidyverse", "forecast", "tseries"))
\`\`\`

## How to run

1. Clone this repository
2. Open `Time Series.Rmd` in RStudio
3. Update the `setwd()` path in the first code chunk to point to your local copy of `FRED.csv`
4. Run chunks sequentially (Ctrl+Enter)

## Author

Jonathan Sprinz
