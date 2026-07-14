Time Series Forecasting of Exchange Rates (PKR/USD)

Among the various forecasting techniques, the Seasonal AutoRegressive Integrated Moving Average with eXogenous variables (SARIMAX) model is one of the most comprehensive and flexible approaches. It extends the traditional ARIMA model by incorporating both seasonality and external (exogenous) variables, enabling more accurate forecasts for datasets exhibiting recurring seasonal patterns and being influenced by external factors.
________________________________________
The SARIMAX Model

SARIMAX stands for:

	S – Seasonal 
  
	AR – AutoRegressive 
  
	I – Integrated 
  
	MA – Moving Average 
  
	X – Exogenous Variables 
  
The model combines four important characteristics:

	Trend modeling 
  
	Seasonal pattern modeling 
  
	Autocorrelation among observations 
  
	Influence of external explanatory variables 
  
This makes SARIMAX particularly suitable for real-world forecasting problems where both seasonal fluctuations and external influences exist.
________________________________________
Mathematical Representation

The SARIMAX model is represented as

SARIMAX(p,d,q)(P,D,Q)_s

where

Non-seasonal parameters

	p = Order of autoregression (AR) 
  
	d = Degree of differencing 
  
	q = Order of moving average (MA) 
  
Seasonal parameters

	P = Seasonal autoregressive order 
  
	D = Seasonal differencing order 
  
	Q = Seasonal moving average order 
  
	s = Length of seasonal cycle 
  
For example,

SARIMAX(2,1,1)(1,1,1)_12

indicates

	AR order = 2 
  
	First differencing
  
	MA order = 1 
  
	Seasonal AR = 1 
  
	Seasonal differencing = 1
  
	Seasonal MA = 1 
  
	Seasonality every 12 periods (monthly data) 
________________________________________
Components of SARIMAX

1. Autoregressive (AR)
   
The autoregressive component assumes that the current value depends on previous observations.

Y_t=c+ϕ_1 Y_(t-1)+ϕ_2 Y_(t-2)+...+ϵ_t

This captures persistence in the series.
________________________________________
2. Integrated (I)
   
Differencing removes non-stationarity from the data.

First-order differencing is

Y_t^'=Y_t-Y_(t-1)

Seasonal differencing is

Y_t^'=Y_t-Y_(t-s)

where s is the seasonal period.
________________________________________
3. Moving Average (MA)
   
The moving average component models dependence on previous forecasting errors.

Y_t=μ+ϵ_t+θ_1 ϵ_(t-1)+θ_2 ϵ_(t-2)

________________________________________
4. Seasonal Component
   
Seasonality captures repeated patterns occurring at fixed intervals 
	
________________________________________
5. Exogenous Variables (X)

Unlike SARIMA, SARIMAX allows additional explanatory variables to influence the dependent variable.
 
The forecasting equation becomes

Y_t=f(ARIMA)+βX_t+ϵ_t

where

	X_t represents external variables
  
	β measures their influence. 
________________________________________
Assumptions of SARIMAX

The SARIMAX model assumes that:

	The series becomes stationary after appropriate differencing. 
  
	Residuals are independently distributed. 
  
	Residuals have constant variance. 
  
	Residuals are approximately normally distributed. 
  
	Exogenous variables are measured accurately and are available for both model fitting and forecasting. 
  
	Seasonal patterns remain relatively stable over time. 
  
________________________________________

Objective

The objective of this study is to model and forecast the monthly exchange rate (PKR/USD) using the Seasonal Autoregressive Integrated Moving Average (SARIMA) model. The study also evaluates the model's adequacy through diagnostic tests and forecasting accuracy measures.
___________________________________________
Data Description

Variable: Exchange Rate (PKR/USD)

Frequency: Monthly 

Period: January 2000 – June 2026 

Number of Observations: 318 
____________________________________________

Methodology

The analysis follows the  SARIMA modeling.
____________________________________________
Steps in Time Series Modeling Using SARIMAX

Step 1: Data Collection

Collect observations arranged chronologically.
________________________________________
Step 2: Data Visualization

