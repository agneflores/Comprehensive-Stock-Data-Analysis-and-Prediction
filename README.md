# Comprehensive-Stock-Data-Analysis-and-Prediction

## Project Overview:
This analysis investigated the effectiveness of various machine learning models in predicting stock closing prices, using Palo Alto Networks (PANW) as a case study with 5 years of historical data.

## Research Question:
"Can machine learning models accurately predict stock closing prices, and which model provides the most reliable predictions?"

## Methodology:
Exploratory and Historical Analysis


Model Selection 
LSTM (Deep Learning)
XGBoost (Gradient Boosting)
Linear Regression
Prophet (Time Series)



-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Exploratory Analysis

### Data Overview

<img width="800" alt="image" src="https://github.com/user-attachments/assets/0bba97b4-0843-4a3d-8a1c-9c7478e811aa">

### Correlation Analysis

<img width="600" alt="image" src="https://github.com/user-attachments/assets/9339aedf-c2e5-47fc-b113-ac41f43d961f">

The correlation matrix reveals several key insights about the relationships between different stock features:

#### Price Variables Correlation:


Very strong correlation (1.0) between Open, High, Low, and Close prices. This high correlation suggests these price metrics move very closely together, which is expected in daily stock data


#### Volume Relationships:


Very weak correlation (near 0) between volume and price metrics
Values range from -0.0059 to 0.0087 with price features
This suggests trading volume moves independently of price levels


#### Stock Splits and Dividends:


Very weak correlation with all other features (all values near 0)
This makes sense as PANW is a growth stock that typically doesn't pay dividends
Shows corporate actions are independent of daily trading patterns

This correlation analysis helps explain why our models need to consider multiple features despite their high correlations, and why volume might be a valuable independent predictor.


## Comprehensive Historical Analysis 

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/11f35c74-6339-4aeb-b99f-b27bdc889c9f">

Looking at the historical price chart of Palo Alto Networks (PANW) from 2020 to early 2025, several key observations make this analysis particularly important:

### Growth and Volatility:


The stock has shown significant growth, rising from around $75 in 2020 to over $350 in 2024

Notable volatility, especially in recent periods (2024) with price swings between $250-$370

Sharp decline during early 2020 (likely due to COVID-19) followed by strong recovery


### Market Evolution:


Clear trend shifts between periods of steady growth and consolidation

Multiple significant price level breakouts, particularly in 2023-2024

Increasing price volatility as the stock reaches higher levels

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/3e105fa3-9674-4698-9633-8a6a58525a20">

Trading volume is a crucial indicator in stock analysis for several important reasons:


### Price Validation & Trends


High volume on price increases suggests strong buying pressure and trend confirmation

High volume on price drops indicates strong selling pressure

Low volume during price moves may indicate less reliable trends


### Market Interest & Liquidity


Higher volume means easier to buy/sell without affecting price significantly

Sudden volume spikes can signal major events or changing market sentiment

Low volume could mean harder to exit positions without price impact


### Technical Analysis Uses


Volume often precedes price movements

Divergences between price and volume can signal potential trend reversal

Common patterns like "volume climax" can help predict market tops/bottoms


### Institutional Activity


Large volume spikes may indicate institutional investors (big funds) entering/exiting

Unusually high volume could signal upcoming news or leaked information

Consistent high volume suggests sustained institutional interest


### Market Psychology


Rising prices with rising volume suggests strong buyer conviction

Falling prices with rising volume indicates strong seller conviction

Volume can help confirm breakouts from trading ranges

### PANW Summary
The volume patterns provide crucial context for our prediction models, as high-volume periods often signal important price movements and potential trend changes. The increasing frequency of volume spikes in recent periods suggests growing market participation and potentially more challenging conditions for price prediction.

<img width="900" alt="image" src="https://github.com/user-attachments/assets/9bfa074f-9b0d-4512-ab78-873e271ab7f2">
<img width="900" alt="image" src="https://github.com/user-attachments/assets/9dce2719-482d-4b1f-bcf1-a46626ae385e">





