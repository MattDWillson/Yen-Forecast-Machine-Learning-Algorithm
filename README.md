# Yen Vs. U.S. Dollar Exchange Rate Predictor
 Tools / languages: JupyterLab, Python, Pandas, Numpy, Matplotlib, sklearn, arch, statsmodels, time series forecasting, linear regression modeling
 
## Overview 
- Uses time series forecasting and linear regression modeling to determine whether there is any predictable behavior for Dollar-Yen exchange rate futures
- Decomposed historical Dollar-Yen exchange rate futures data into noise and trend using the Hodrick Prescott Filter
- Forecasted returns using an ARMA model
- Forecasted settlement price using an ARIMA model
- Forecasted volatility using a GARCH model
- Determined that volatility and price were expected to increase

# Time Series
## Settle Price Vs. Trend
<img width="1072" alt="Screen Shot 2021-08-04 at 1 35 17 PM" src="https://user-images.githubusercontent.com/83780964/128227900-1c50aa8f-cb94-4f44-ad90-ef4f6d572d94.png">

## Noise 
<img width="1055" alt="Screen Shot 2021-08-04 at 1 35 30 PM" src="https://user-images.githubusercontent.com/83780964/128227973-59bf88de-c892-4734-9d34-d51e58be1a98.png">

## ARMA Model - 5 Day Returns Forecast
<img width="374" alt="Screen Shot 2021-08-04 at 1 35 47 PM" src="https://user-images.githubusercontent.com/83780964/128228051-75319dd5-0d95-4666-901f-e8581582dd7a.png">

## ARIMA Model - 5 Day Settle Price Forecast
<img width="351" alt="Screen Shot 2021-08-04 at 1 38 37 PM" src="https://user-images.githubusercontent.com/83780964/128228215-770a9be6-3136-4761-a5cd-af3a30cb7add.png">

## Garch Model - 5 Day Volatility Forecast 
<img width="359" alt="Screen Shot 2021-08-04 at 1 39 31 PM" src="https://user-images.githubusercontent.com/83780964/128228315-6b3bcb98-5a5c-41c5-90ae-b196215381b7.png">

## Time Series Conclusion:
Based on the time series analysis I would not buy the yen now. The models show that volatility will increase in the next 5 days. I would feel confident using the Garch volatility model for trading because the P values are lower than .05 which signifies that it is a good model. However, both the price and returns models have high p values which signifies that they are bad models. Volatility = opportunity so one could profit if they had a better model to predict the short term trajectory of the Yen.

# Regression
## Return Vs. Predicted Returns
<img width="368" alt="Screen Shot 2021-08-04 at 1 40 17 PM" src="https://user-images.githubusercontent.com/83780964/128228525-13ed6848-aafc-4064-b952-ff47abe61dcc.png">

## Regression Analysis:
## In Sample Vs. Out of Sample RMSE
Out-of-Sample Root Mean Squared Error (RMSE): 0.4154832784856737
In-sample Root Mean Squared Error (RMSE): 0.5963660785073426
In conclusion, the out-of-sample RMSE is lower than the in-sample RMSE. RMSE is typically lower for training data, but is higher in this case. 
