# Comprehensive-Stock-Data-Analysis-and-Prediction

## Project Overview:
This analysis investigated the effectiveness of various machine learning models in predicting stock closing prices, using Palo Alto Networks (PANW) as a case study with 5 years of historical data.

## Research Question:
"Can machine learning models accurately predict stock closing prices, and which model provides the most reliable predictions?"

## Methodology:

#### Exploratory and Historical Analysis
#### Model Selection 

Linear Regression

LSTM (Deep Learning)

Prophet (Time Series)

XGBoost (Gradient Boosting)




-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Exploratory Analysis

### Data Overview

<img width="800" alt="image" src="https://github.com/user-attachments/assets/0bba97b4-0843-4a3d-8a1c-9c7478e811aa">

### Correlation Analysis

<img width="600" alt="image" src="https://github.com/user-attachments/assets/9339aedf-c2e5-47fc-b113-ac41f43d961f">

The correlation matrix reveals several key insights about the relationships between different stock features:

#### Price Variables Correlation:


Very strong correlation (1.0) between Open, High, Low, and Close prices. This high correlation suggests these price metrics move very closely together, which is expected in daily stock data.


#### Volume Relationships:


Very weak correlation (near 0) between volume and price metrics. Values range from -0.0059 to 0.0087 with price features. This suggests trading volume moves independently of price levels.


#### Stock Splits and Dividends:


Very weak correlation with all other features (all values near 0). This makes sense as PANW is a growth stock that typically doesn't pay dividends. Shows corporate actions are independent of daily trading patterns

This correlation analysis helps explain why our models need to consider multiple features despite their high correlations, and why volume might be a valuable independent predictor.


## Comprehensive Historical Analysis 

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/11f35c74-6339-4aeb-b99f-b27bdc889c9f">

Looking at the historical price chart of Palo Alto Networks (PANW) from 2020 to early 2025, several key observations make this analysis particularly important:

#### Growth and Volatility:


The stock has shown significant growth, rising from around $75 in 2020 to over $350 in 2024

Notable volatility, especially in recent periods (2024) with price swings between $250-$370

Sharp decline during early 2020 (likely due to COVID-19) followed by strong recovery


#### Market Evolution:


Clear trend shifts between periods of steady growth and consolidation

Multiple significant price level breakouts, particularly in 2023-2024

Increasing price volatility as the stock reaches higher levels

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/3e105fa3-9674-4698-9633-8a6a58525a20">

Trading volume is a crucial indicator in stock analysis for several important reasons:


#### Price Validation & Trends


High volume on price increases suggests strong buying pressure and trend confirmation

High volume on price drops indicates strong selling pressure

Low volume during price moves may indicate less reliable trends


#### Market Interest & Liquidity


Higher volume means easier to buy/sell without affecting price significantly

Sudden volume spikes can signal major events or changing market sentiment

Low volume could mean harder to exit positions without price impact


#### Technical Analysis Uses


Volume often precedes price movements

Divergences between price and volume can signal potential trend reversal

Common patterns like "volume climax" can help predict market tops/bottoms


#### Institutional Activity


Large volume spikes may indicate institutional investors (big funds) entering/exiting

Unusually high volume could signal upcoming news or leaked information

Consistent high volume suggests sustained institutional interest


#### Market Psychology


Rising prices with rising volume suggests strong buyer conviction

Falling prices with rising volume indicates strong seller conviction

Volume can help confirm breakouts from trading ranges

### PANW Summary
The volume patterns provide crucial context for our prediction models, as high-volume periods often signal important price movements and potential trend changes. The increasing frequency of volume spikes in recent periods suggests growing market participation and potentially more challenging conditions for price prediction.

<img width="900" alt="image" src="https://github.com/user-attachments/assets/9bfa074f-9b0d-4512-ab78-873e271ab7f2">
<img width="900" alt="image" src="https://github.com/user-attachments/assets/9dce2719-482d-4b1f-bcf1-a46626ae385e">

