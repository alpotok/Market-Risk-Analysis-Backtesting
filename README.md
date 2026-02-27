# Market Risk Analysis & Backtesting for PLN/NOK

**Date:** 2024-05-22  

This repository contains a comprehensive analysis of market risk measures for the **PLN/NOK** (Polish Zloty to Norwegian Krone) exchange rate. The project focuses on the estimation and backtesting of **Value at Risk (VaR)** and **Expected Shortfall (ES)** using various statistical and econometric approaches.

## Data Source
The analysis is based on daily exchange rate data from **January 4, 2016, to October 10, 2025** (over 2,500 observations). The data was sourced from https://stooq.pl.

## Technologies
* **Language:** R / R Markdown

## Key Analyses
The project is structured into several core sections:

* **Exploratory Data Analysis:** Calculation of log-returns and descriptive statistics. The analysis highlights the presence of "fat tails" (kurtosis of 9.84) and the impact of significant global events like the COVID-19 pandemic and the war in Ukraine on currency volatility.
* **VaR & ES Estimation:** Implementation of five distinct methodologies for 99% VaR/ES estimation using a 250-day rolling window:
    * **Historical Simulation:** A non-parametric approach based on empirical distributions.
    * **Weighted Historical Simulation:** An extension using decay factors ($q=0.995$) to prioritize recent observations.
    * **Parametric EWMA:** Exponentially Weighted Moving Average to account for time-varying volatility.
    * **GARCH(1,1) Model:** Utilizing the `rugarch` package to capture conditional heteroskedasticity.
    * **Monte Carlo Simulation:** Simulating future returns based on the assumption of normality.
* **Statistical Backtesting:**
    * **Bernoulli Coverage Test:** Using the Binomial distribution to verify if the number of exceptions aligns with the 1% confidence level across different time horizons (100 and 250 days).
    * **Christoffersen Independence Test:** Evaluating whether VaR violations are independent or occur in clusters (volatility clustering).
* **Comparative Performance:** Analysis of how models performed during "calm" (2017–2019) vs. "volatile" (2020–2022) periods, highlighting that while parametric models (GARCH/EWMA) react faster to market shocks, the Monte Carlo method struggled due to its normality assumptions.

## Project Structure
* `Market-Risk-Analysis.Rmd` - The main R Markdown script containing the data processing, model implementations, and backtesting logic.
* `data/plnnok_d.csv` - The raw dataset of PLN/NOK daily exchange rates.
* `reports/Market-Risk-Analysis.html` - The compiled report featuring interactive-style formatting and visualizations of the results.
