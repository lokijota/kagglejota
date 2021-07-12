# Tabular Playground Series - Jul 2021

From: <https://www.kaggle.com/c/tabular-playground-series-jul-2021/data>

In this competition you are predicting the values of air pollution measurements over time, based on basic weather information (temperature and humidity) and the input values of 5 sensors.

The three target values to you to predict are: target_carbon_monoxide, target_benzene, and target_nitrogen_oxides.

Submissions are evaluated using the mean column-wise root mean squared logarithmic error. The RMSLE for a single column calculated as indicated in <https://www.kaggle.com/c/tabular-playground-series-jul-2021/overview/evaluation>. The final score is the mean of the RMSLE over all columns.

The submission must must predict a probability for the TARGET variable (each of the three pollutants).

## To-do

- Understand why CT MinMax Scaler and make_pipeline with MinMaxScaler end up with different results
    - They output the same result: 0.1911234053816591. SO there's nothing wrong with the minmaxscaler in the col transformer or directly in pipeline
    - Adding the date expansion, we get: 0.1778039335316294

## Done

### 12-07-2021

- Save better Hyperparams from Randomized Search, and apply to regressor

search_cm = RandomizedSearchCV(pipeline_cm, param_distributions=param_dist, cv=5, n_iter=50)
{'lgbmregressor__n_estimators': 150, 'lgbmregressor__max_depth': 20, 'lgbmregressor__learning_rate': 0.05}

search_benz = RandomizedSearchCV(pipeline_benz, param_distributions=param_dist, cv=5, n_iter=50)
{'lgbmregressor__n_estimators': 200, 'lgbmregressor__max_depth': 20, 'lgbmregressor__learning_rate': 0.05}

search_no = RandomizedSearchCV(pipeline_no, param_distributions=param_dist, cv=5, n_iter=50)
{'lgbmregressor__n_estimators': 150, 'lgbmregressor__max_depth': 15, 'lgbmregressor__learning_rate': 0.05}