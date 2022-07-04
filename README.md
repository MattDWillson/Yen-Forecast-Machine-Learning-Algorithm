## Time Series Basics 
Working with time series data requires a return to the basics. Data needs to be sliced and diced at various time frequencies in order to analyze data points as a time series. 

Pandas DateTimeIndex can be used to help with this = df.loc[2019

The Pandas resample function can be used to slice data once the date time index has been created,
weekly = df.['close'].resample('W').mean()

## Time Series Decomposition
Seperation of a time series into useful and less useful components. The useful components can be used to observe patterns and to make predictions. 

## Components of Times Series Decomposition
1) Level: What is the average value of the series?
2) Trend: Is there an overall direction of movement? 
3) Periodicity: Do patterns occur in cycles? 
4) Residual: How much noise exists in the data? 

# Exponentially Weighted Moving Average (EWMA) 
EWMA is an approach used to "denoise" or "smooth" out time series data so that trends and predictions can be made, 

1) EWMA involves calculating the average of the last n prices. 
2) Weights are added to the averages based on the recency of the data
  - Recent data is weighted more heavily 
  - Weighting decreases exponentially for previous prices / time periods 
3) Requires a past average values to be stored in memory 

EWMA is used to highlight trends and illustrate the price trajectory for an investment.

## Hodrick Prescott Filter (HP filter)
The HP filter is a mathematic function that seperates a time series into trend and non trend components by filtering out short-term fluctuations and decomposing a into noise and trend. 
<img width="1095" alt="Screen Shot 2022-07-04 at 1 42 06 PM" src="https://user-images.githubusercontent.com/83780964/177199873-260ab579-b716-4d81-803c-63efb01ca6d5.png">

## Autocorrelation
Autocorrelation is a measure of how closely current values correlate with past values. For example, autocorrelation is used to determine what extrent today's prices correlate with yesturday's prices. 

## Time Series Statistical Models: 

Stationarity: in a stationary process, the mean and variance are constant across time, adjust non stationary data to stationary using the pct_change() function. 

Non-Stationarity: A time series with an upward or downward trend. 

Stationarity is important in selecting a time series model because it makes data easier to model. 

## ARMA (Auto Regressive Moving Average) 
<img width="1115" alt="Screen Shot 2022-07-04 at 1 43 57 PM" src="https://user-images.githubusercontent.com/83780964/177200074-23c7d563-1b73-498c-ba9a-c65aa91da870.png">

## Autoregressive Models (AR) 
1) Past values are used to predict future values. 
2) Therefore assumes the same degree of autocorrelation. 
3) An ARMA model may have one significant lag, or it may have multiple. 

## Secondary AR Model 
<img width="1137" alt="Screen Shot 2022-07-04 at 1 43 20 PM" src="https://user-images.githubusercontent.com/83780964/177200019-456f95ce-1a98-40e8-94d1-9d1beb7a615e.png">

## AR Model Summary
An AR model predicts future values based on,
1) Past values at a specified lag.
2) The number of significant lags.

## Moving Average Models 
<img width="1093" alt="Screen Shot 2022-07-04 at 1 46 12 PM" src="https://user-images.githubusercontent.com/83780964/177200267-dccf7bab-b9d4-463e-bce5-c1e6ced6a044.png">
- Past errors (plus current errors) are used to predict future values. 

## ARMA Models
- combines features of AR and MA models 
- Past values and errors are used to predict future values 

## ARIMA Model 
<img width="961" alt="Screen Shot 2022-07-04 at 1 48 16 PM" src="https://user-images.githubusercontent.com/83780964/177200470-7167467c-a6c7-4884-83d6-423bc836bfab.png">

- Combines feautures of AR and MA models.
- Past values and errors are used to predict future values. 
- Arima creates differences (^Y) of the data as part of the process. 

## AIC (AIKaike Information Criterion) and BIC (Bayesian Information Criterion)
- Assess how well a model fits the data (goodness of fit), and complexity.
- Higher order models are penalized for complexity.
- Lower scores are better. 

## Diversified Portfolio
- Higher volatility = more risk
- Volatility = amount of variance across a time series
- By understanding the volatility of individual assets (stocks, bonds, etc) a more diversified portfolio can be constructed. 
- Some assets are particularly volatile e.g. derivatives.
- Volatility can beget volatility e.g. cluster. 

## Generalized Autoregressive Conditional Heteroskedacity (GARCH)
Garch models are used to predict volatility. Like ARMA, garch also has auto regressive and moving average components. 

Heteroskadicity means, "uneven variance".