Plot the series to identify

	Trend 
  
	Seasonality 
  
	Cycles
  
	Outliers
  
Visualization provides preliminary insights into the data structure.
________________________________________
Step 3: Data Preprocessing

Preprocessing may involve

	Converting dates into DateTime format 
  
	Setting the time index 
________________________________________
Step 4: Train-Test Split

Unlike random sampling, time series data are divided chronologically.

Example

	Training data: 80% 
  
	Testing data: 20% 
  
This preserves the temporal order of observations.
________________________________________
Step 5: Stationarity Testing

Stationarity is assessed using

	Augmented Dickey-Fuller (ADF) Test 
  
If the series is non-stationary, differencing is applied until stationarity is achieved.
________________________________________
Step 6: Seasonal Analysis

Seasonality is examined through

	Seasonal decomposition
  
	Seasonal plots 
  
	Autocorrelation patterns 
  
The seasonal period (s) is identified based on the data frequency (e.g., 12 for monthly data, 4 for quarterly data).
________________________________________
Step 7: Identification of Model Orders

Model parameters are selected using

	ACF plot 
  
	PACF plot 
  
	Information criteria such as AIC and BIC 
  
	Grid search or automated model selection 
  
Orders include

	(p,d,q) 
  
	(P,D,Q,s) 
________________________________________
Step 8: Model Estimation

The SARIMAX model is estimated using Maximum Likelihood Estimation (MLE).

Both seasonal and non-seasonal parameters are estimated simultaneously, along with coefficients for exogenous variables if included.
________________________________________
Step 9: Diagnostic Checking

Model adequacy is evaluated using

Residual Analysis

Residuals should resemble white noise.

Ljung-Box Test

Tests for autocorrelation in residuals.

Jarque-Bera Test

Evaluates residual normality.

Heteroscedasticity Test

Checks whether residual variance remains constant.

A satisfactory model has residuals that are approximately independent, normally distributed, and homoscedastic.
________________________________________
Step 10: Forecasting

Once validated, the model generates forecasts for future periods. If exogenous variables are part of the model, their future values (or forecasts of them) must also be supplied for the forecast horizon.

Forecasts are typically presented with:

	Point forecasts 
  
	Confidence intervals (e.g., 95%) 
  
	Prediction plots comparing observed and forecasted values 
________________________________________
Model Evaluation

Forecast accuracy is commonly assessed using:

	Mean Absolute Error (MAE): Average absolute difference between observed and predicted values. 
  
	Mean Squared Error (MSE): Average squared forecast error. 
  
	Root Mean Squared Error (RMSE): Square root of MSE, expressed in the original units. 
  
	Mean Absolute Percentage Error (MAPE): Average percentage error, useful for comparing performance across datasets. 
  
Lower values of these metrics indicate better predictive performance.
________________________________________
Advantages of SARIMAX

	Captures both trend and seasonality. 
  
	Incorporates exogenous variables, improving explanatory power. 
  
	Suitable for economic, financial, environmental, and business forecasting. 
  
	Produces statistically interpretable parameter estimates. 
  
	Often yields higher forecasting accuracy than ARIMA when seasonal effects or external drivers are present. 
________________________________________
Limitations of SARIMAX

	Requires stationary data after differencing. 
  
	Model identification can be time-consuming. 
  
	Performance depends on accurate specification of seasonal parameters.
  
	Forecasting with exogenous variables requires future values of those variables. 
  
	Less effective for highly nonlinear relationships compared with some machine learning and deep learning models. 
 
________________________________________
Conclusion
The SARIMAX model is a robust and versatile extension of the ARIMA framework that effectively captures trend, seasonality, and the influence of external variables. By integrating autoregressive, differencing, moving average, seasonal, and exogenous components into a single framework, SARIMAX provides a comprehensive approach to forecasting complex time series. Successful implementation requires careful data preprocessing, stationarity testing, appropriate selection of model orders, thorough diagnostic checking, and evaluation using standard forecast accuracy metrics. When these steps are followed, SARIMAX serves as a powerful tool for generating reliable forecasts and supporting evidence-based decision-making across a wide range of disciplines.