The two images together provide a comprehensive view of PANW's price and volume trends:
Price Analysis (Image 1):

Strong upward trend from $50 (2020) to $350+ (2025)
Moving averages (20-day and 50-day) show clear trend confirmation
Notable consolidation period during 2022-2023 around $150-$200
Accelerated growth phase from 2023 onwards
Increased volatility in recent periods (2024)

Volume Analysis (Image 2):

Base trading volume represented by 20-day MA (black line)
Several major volume spikes throughout the period
Highest spike in late 2023 (>50M shares)
Recent volume pattern shows increased activity
Volume spikes often coincide with price movement changes

Key Relationships:

Higher volume often accompanies significant price movements
Moving averages help identify trend changes
Recent period (2023-2024) shows both higher prices and more frequent volume spikes
Market interest (indicated by volume) has increased with price appreciation

# Model Selection

#### Realistic Performance Expectations:


LSTM: R² ~ 0.60-0.70

XGBoost: R² ~ 0.50-0.65

Linear Regression: R² ~ 0.40-0.55

Prophet: R² ~ 0.45-0.60

## Linear Regression

### Key Parameters:

Features: Open, High, Low, Volume

Target: Close price

80-20 train-test split

<img width="766" alt="image" src="https://github.com/user-attachments/assets/e1892806-2f7a-4b9d-9f39-ee475240632e">

<img width="512" alt="image" src="https://github.com/user-attachments/assets/2c269f8b-2f39-4170-b269-a056db893881">

### Performance Metrics:

R² Score: 0.99

RMSE: 1.7

Very high R² suggests potential overfitting
Low RMSE indicates small prediction errors
Results suggest need for model refinement

I can see the issue causing the overfitting in my Linear Regression model. The main problem is data leakage due to using same-day price data.
The issue is that 'High' and 'Low' prices are from the same day as the 'Close' price we're trying to predict. This means we're using information that wouldn't be available at prediction time, leading to artificially high R² scores.

## Linear Regression with Previous Day's Data
### Key improvements:

Only uses previous day's data

Adds meaningful technical indicators

Maintains chronological order

Includes proper error analysis

Shows feature importance

### Features now include:

Previous day's prices

Previous day's volume

Previous day's price changes

Moving averages (calculated properly)

Previous returns

### Additional analysis:

Feature coefficients

Error analysis

Multiple visualizations

Detailed performance metrics

### Performance Metrics:

R² Score: 0.8990
RMSE: $9.42
MAE: $5.48

<img width="763" alt="image" src="https://github.com/user-attachments/assets/e2554a5d-c12b-41ba-9f20-5d048230cabf">

<img width="508" alt="image" src="https://github.com/user-attachments/assets/401c2bee-a8d7-4054-b88c-7a47eab1caa2">

<img width="760" alt="image" src="https://github.com/user-attachments/assets/5b200edb-4ce5-41fd-83f7-eed9c954d1da">

Error Statistics:
Mean Error: $0.52
Error Std Dev: $9.42
Max Overprediction: $-104.98
Max Underprediction: $23.95

This error plot provides several important insights about the Linear Regression model's performance:

Error Distribution:


Most errors fluctuate between +20 and -20 dollars
Generally symmetric around zero (blue dashed line)
Shows relatively consistent volatility except for one major outlier


Notable Issues:


Large outlier spike around March 2024 (approximately -100 dollar error)
This could indicate:

A significant market event
Earnings announcement
Other unexpected news affecting the stock price




Pattern Analysis:


Error magnitude appears relatively stable over time
No clear trend in errors (good)
Random distribution around zero suggests unbiased predictions
Consistent error band width suggests stable model performance


Areas for Improvement:


Model struggles with sudden large price movements
Could benefit from:

Outlier handling
Additional features to capture market events
Rolling window training to adapt to changing conditions

## Prophet Model

Key components:

Data preparation specific to Prophet requirements
Model configuration with seasonality parameters
Forecast visualization with confidence intervals
Component analysis
Performance metrics calculation