<img width="600" alt="Screen Shot 2022-07-04 at 1 59 44 PM" src="https://user-images.githubusercontent.com/83780964/177201438-f2c9991a-dc00-4172-b5b7-100915a82bcc.png">

## Volatility and returns tend to cluster. GARCH is a model designed to take advantage of that: 
<img width="917" alt="Screen Shot 2022-07-04 at 2 01 07 PM" src="https://user-images.githubusercontent.com/83780964/177201578-8cfbc1cf-4480-43f2-8988-5e6e9b393e8a.png">

# Time Series Regression

## Multiple Regression 
<img width="1134" alt="Screen Shot 2022-07-04 at 2 06 11 PM" src="https://user-images.githubusercontent.com/83780964/177202044-26a1a02c-e4e1-46f0-a1ba-a583b884c863.png">
- Each day (X) is assigned its weight, or coefficient.

## Regression Metrics
<img width="652" alt="Screen Shot 2022-07-04 at 2 08 04 PM" src="https://user-images.githubusercontent.com/83780964/177202175-90bf0e2e-8349-4f6c-9cc3-605b1804b38c.png">

## Overfitting 
<img width="1146" alt="Screen Shot 2022-07-04 at 2 09 11 PM" src="https://user-images.githubusercontent.com/83780964/177202288-3cb71ef4-cd01-4711-b3c2-a1d45e2b562e.png">
- Overfit models learn the ‘noise’ found in the training data, rather than just 
the ‘signal’ 

## Variance Vs. Bias 
<img width="568" alt="Screen Shot 2022-07-04 at 2 10 47 PM" src="https://user-images.githubusercontent.com/83780964/177202415-63e61a2c-f4d4-4abb-b593-beac80a6e7e1.png">

## Parsimony 
- Statistical application of Occam’s razor: when two models perform similarly, choose the simpler one. Needlessly complex models are harder to compute and may lead to overfitting.

## Rolling Out of Sample Approach 
<img width="863" alt="Screen Shot 2022-07-04 at 2 12 29 PM" src="https://user-images.githubusercontent.com/83780964/177202538-2e94582e-fb1f-4431-88b0-6bb999a61f7a.png">

# JPY Vs. USD Exchange Rate Predictor
Tools / languages: JupyterLab, Python, Pandas, Numpy, Matplotlib, sklearn, arch, statsmodels

The algorithm uses time series forecasting and linear regression to determine if there is any predicatable behavior for USD-JPY exchange rate futures.

## Regression 
<img width="368" alt="Screen Shot 2021-08-04 at 1 40 17 PM" src="https://user-images.githubusercontent.com/83780964/128228525-13ed6848-aafc-4064-b952-ff47abe61dcc.png">

Out-of-Sample Root Mean Squared Error (RMSE): 0.4154832784856737

In-sample Root Mean Squared Error (RMSE): 0.5963660785073426

The out-of-sample RMSE is lower than the in-sample RMSE. RMSE is typically lower for training data, but is higher in this case. 

# Time Series - ARMA, ARIMA, GARCH
- Decomposed historical Dollar-Yen exchange rate futures data into noise and trend using the Hodrick Prescott Filter.
- Forecasted returns using an ARMA model.
- Forecasted settlement price using an ARIMA model.
- Forecasted volatility using a GARCH model.
- Determined that volatility and price were expected to increase.

## Settle Vs. Trend

<img width="1072" alt="Screen Shot 2021-08-04 at 1 35 17 PM" src="https://user-images.githubusercontent.com/83780964/128227900-1c50aa8f-cb94-4f44-ad90-ef4f6d572d94.png"

## ARMA Model - 5 Day Returns Forecast
<img width="374" alt="Screen Shot 2021-08-04 at 1 35 47 PM" src="https://user-images.githubusercontent.com/83780964/128228051-75319dd5-0d95-4666-901f-e8581582dd7a.png">

## ARIMA Model - 5 Day Settle Price Forecast
<img width="351" alt="Screen Shot 2021-08-04 at 1 38 37 PM" src="https://user-images.githubusercontent.com/83780964/128228215-770a9be6-3136-4761-a5cd-af3a30cb7add.png">

## Garch Model - 5 Day Volatility Forecast 
<img width="359" alt="Screen Shot 2021-08-04 at 1 39 31 PM" src="https://user-images.githubusercontent.com/83780964/128228315-6b3bcb98-5a5c-41c5-90ae-b196215381b7.png">

## Conclusion:
The models show that volatility and price will increase in the next 5 days. I would feel confident using the Garch volatility model for trading because the P values are lower than .05 which signifies that it is a good model. However, both the price and returns models have high p values which signifies that they are bad models. Volatility = opportunity so one could profit if they had a better model to predict the short term trajectory of the Yen.

