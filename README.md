# **THE DENARII TRADER: - A daytrader trying to make a “day's wage” from a desktop brain!!**

![MLSP](https://user-images.githubusercontent.com/78338890/121461642-40314d80-c97d-11eb-9045-43d68de8d24b.jpg)

## *OVERVIEW*

Machine learning is a subset of artificial intelligence involved with the creation of algorithms that can change itself without human intervention to produce an output by feeding itself through structured data. In this project, we created a model that makes a 7-day prediction for a particular stock/ticker using different machine learning models.We were able to extract data from Yahoo Finance and run it through our prepared model to get the predictions that help us make buying and selling decisions on our stocks.

## *DATASET AND FEATURES*

The first step is to intitialize imports and prepare the data. We load the dataset and calculate the indicators- RSI, MACD and CMF. The dataset was downloaded from the YahooFinance. 

#### *Initial imports*

<img width="641" alt="Screen Shot 2021-06-14 at 22 42 44" src="https://user-images.githubusercontent.com/78338890/121984985-ef956800-cd61-11eb-9645-66f6bded26d1.png">

<img width="280" alt="Screen Shot 2021-06-14 at 22 42 59" src="https://user-images.githubusercontent.com/78338890/121985006-f6bc7600-cd61-11eb-95ff-7505b456fdf6.png">



#### *Identifying the ticker we want to analyze (in our case, AAPL) and importing data from Yahoo Finance*

<img width="492" alt="Screen Shot 2021-06-14 at 22 44 37" src="https://user-images.githubusercontent.com/78338890/121985127-24a1ba80-cd62-11eb-9462-1de8237c065c.png">



#### *Calculating and adding Indicators- RSI, MACD, CMF and Bollinger band signals to create our dataframe df* 

- RSI indicator (Relative Strength Index) is an indicator that we can use to measure if given asset is priced to high or too low. It is intended to chart the current and historical strength or weakness of a stock or market based on the closing prices of a recent trading period.

- MACD indicator stands for Moving Average Convergence Divergence. As the name suggests, indicator is evaluating two moving averages and the relation between them. It is calculated by subtracting the 26-period exponential moving average (EMA) from the 12-period EMA.

- Chaikin Money Flow (CMF) is a technical analysis indicator used to measure Money Flow Volume over a set period of time. Money Flow Volume (a concept also created by Marc Chaikin) is a metric used to measure the buying and selling pressure of a security for single period.


<img width="1274" alt="Screen Shot 2021-06-14 at 22 46 34" src="https://user-images.githubusercontent.com/78338890/121985250-6894bf80-cd62-11eb-9dac-75de637170b7.png">


##### *Plotting of the three indicators*

<img width="777" alt="Screen Shot 2021-06-14 at 22 47 46" src="https://user-images.githubusercontent.com/78338890/121985391-a8f43d80-cd62-11eb-8b92-b2066a61561f.png">

<img width="766" alt="Screen Shot 2021-06-14 at 22 48 01" src="https://user-images.githubusercontent.com/78338890/121985408-af82b500-cd62-11eb-9e38-892a2e52237b.png">

##### *Cleaning dataframe and saving as a csv*

<img width="1006" alt="Screen Shot 2021-06-14 at 22 49 25" src="https://user-images.githubusercontent.com/78338890/121985508-dc36cc80-cd62-11eb-98b3-65618eadc0f6.png">


## *TRAINING MODELS*

### *MODEL 1- Forecasting stock prices using LSTM*

- Set Index Date as string type
- Select features from the dataset that are to be used for training and predicting. In our case, Columns 0 to 5
- Create array for LSTM model to run
<img width="364" alt="Screen Shot 2021-06-14 at 22 58 37" src="https://user-images.githubusercontent.com/78338890/121986184-16ed3480-cd64-11eb-974a-3c174d7c4c6b.png">

- Scale the features and create a datastructure with 90 timestamps and 1 output
- Now, initialize the LSTM based Neural Network
<img width="550" alt="Screen Shot 2021-06-14 at 22 59 39" src="https://user-images.githubusercontent.com/78338890/121986499-9a0e8a80-cd64-11eb-9d4a-e3692966906e.png">

- Start training
<img width="827" alt="Screen Shot 2021-06-14 at 23 03 56" src="https://user-images.githubusercontent.com/78338890/121986706-01c4d580-cd65-11eb-8aa3-97209e37b3bd.png">

- Generate list of sequence of days for predictions
- Convert Pandas Timestamp to Datetime object
- Perform predictions 
<img width="768" alt="Screen Shot 2021-06-14 at 23 45 31" src="https://user-images.githubusercontent.com/78338890/121989792-b4e3fd80-cd6a-11eb-9ca7-4d290073a892.png">

- Plotting predicted stock price
<img width="1011" alt="Screen Shot 2021-06-14 at 23 48 40" src="https://user-images.githubusercontent.com/78338890/121990062-291ea100-cd6b-11eb-8a5c-22a1d6395fa0.png">

### *MODEL 2- Forecasting stock prices using ARIMA*

<img width="1010" alt="Screen Shot 2021-06-14 at 23 55 32" src="https://user-images.githubusercontent.com/78338890/121990707-3720f180-cd6c-11eb-9635-78143c6c1a3f.png">
<img width="1004" alt="Screen Shot 2021-06-14 at 23 55 43" src="https://user-images.githubusercontent.com/78338890/121990722-3e47ff80-cd6c-11eb-87c3-dbe7088d3d90.png">
<img width="1022" alt="Screen Shot 2021-06-14 at 23 55 58" src="https://user-images.githubusercontent.com/78338890/121990732-43a54a00-cd6c-11eb-857d-4632022482a8.png">
<img width="1019" alt="Screen Shot 2021-06-14 at 23 56 19" src="https://user-images.githubusercontent.com/78338890/121990749-4a33c180-cd6c-11eb-93fc-9c6e4d5d3d53.png">
<img width="1015" alt="Screen Shot 2021-06-14 at 23 56 32" src="https://user-images.githubusercontent.com/78338890/121990757-515acf80-cd6c-11eb-9850-c5c300cd7e3e.png">
<img width="362" alt="Screen Shot 2021-06-14 at 23 59 05" src="https://user-images.githubusercontent.com/78338890/121990880-8bc46c80-cd6c-11eb-8b49-2057c9457208.png">

- Creating dataframes of predicted close prices (for next 7 days), defining start date as tomorrow and a dateframe with just the Dates (of next 7 days).
- Concatenate the two dataframes into one and rename respective columns to Date and Predicted price.

<img width="385" alt="Screen Shot 2021-06-15 at 00 06 09" src="https://user-images.githubusercontent.com/78338890/121991373-8d426480-cd6d-11eb-83da-c8f18f6061f3.png">

<img width="1033" alt="Screen Shot 2021-06-15 at 00 05 00" src="https://user-images.githubusercontent.com/78338890/121991292-5ec48980-cd6d-11eb-86e0-a9ae155b2f26.png">


### *MODEL 1- Forecasting stock prices using Prophet*

- Create a new dataframe for this model by selecting only the Close price from our original df.
<img width="231" alt="Screen Shot 2021-06-16 at 23 03 26" src="https://user-images.githubusercontent.com/78338890/122324622-1afd8b80-cef7-11eb-8f34-d145dc284446.png">

- Reset Index and use the 'rename' function to change the name of the columns to "Date" and "Close".
- Fit the new dataframe in Prophet model and set the forecast period (in our case, 14 days).
- Display the dataframe with predicted prices where "yhat" is Close price, "yhat_lower" is lowest price for the day and "yhat_upper" is the highest price for the day.
<img width="402" alt="Screen Shot 2021-06-16 at 23 08 48" src="https://user-images.githubusercontent.com/78338890/122325024-d7efe800-cef7-11eb-92dd-0ee7cce81ef5.png">

- Plot predicted prices.
<img width="671" alt="Screen Shot 2021-06-16 at 23 10 43" src="https://user-images.githubusercontent.com/78338890/122325211-27ceaf00-cef8-11eb-80ee-aa0d6cb3c7a9.png">
<img width="615" alt="Screen Shot 2021-06-16 at 23 11 00" src="https://user-images.githubusercontent.com/78338890/122325220-2d2bf980-cef8-11eb-98c7-92d89a37d1b7.png">

## *Comparing price predictions of each of the models with actual stock(AAPL) Close price*

- Create a dataframe with only Close price prediction from Prophet model.
- Create a 2nd dataframe with Close price prediction from LSTM model.
- Create a 3rd dataframe with Close price prediction from ARIMA model.
- Concatenate all the three dataframes into one and rename columns.
<img width="378" alt="Screen Shot 2021-06-16 at 23 16 25" src="https://user-images.githubusercontent.com/78338890/122325709-1043f600-cef9-11eb-8424-6747baf4ce5c.png">

- Display actual AAPL stock price and compare to see which model predicted the most accurate price.
<img width="235" alt="Screen Shot 2021-06-16 at 23 16 55" src="https://user-images.githubusercontent.com/78338890/122325682-07ebbb00-cef9-11eb-9f39-706a13c8632b.png">

## *RESULTS FROM THE PREDICTIONS*

After running the above models, the predictions from ARIMA were pretty close to the actual readings so we picked ARIMA as the most accurate out of the three.

### *Model 4: Predict Stock Prices Change using Random Forest*

- First, plot 1-day percentage change of adjusted close price in a histogram.
<img width="1012" alt="Screen Shot 2021-06-16 at 23 21 26" src="https://user-images.githubusercontent.com/78338890/122326019-9ceeb400-cef9-11eb-8934-0123eb3ac7e6.png">

- Create an empty list to hold the feature names.
- In a for loop, use the ta-lib library SMA and RSI methods to calculate the SMA-14, SMA-30, SMA-50, & SMA-200 and also RSI-14, RSI-30, RSI-50, & RSI-200.
- Append the moving average and rsi variable names to the feature_names list.
- use the dataframe pct_change method again to calculate the daily volume change percentage and add the volume feature name to the list
-  shift price values forward to the next 7 indexes.
-  7-days future close price change percentage.
-  Drop nulls.
-  Assign feature_names list to variable X and 7-day future close price percentage column to variable y.
-  Set training size to 85% of the entire dataset and assign the first 85% of the feature values and target values to X_train and y_train, respectively.
-  Assign the last 15% of the feature values and target values to X_test and y_test, respectively.
-  Set a dictionary of parameters for our random forest model. 
<img width="521" alt="Screen Shot 2021-06-16 at 23 30 55" src="https://user-images.githubusercontent.com/78338890/122326844-eee40980-cefa-11eb-8412-ba79f3f4e049.png">

- Create an empty list to hold the values test_score for different parameter sets.
- Create a scikit-learn RandomForestRegressor object.
- Use a for-loop to iterate through the parameter value in the grid dictionary, apply the parameter set to the random forest model using the set_params function and fit the model with the training set, X_train & y_train.
- Use the NumPy argmax function to get the index of the highest test score from the list and print the best test score and parameter set.
- Fit X_train and y_train in the Random Forest model. Predict "y" and plot the preciction.
<img width="1029" alt="Screen Shot 2021-06-16 at 23 35 04" src="https://user-images.githubusercontent.com/78338890/122327384-c577ad80-cefb-11eb-9d93-7c3e37e27348.png">

  ##### *Now evaluating our RF model*

- Use scikit-learn metrics module to calculate the MAE, MSE, and RMSE and then print them out.
<img width="516" alt="Screen Shot 2021-06-16 at 23 38 58" src="https://user-images.githubusercontent.com/78338890/122327557-0e2f6680-cefc-11eb-9d5f-930cd0de56f8.png">

- Now combine historical close price with ARIMA model's predicted close price and plot it. We used ARIMA predictions because ARIMA model gave us the most accurate/closest price to the actual close price.
<img width="1012" alt="Screen Shot 2021-06-16 at 23 43 51" src="https://user-images.githubusercontent.com/78338890/122327948-bcd3a700-cefc-11eb-8f11-4ee80597b8ed.png">

### *Bollinger bands trading srategy and signals*

- Bollinger Bands are a type of price envelope developed by John BollingerOpens in a new window. (Price envelopes define upper and lower price range levels.) Bollinger Bands are envelopes plotted at a standard deviation level above and below a simple moving average of the price. Because the distance of the bands is based on standard deviation, they adjust to volatility swings in the underlying price. Bollinger Bands use 2 parameters, Period and Standard Deviations, StdDev. The default values are 20 for period, and 2 for standard deviations, although you may customize the combinations. Bollinger bands help determine whether prices are high or low on a relative basis. They are used in pairs, both upper and lower bands and in conjunction with a moving average. Further, the pair of bands is not intended to be used on its own. Use the pair to confirm signals given with other indicators.

- For this, we used the concatenated dataframe with the historical and 7 days of precicted prices.
<img width="224" alt="Screen Shot 2021-06-16 at 23 45 56" src="https://user-images.githubusercontent.com/78338890/122328151-205dd480-cefd-11eb-8266-a5929fd27dfc.png">

- Calculate, rolling mean and rolling standard deviation with window of 20 days as well as calculate rolling upper and rolling lower and plot the Bollinger bands.
<img width="1050" alt="Screen Shot 2021-06-16 at 23 49 08" src="https://user-images.githubusercontent.com/78338890/122328347-7cc0f400-cefd-11eb-8174-ec08e2cd1aae.png">

- Define data, data = df.Close
- Creating the Trading Strategy and define signals.
<img width="581" alt="Screen Shot 2021-06-16 at 23 51 02" src="https://user-images.githubusercontent.com/78338890/122328484-beea3580-cefd-11eb-8203-70eabc65a418.png">

- Plot the Bollinger bands signals
![Screen Shot 2021-06-17 at 12 03 03 PM](https://user-images.githubusercontent.com/78338890/122499168-6c248280-cfbe-11eb-934d-fa04d83a40f3.png)

### *Moving Average Crossover trading signal*

Moving Average (MA) Crossover indicator signals a crossover of a slower moving average or a longer period moving average by a faster moving average or a shorter period moving average. The MA crossover shows when the longer period moving average line cross a shorter period moving average line.

- Set the long and short windows, generate short and long MAs, generate trading signals and calculate the points in time at which a position should be taken.
<img width="585" alt="Screen Shot 2021-06-16 at 23 54 24" src="https://user-images.githubusercontent.com/78338890/122328829-4d5eb700-cefe-11eb-8a2b-5714765e8a2f.png">

- Plot everything
<img width="541" alt="Screen Shot 2021-06-16 at 23 54 39" src="https://user-images.githubusercontent.com/78338890/122328840-52bc0180-cefe-11eb-955f-fcd02a049c82.png">
<img width="1057" alt="Screen Shot 2021-06-16 at 23 54 53" src="https://user-images.githubusercontent.com/78338890/122328849-58b1e280-cefe-11eb-94bd-881daebeb636.png">



### *SOURCES*

- https://tcoil.info/compute-rsi-for-stocks-with-python-relative-strength-index/
- https://tcoil.info/compute-macd-indicator-for-stocks-with-python/
- https://tcoil.info/predict-stock-price-trend-with-machine-learning-random-forest-scikit-python/ 
- https://github.com/vb100/multivariate-lstm/blob/master/LSTM_model_stocks.ipynb
- https://www.tradingview.com/support/solutions/43000501974-chaikin-money-flow-cmf/
- https://www.fidelity.com/learning-center/trading-investing/technical-analysis/technical-indicator-guide/bollinger-bands
- https://patternswizard.com/moving-average-crossover/

### *CONTRIBUTORS*
1. Yu Wang
2. Dipendra Shastri
3. Jack Que
4. Christopher Kulathoor
5. Simran Saini