The Prophet model features:

Daily, weekly, and yearly seasonality
Automatic changepoint detection
Confidence intervals
Trend decomposition

<img width="515" alt="image" src="https://github.com/user-attachments/assets/daed6fd6-1555-43a7-86bb-36522ec95c8e">

<img width="454" alt="image" src="https://github.com/user-attachments/assets/085c8666-3904-4caa-b4da-24df56c60cd1">

<img width="443" alt="image" src="https://github.com/user-attachments/assets/9def9614-900e-4198-9c3c-6249aa2c03a2">

<img width="451" alt="image" src="https://github.com/user-attachments/assets/ef83bbc9-53bf-4ca7-84db-34d1a5c3ed1d">

Model Performance Metrics:
RMSE: $14.08
MAE: $10.67
R² Score: 0.9717

Next 5 Days Forecast:
           Date  Predicted Price  Lower Bound  Upper Bound
1190 2024-11-05       354.867437   337.175962   373.194015
1191 2024-11-06       354.691919   336.597743   371.799442
1192 2024-11-07       355.147516   334.587008   372.889406
1193 2024-11-08       355.956970   336.955457   372.926920
1194 2024-11-09       359.476836   342.163642   378.385061

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## LSTM Model
Key components:

Data preparation specific to LSTM:

Sequence creation
Scaling
Train/test split


LSTM Architecture:

Two LSTM layers
Dropout for regularization
Dense output layer


Visualization:

Training history
Predictions vs actual values


Future predictions:

Rolling window approach
30-day forecast

<img width="543" alt="image" src="https://github.com/user-attachments/assets/4e2b6bee-fa62-4f26-ae0e-99c07e6ef407">


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

XGBoost Model

Key components:

Feature Engineering:

Technical indicators
Moving averages
Price momentum
Volatility measures
Lagged features


Model Configuration:

Gradient boosting parameters
Feature importance analysis
Proper train/test split


Visualization:

Price predictions
Feature importance
Historical comparison


Future Predictions:

5-day forecast
Feature updates for sequential predictions
<img width="547" alt="image" src="https://github.com/user-attachments/assets/6e3d2102-326e-463f-a112-85d2787a9e58">

<img width="514" alt="image" src="https://github.com/user-attachments/assets/f22b73c7-97dd-479c-ae61-b4444307c7fc">

Model Performance Metrics:
RMSE: $47.80
MAE: $39.01
R² Score: -1.6644

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Stock Price Prediction Model Review and Comparison
Performance Analysis:

Model Rankings (by R² Score):

Prophet: 0.9717 (Highest)
Linear Regression: 0.8990
LSTM: 0.7416
XGBoost: -1.6644 (Significant underperformance)

Key Observations:

Unexpected Results:

Prophet and Linear Regression outperformed more complex models
XGBoost significantly underperformed despite its typical strength in financial data
LSTM performed within expected range (R² 0.60-0.70)


Model-Specific Insights:

Linear Regression: Shows surprisingly good performance with simple previous day's data
Prophet: Excels at capturing seasonal patterns and trends
LSTM: Demonstrates reliable performance consistent with expectations
XGBoost: Requires significant optimization and feature engineering



Improvement Suggestions:

XGBoost Model:

Implement feature selection
Tune hyperparameters
Add more relevant technical indicators
Consider different time windows for features


LSTM Model:

Experiment with network architecture
Add attention mechanisms
Include more sequence length variations
Implement batch normalization


General Improvements:

Add market sentiment analysis
Include sector-specific indicators
Implement ensemble methods
Add outlier detection and handling



Recommendations:

Short-term: Use Linear Regression or Prophet for quick, reliable predictions
Long-term: Develop ensemble approach combining multiple models
Research: Investigate XGBoost's underperformance
Production: Consider Prophet for deployment due to balance of performance and simplicity

Future Work:

Develop hybrid models
Include external data sources
Implement real-time prediction capabilities
Add confidence intervals for all models
Create automated model selection based on market conditions



