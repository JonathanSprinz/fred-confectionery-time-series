# Confectionery Production Time Series Analysis

Time series analysis of U.S. confectionery product manufacturing (FRED IPG3113N series) in R, exploring long-term trend and seasonal demand patterns, and building an ARIMA forecasting model.

## Overview

This project uses monthly confectionery production data (1972–2022, sourced from FRED) to investigate seasonal demand patterns in the confectionery industry, driven by events like Halloween and Christmas, and to forecast future production using a fitted ARIMA model.

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
8. Testing for stationarity with an augmented Dickey-Fuller test (`adf.test()`)
9. Checking the residuals for autocorrelation with an ACF plot and histogram
10. Fitting an ARIMA model (`auto.arima()`) and forecasting 3 and 24 months ahead
11. Extending forecasts to 5, 10, and 20 years
12. Splitting the data into training (1972–2020) and test (2021) sets
13. Fitting the model to the training data and overlaying the test set for comparison
14. Evaluating forecast accuracy with the `accuracy()` function (MAPE)

## Key findings

- Production shows a clear upward trend from the 1970s to around 2000, a dip afterward, and renewed growth in later years, consistent with broader economic cycles (e.g. 2008 recession, COVID-19).
- Strong, repeating seasonality: production is below the yearly average from February through August, and rises sharply from September, peaking in November and December — consistent with Halloween and Christmas demand.
- The augmented Dickey-Fuller test confirmed the series is stationary (p = 0.01), and the ACF plot showed some remaining autocorrelation in the residuals at yearly lags.
- An `auto.arima()` model (ARIMA(2,0,2)(0,1,2)[12] with drift on the full series) was used to forecast future production.

## Model performance

The model was trained on 1972–2020 data and tested against the actual 2021 values it had not seen. It returned a **test set MAPE of 4.6%** — well within the "excellent" accuracy threshold (under 10%) — indicating the model reliably predicts future confectionery production.

## Requirements

```r
install.packages(c("tidyverse", "forecast", "tseries"))
```

## How to run

1. Clone this repository
2. Open `Time Series.Rmd` in RStudio
3. Update the `setwd()` path in the first code chunk to point to your local copy of `FRED.csv`
4. Run chunks sequentially (Ctrl+Enter)

## Author

Jonathan Sprinz
