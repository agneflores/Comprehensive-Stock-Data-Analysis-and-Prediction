# Comprehensive-Stock-Data-Analysis-and-Prediction

## Project Overview:
This analysis investigated the effectiveness of various machine learning models in predicting stock closing prices, using Palo Alto Networks (PANW) as a case study with 5 years of historical data.

## Research Question:
"Can machine learning models accurately predict stock closing prices, and which model provides the most reliable predictions?"

## Methodology:
Tested four distinct modeling approaches:

LSTM (Deep Learning)
XGBoost (Gradient Boosting)
Linear Regression
Prophet (Time Series)

Key Findings:

Best Performing Model: LSTM

R² Score: 0.64
Demonstrated superior ability to capture complex price patterns
Better at handling temporal dependencies


Other Model Performance:

Linear Regression: Initial R² of 0.99 revealed data leakage issues
Corrected Linear Regression: R² ≈ 0.45-0.55
XGBoost: R² ≈ 0.50-0.65
Prophet: R² ≈ 0.45-0.60
