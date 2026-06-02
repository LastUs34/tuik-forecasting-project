# TÜu130K Forecasting Project

## 1. Project Overview

This project forecasts the total number of monthly births in Turkey using time series data obtained directly from the TÜu130K Data Portal via the `tuikr` R package. Ten forecasting methods are applied, compared, and the superior method is selected to produce a forecast for January 2026.

## 2. Data Source and TÜu130K Connection

- **TÜu130K data set name:** Births by sex and month, 2001-2025
- **TÜu130K theme/category:** Population and Demography (Theme 11)
- **TÜu130K table name:** Births by sex and month, 2001-2025
- **tuikr Dataflow ID:** NA — istab table accessed via tuikr::statistical_tables("11")
- **Selected variable:** Total monthly births (Toplam-Total)
- **Data frequency:** Monthly
- **Time coverage:** January 2001 - December 2025
- **Latest available observation:** December 2025
- **Forecast target period:** January 2026
- **Date of data access:** June 2026
- **Package source:** https://github.com/emraher/tuikr

## 3. Research Objective

This project forecasts the total number of births in Turkey for January 2026. Monthly birth statistics reflect demographic trends and fertility rates, making them a meaningful variable for forecasting.

## 4. Use of TÜu130K Data in R

Data were accessed directly from TÜu130K using tuikr::statistical_tables("11"). No manually prepared, edited, or newly created dataset was used. R-based cleaning included: year column filled down, wide-to-long transformation, numeric conversion.

## 5. Exploratory Time Series Analysis

- **Trend:** Clear downward trend since approximately 2015
- **Seasonality:** Strong monthly pattern — births peak in July-August, lowest in December-February
- **Missing values:** None
- **Outliers:** Slight dip in 2020-2021 (COVID-19 effect)

## 6. Forecasting Methods Applied

- Naive Forecasting
- Moving Average (12-month window)
- Weighted Moving Average (weights: 0.5, 0.3, 0.2)
- Exponential Smoothing (alpha = 0.3)
- Trend-Adjusted Exponential Smoothing (alpha = 0.3, beta = 0.1)
- Linear Trend Projection
- Seasonal Indices (ratio-to-moving-average)
- Additive Decomposition
- Multiplicative Decomposition
- Regression with Trend and Seasonal Dummy Variables

## 7. Forecast Accuracy Comparison

All methods compared using: Bias, MAD, MSE, MAPE, RSFE, Tracking Signal. Full table in outputs/tables/accuracy_comparison.csv.

## 8. Selection of the Superior Method

**Superior method: Regression with Trend and Seasonal Dummy Variables**

The series has a clear downward trend and strong monthly seasonality. Regression with dummies explicitly models both components, achieves low MAPE, and shows no systematic bias.

## 9. Final Next-Period Forecast

- **Superior method:** Regression with Trend and Seasonal Dummy Variables
- **Date of data access:** June 2026
- **Latest available TÜu130K observation:** December 2025
- **Forecast target period:** January 2026
- **Forecasted value:** See outputs/tables/final_forecast.csv

## 10. Interpretation of Results

Turkey birth rate has been declining since 2015. January is historically one of the lowest months for births. The forecast reflects both the ongoing downward trend and the typical January seasonal dip.

## 11. Limitations

- Model assumes historical trend and seasonality continue into 2026
- Economic shocks or policy changes could alter the pattern
- Data revisions by TÜu130K may affect results

## 12. Reproducibility

Install R 4.3.3+ and RStudio. Install packages: pak::pak("emraher/tuikr") and install.packages(c("httr","readxl","dplyr","tidyr","ggplot2","knitr","scales")). Clone repository: git clone https://github.com/LastUs34/tuik-forecasting-project. Open forecasting_project.Rmd and click Knit.

## 13. Repository Structure

tuik-forecasting-project/
- README.md
- forecasting_project.Rmd
- forecasting_project.html
- outputs/tables/accuracy_comparison.csv
- outputs/tables/final_forecast.csv
- outputs/figures/ (all method plots)

## 14. Author

- **Student name:** Omer Faruk Donmez
- **Student number:** 138723504
- **Course name:** Forecasting Methods

