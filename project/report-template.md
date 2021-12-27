# Report: Predict Bike Sharing Demand with AutoGluon Solution
### William Hyun

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
The `datetime` column was not accepted in **Regression** training, therefore I had to separate it into three numeric columns of year, month, and day.

### What was the top ranked model that performed?
`WeightedEnsemble_L3` performed the best with a fit score of `-36.970716`. 

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
Since I already did EDA including splitting the datetime, I found that the train data had significantly more sales in months 1 and 12, so I re-divided the months into seasons (e.g. months 11, 12, and 1 being a group) and called it `season2`. I replaced `weather` and `season2` columns with one-hot encoding columns because they were categorical data semantically. 

### How much better did your model preform after adding additional features and why do you think that is?
My model performed worse after adding additional features with the score of `-36.711429`. 
Also, the Kaggle score (root square mean logarithmic error) increased to `0.51492`from `0.51112`, which means that it performed worse. 
I believe that adding `season2` and using one-hot encoding caused the overfit to the training data set and thus increased the error in Kaggle data. 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
I tried three hyper parameters: `time`, `eval_metric`, and `presets`.
All three parameters showed improvements over the `initial` and `add_features` models. 
The best performing was `eval_metric` with a Kaggle score of `0.44682`. 

### If you were given more time with this dataset, where do you think you would spend more time?
I would try different hyper parameters to model the data better since all of the tuned hyper parameters I tried showed improvements.  

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|time_limit|eval_metric|presets|score|
|--|--|--|--|--|
|initial|120|RMSE|best_quality|0.51112|
|initial_with_240|240|RMSE|best_quality|0.47642|
|add_features|120|RMSE|best_quality|0.51492|
|MAE|120|MAE|best_quality|0.44682|
|MQFT|120|RMSE|MQFT|0.49753|

* RMSE: root_mean_squared_error
* MAE: mean_absolute_error
* MQFT: medium_quality_faster_train

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](img/model_test_score.png)

## Summary
I have tried five different models, `initial`, `initial_with_240`, `add_features`, `MAE`, and `MQFT`.
Through my attempts, I have found that hyperparmeter tuning resulted in better performance.
The best performing model was `MAE` (`mean_absolute_error`). 
If I have more budget, I wish to explore more hyperparameter space. 